# babel-plugin-transform-es2015-function-name

> 将 ES2015 的 function.name 语义应用于所有函数。

## 安装

```sh
npm install --save-dev babel-plugin-transform-es2015-function-name
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

```json
{
  "plugins": ["transform-es2015-function-name"]
}
```

### 通过 CLI

```sh
babel --plugins transform-es2015-function-name script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-es2015-function-name"]
});
```
