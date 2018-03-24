# babel-plugin-transform-es2015-typeof-symbol

> ES6 引入了一种称为 [symbols](https://babeljs.cn/learn-es2015/#ecmascript-2015-features-symbols) 新的原生类型。该转译器用类似原生行为的方法包装了所有 `typeof` 表达式（即，为 symbols 返回 "symbol"）。

## 示例

**输入**

```javascript
typeof Symbol() === "symbol";
```

**输出**

```javascript
var _typeof = function (obj) {
  return obj && obj.constructor === Symbol ? "symbol" : typeof obj;
};

_typeof(Symbol()) === "symbol";
```

## 安装

```sh
npm install --save-dev babel-plugin-transform-es2015-typeof-symbol
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

```json
{
  "plugins": ["transform-es2015-typeof-symbol"]
}
```

### 通过 CLI

```sh
babel --plugins transform-es2015-typeof-symbol script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-es2015-typeof-symbol"]
});
```
