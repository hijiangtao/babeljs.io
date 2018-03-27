# babel-plugin-transform-es2015-destructuring

> 将 ES2015 的解构编译为 ES5。

## 安装

```sh
npm install --save-dev babel-plugin-transform-es2015-destructuring
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

```json
{
  "plugins": ["transform-es2015-destructuring"]
}
```

### 通过 CLI

```sh
babel --plugins transform-es2015-destructuring script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-es2015-destructuring"]
});
```
