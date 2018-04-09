# babel-plugin-transform-decorators

> 将类和对象装饰器编译为 ES5。

## 示例

（例子出自提案）

### 简单的类（class）装饰器

```js
@annotation
class MyClass { }

function annotation(target) {
   target.annotated = true;
}
```

### 类（Class）装饰器

```js
@isTestable(true)
class MyClass { }

function isTestable(value) {
   return function decorator(target) {
      target.isTestable = value;
   }
}
```

### 类（Class）函数装饰器

```js
class C {
  @enumerable(false)
  method() { }
}

function enumerable(value) {
  return function (target, key, descriptor) {
     descriptor.enumerable = value;
     return descriptor;
  }
}
```

## 安装

```sh
npm install --save-dev babel-plugin-transform-decorators
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

```json
{
  "plugins": ["transform-decorators"]
}
```

### 通过 CLI

```sh
babel --plugins transform-decorators script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-decorators"]
});
```

## 参考

* [提案：Javascript 装饰器](https://github.com/wycats/javascript-decorators/blob/master/README.md)
