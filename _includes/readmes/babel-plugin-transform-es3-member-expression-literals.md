# babel-plugin-transform-es3-member-expression-literals

> 确保保留字在属性访问中的引用。

## 示例

**输入**

```javascript
foo.catch;
```

**输出**

```javascript
foo["catch"];
```

## 安装

```sh
npm install --save-dev babel-plugin-transform-es3-member-expression-literals
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

```json
{
  "plugins": ["transform-es3-member-expression-literals"]
}
```

### 通过 CLI

```sh
babel --plugins transform-es3-member-expression-literals script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-es3-member-expression-literals"]
});
```
