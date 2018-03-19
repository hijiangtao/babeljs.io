# babel-plugin-transform-object-set-prototype-of-to-assign

> 该插件将所有的 `Object.setPrototypeOf` 调用转换为一个方法，该方法会设置所有属性的浅层默认值。

**注意：** 使用此插件时有一些注意事项，请参阅 [`babel-plugin-transform-proto-to-assign` README](https://github.com/babel/babel/tree/master/packages/babel-plugin-transform-proto-to-assign) 了解更多信息。

## 示例

**输入**

```javascript
Object.setPrototypeOf(bar, foo);
```

**输出**

```javascript
var _defaults = ...;

_defaults(bar, foo);
```

## 安装

```sh
npm install --save-dev babel-plugin-transform-object-set-prototype-of-to-assign
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

```json
{
  "plugins": ["transform-object-set-prototype-of-to-assign"]
}
```

### 通过 CLI

```sh
babel --plugins transform-object-set-prototype-of-to-assign script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-object-set-prototype-of-to-assign"]
});
```
