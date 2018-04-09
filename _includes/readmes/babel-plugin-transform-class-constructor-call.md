# babel-plugin-transform-class-constructor-call (deprecated)

> 提案撤回：可以用装饰器解决。

该插件允许 Babel 转译类构造函数。

它基本上允许使用 ES2015 类的 [new.target](http://mdn.io/new.target) 功能：

```js
class Point {

  constructor(x, y) {
    this.x = x;
    this.y = y;
  }

  call constructor(x, y) {
    return new Point(x, y);
  }

}

let p1 = new Point(1, 2); // OK
let p2 = Point(3, 4); // OK
```

## 示例

### Date 示例
javascript [Date](http://mdn.io/date) 以这种方式工作：

```js
// 你可以使用 new 关键字获取 Date 实例
let now = new Date();
console.log(now.getMonth()); // 打印 '3'
console.log(now.toString()); // 打印 'Mon Apr 11 2016 13:26:07 GMT+0100 (BST)'

// 你可以使用 Date 作为函数获取当前日期的字符串：
let nowStr = Date();
console.log(nowStr); // 打印 'Mon Apr 11 2016 13:26:07 GMT+0100 (BST)'
```

目前可以使用 [new.target](http://mdn.io/new.target) 实现类似功能（参阅[提案中的示例](https://github.com/tc39/ecma262/blob/master/workingdocs/callconstructor.md#motivating-example)），并且此新功能使其可用于 ES2015 类。

日期的实现如下：

```js
class Date {
  constructor() {
    // ...
  }

  call constructor() {
    let date = new Date();
    return date.toString();
  }
}

let now = new Date(); // 获取日期实例
let nowStr = Date(); // 使用 'call constructor()' 部分来获取当前日期的字符串
```

## 安装

```sh
npm install --save-dev babel-plugin-transform-class-constructor-call
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

```json
{
  "plugins": ["transform-class-constructor-call"]
}
```

### 通过 CLI

```sh
babel --plugins transform-class-constructor-call script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-class-constructor-call"]
});
```

## 参考

* [无效的提案](https://github.com/tc39/proposals/blob/master/inactive-proposals.md)
* [提案：调用构造函数](https://github.com/tc39/ecma262/blob/master/workingdocs/callconstructor.md)
* [博客文章：ECMAScript 提案：函数可调用（function-callable）类](http://www.2ality.com/2015/10/call-constructor-esprop.html)
