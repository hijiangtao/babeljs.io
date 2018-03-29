# babel-plugin-transform-es3-property-literals

> 确保保留字在对象属性中的引用

## 示例

**输入**

```javascript
var foo = {
  catch: function () {}
};
```

**输出**

```javascript
var foo = {
  "catch": function () {}
};
```

## 安装

```sh
npm install --save-dev babel-plugin-transform-es3-property-literals
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

```json
{
  "plugins": ["transform-es3-property-literals"]
}
```

### 通过 CLI

```sh
babel --plugins transform-es3-property-literals script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-es3-property-literals"]
});
```
