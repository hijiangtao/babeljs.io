# babel-plugin-transform-es2015-modules-commonjs

> 该插件将 ES2015 转译为 [CommonJS](http://wiki.commonjs.org/wiki/Modules/1.1)。

## 示例

**输入**

```javascript
export default 42;
```

**输出**

```javascript
Object.defineProperty(exports, "__esModule", {
  value: true
});

exports.default = 42;
```

## 安装

```sh
npm install --save-dev babel-plugin-transform-es2015-modules-commonjs
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

```js
// 未包含选项
{
  "plugins": ["transform-es2015-modules-commonjs"]
}

// 包含选项
{
  "plugins": [
    ["transform-es2015-modules-commonjs", {
      "allowTopLevelThis": true
    }]
  ]
}
```

### 通过 CLI

```sh
babel --plugins transform-es2015-modules-commonjs script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-es2015-modules-commonjs"]
});
```

## 选项

### `loose`

`boolean`，默认为 `false`。

就规范而言，`import` 和 `export` 只允许在顶层使用。在松散模式（loose）下，这些允许在任何地方使用。

默认情况下，当使用 babel 导出时，会导出不可枚举 `__esModule` 属性。

```javascript
var foo = exports.foo = 5;

Object.defineProperty(exports, "__esModule", {
  value: true
});
```

在不支持此功能的环境中，你可以使用 `babel-plugin-transform-es2015-modules-commonjs` 上启用松散模式下，将使用赋值的方式代替使用 `Object.defineProperty`。

```javascript
var foo = exports.foo = 5;
exports.__esModule = true;
```

### `strict`

`boolean`，默认为 `false`。

默认情况下，当使用 babel 导出时，会导出不可枚举的 `__esModule` 属性。在某些情况下，此属性用于确定导入的_是_默认导出，或者_包含_默认导出。

```javascript
var foo = exports.foo = 5;

Object.defineProperty(exports, "__esModule", {
  value: true
});
```

为了防止 `__esModule` 属性被导出，你可以将 `strict` 选项设置为 `true`。

### `noInterop`

`boolean`，默认为 `false`

默认情况下，当使用 babel 导出时，会导出不可枚举的 `__esModule` 属性。然后使用该属性确定导入的_是_默认导出，或者_包含_默认导出。

```javascript
"use strict";

var _foo = require("foo");

var _foo2 = _interopRequireDefault(_foo);

function _interopRequireDefault(obj) {
  return obj && obj.__esModule ? obj : { default: obj };
}
```

在不需要自动解包 `default` 的情况下，可以将 `noInterop` 选项设置为 `true` 以避免使用 `interopRequireDefault` helper（以内联形式显示）。
