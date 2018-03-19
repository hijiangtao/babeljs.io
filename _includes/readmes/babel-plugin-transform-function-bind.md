# babel-plugin-transform-function-bind

> 编译新的函数绑定运算符 `::` 到 ES5。

## 详情

```js
obj::func
// 相当于：
func.bind(obj)

::obj.func
// 相当于：
obj.func.bind(obj)

obj::func(val)
// 相当于：
func.call(obj, val)

::obj.func(val)
// 相当于：
obj.func.call(obj, val)
```


## 示例

### 基本代码

```js
const box = {
  weight: 2,
  getWeight() { return this.weight; },
};

const { getWeight } = box;

console.log(box.getWeight()); // 输出 '2'

const bigBox = { weight: 10 };
console.log(bigBox::getWeight()); // 输出 '10'

// 通过绑定:
function add(val) { return this + val; }

console.log(bigBox::getWeight()::add(5)); // 输出 '15'
```


### 与 `document.querySelectorAll` 一起使用

与 `document.querySelectorAll` 一起使用时可以非常方便：

```js
const { map, filter } = Array.prototype;

let sslUrls = document.querySelectorAll('a')
                ::map(node => node.href)
                ::filter(href => href.substring(0, 5) === 'https');

console.log(sslUrls);
```


`document.querySelectorAll` 返回的不是普通的 `NodeList` 元素数组，所以通常你不能使用 `map` 函数，并且必须以这种方式使用它：`Array.prototype.map.call(document.querySelectorAll(...), node => { ... })`。上述使用 `::` 的代码将起作用，因为它相当于：

```js
const { map, filter } = Array.prototype;

let sslUrls = document.querySelectorAll('a');
sslUrls = map.call(sslUrls, node => node.href);
sslUrls = filter.call(sslUrls, href => href.substring(0, 5) === 'https');

console.log(sslUrls);
```

### 自动绑定 self
当在 `::` 运算符之前没有指定任何内容时，该函数被绑定到它的对象：

```js
$('.some-link').on('click', ::view.reset);
// 相当于：
$('.some-link').on('click', view.reset.bind(view));
```

## 安装

```sh
npm install --save-dev babel-plugin-transform-function-bind
```

## 使用

### 通过 `.babelrc`（推荐）

**.babelrc**

```json
{
  "plugins": ["transform-function-bind"]
}
```

### 通过 CLI

```sh
babel --plugins transform-function-bind script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-function-bind"]
});
```

## 参考

* [提案](https://github.com/zenparsing/es-function-bind)
* [Babel 博客：函数绑定语法（Function Bind Syntax）](/blog/2015/05/14/function-bind)
