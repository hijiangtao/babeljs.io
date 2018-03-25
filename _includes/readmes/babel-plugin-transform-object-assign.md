# babel-plugin-transform-object-assign

> 用内联的 helper 替换 `Object.assign`。如果你正在编写应用程序而不是库，建议你改为使用 `Object.assign` polyfill 代替。

## 实例

**输入**

```javascript
Object.assign(a, b);
```

**输出**

```javascript
var _extends = ...;

_extends(a, b);
```

## 注意事项

- 只能使用 `Object.assign` 或 Object['assign'] 形式的代码。不支持以下方式：

  ```javascript
  var { assign } = Object;
  var assign = Object.assign;
  ```

## 安装

```sh
npm install --save-dev babel-plugin-transform-object-assign
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

```json
{
  "plugins": ["transform-object-assign"]
}
```

### 通过 CLI

```sh
babel --plugins transform-object-assign script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-object-assign"]
});
```
