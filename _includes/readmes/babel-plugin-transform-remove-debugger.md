# babel-plugin-transform-remove-debugger

该插件会删除所有 `debugger;` 语句。

## 示例

**输入**

```javascript
debugger;
```

**输出**

```javascript
```

## 安装

```sh
npm install babel-plugin-transform-remove-debugger
```

## 使用

### 通过 `.babelrc`（Recommended）

**.babelrc**

```json
{
  "plugins": ["transform-remove-debugger"]
}
```

### 通过 CLI

```sh
babel --plugins transform-remove-debugger script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-remove-debugger"]
});
```
