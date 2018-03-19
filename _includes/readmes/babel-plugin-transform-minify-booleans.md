# babel-plugin-transform-minify-booleans

该插件允许 Babel 将 boolean 字面量进行转换 `!0` 代表 `true`，`!1` 代表 `false`。

## 示例

**输入**

```javascript
true;
false;
```

**输出**

```javascript
!0;
!1;
```

## 安装

```sh
npm install babel-plugin-transform-minify-booleans
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

```json
{
  "plugins": ["transform-minify-booleans"]
}
```

### 通过 CLI

```sh
babel --plugins transform-minify-booleans script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-minify-booleans"]
});
```
