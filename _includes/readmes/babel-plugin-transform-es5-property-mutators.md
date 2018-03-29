# babel-plugin-transform-es5-property-mutators

> 该插件允许 Babel 将[对象初始化器](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/Object_initializer#Method_definitions)转译为 `Object.defineProperties`。

## 示例

**输入**

```javascript
var foo = {
  get bar() {
    return "bar";
  }
};
```

**输出**

```javascript
var foo = Object.defineProperties({}, {
  bar: {
    get: function () {
      return "bar";
    },
    enumerable: true,
    configurable: true
  }
});
```

## 安装

```sh
npm install --save-dev babel-plugin-transform-es5-property-mutators
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

```json
{
  "plugins": ["transform-es5-property-mutators"]
}
```

### 通过 CLI

```sh
babel --plugins transform-es5-property-mutators script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-es5-property-mutators"]
});
```
