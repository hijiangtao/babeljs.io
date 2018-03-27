# babel-plugin-transform-es2015-instanceof

## 安装

```sh
npm install --save-dev babel-plugin-transform-es2015-instanceof
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

```json
{
  "plugins": ["transform-es2015-instanceof"]
}
```

### 通过 CLI

```sh
babel --plugins transform-es2015-instanceof script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-es2015-instanceof"]
});
```
