# babel-plugin-transform-property-literals

该插件允许 Babel 将有效的标识符属性 key 的字面量转换为标识符。

## 示例

**输入**

```javascript
var foo = {
  // changed
  "bar": function () {},
  "1": function () {},
  
  // not changed
  "default": 1,
  [a]: 2,
  foo: 1
};
```

**输出**

```javascript
var foo = {
  bar: function () {},
  1: function () {},

  "default": 1,
  [a]: 2,
  foo: 1
};
```

## 安装

```sh
npm install babel-plugin-transform-property-literals
```

## 用法

### 通过 `.babelrc`（Recommended）

**.babelrc**

```json
{
  "plugins": ["transform-property-literals"]
}
```

### 通过 CLI

```sh
babel --plugins transform-property-literals script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-property-literals"]
});
```
