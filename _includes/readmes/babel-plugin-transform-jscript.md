# babel-plugin-transform-jscript

> 该插件允许 Babel 将命名函数表达式转换为函数声明，以解决与声明式函数表达式相关的一些[特别讨厌的 JScript 错误](https://kangax.github.io/nfe/#jscript-bugs)。

## 示例

**输入**

```javascript
var foo = function bar() {

};
```

**输出**

```javascript
"use strict";

var foo = (function () {
  function bar() {}

  return bar;
})();
```

## 安装

```sh
npm install --save-dev babel-plugin-transform-jscript
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

```json
{
  "plugins": ["transform-jscript"]
}
```

### 通过 CLI

```sh
babel --plugins transform-jscript script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-jscript"]
});
```
