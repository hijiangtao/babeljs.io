# babel-plugin-transform-remove-console

该插件会移除所有 `console.*` 的调用。

## 示例

**输入**

```javascript
console.log("foo");
console.error("bar");
```

**输出**

```javascript
```

## 安装

```sh
npm install babel-plugin-transform-remove-console
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

```json
// 未包含选项
{
  "plugins": ["transform-remove-console"]
}
```

```json
// 包含选项
{
  "plugins": [ ["transform-remove-console", { "exclude": [ "error", "warn"] }] ]
}
```

### 通过 CLI

```sh
babel --plugins transform-remove-console script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-remove-console"]
});
```

## 选项

+ `exclude` - 排除不需要移除 console 方法的数组。
