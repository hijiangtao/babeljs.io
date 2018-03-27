# babel-plugin-transform-es2015-modules-amd

> 该插件将 ES2015 模块转译为 [Asynchronous Module Definition (AMD)](https://github.com/amdjs/amdjs-api)。

## 示例

**输入**

```javascript
export default 42;
```

**输出**

```javascript
define(["exports"], function (exports) {
  "use strict";

  Object.defineProperty(exports, "__esModule", {
    value: true
  });

  exports.default = 42;
});
```

## 安装

```sh
npm install --save-dev babel-plugin-transform-es2015-modules-amd
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

```json
{
  "plugins": ["transform-es2015-modules-amd"]
}
```

### 通过 CLI

```sh
babel --plugins transform-es2015-modules-amd script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-es2015-modules-amd"]
});
```

### 选项

请参阅 `babel-plugin-transform-es2015-commonjs` 的选项。
