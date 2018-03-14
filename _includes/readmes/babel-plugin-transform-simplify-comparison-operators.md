# babel-plugin-transform-simplify-comparison-operators

如果它们的类型推断为相同，则将 `===` 和 `!==` 转换为 `==` 和 `!=`。

## 示例

**输入**

```javascript
typeof foo === "object";
```

**输出**

```javascript
typeof foo == "object";
```

## 安装

```sh
npm install babel-plugin-transform-simplify-comparison-operators
```

## 使用

### 通过 `.babelrc`（推荐）

**.babelrc**

```json
{
  "plugins": ["transform-simplify-comparison-operators"]
}
```

### 通过 CLI

```sh
babel --plugins transform-simplify-comparison-operators script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-simplify-comparison-operators"]
});
```
