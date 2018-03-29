# babel-plugin-transform-es2015-block-scoped-functions

> Babel 插件确保块级的函数声明属于块级作用域内。

## 安装

```sh
npm install --save-dev babel-plugin-transform-es2015-block-scoped-functions
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

```json
{
  "plugins": ["transform-es2015-block-scoped-functions"]
}
```

### 通过 CLI

```sh
babel --plugins transform-es2015-block-scoped-functions script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-es2015-block-scoped-functions"]
});
```
