# babel-plugin-syntax-dynamic-import

解析 `import()`。

## 安装

```sh
npm install --save-dev babel-plugin-syntax-dynamic-import
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

```json
{
  "plugins": ["syntax-dynamic-import"]
}
```

### 通过 CLI

```sh
babel --plugins syntax-dynamic-import script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["syntax-dynamic-import"]
});
```
