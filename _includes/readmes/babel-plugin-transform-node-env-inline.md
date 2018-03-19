# babel-plugin-transform-node-env-inline

内联 `NODE_ENV` 环境变量，如果它是二元表达式的一部分（例如： `process.env.NODE_ENV === "development"`），则静态评估并替换它。

## 示例

**输入**

```javascript
process.env.NODE_ENV === "development";
process.env.NODE_ENV === "production";
```

**输出**

```sh
NODE_ENV=development babel in.js --plugins transform-node-env-inline
```

```javascript
true;
false;
```

## 安装

```sh
npm install babel-plugin-transform-node-env-inline
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

```json
{
  "plugins": ["transform-node-env-inline"]
}
```

### 通过 CLI

```sh
babel --plugins transform-node-env-inline script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-node-env-inline"]
});
```
