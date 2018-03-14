# babel-plugin-transform-remove-undefined

对于变量赋值来说，这将删除评估为 `undefined ` 的 rval（仅对函数中的 `var` 有效）。
对于函数来说，这将删除评估为 `undefined` 的返回值。

## 示例

**输入**

```javascript
let a = void 0;
function foo() {
  var b = undefined;
  return undefined;
}
```

**输出**

```javascript
let a;
function foo() {
  var b;
  return;
}
```

## 安装

```sh
npm install babel-plugin-transform-remove-undefined
```

## 使用

### 通过 `.babelrc`（推荐）

**.babelrc**

```json
{
  "plugins": ["babel-plugin-transform-remove-undefined"]
}
```

### 通过 CLI

```sh
babel --plugins babel-plugin-transform-remove-undefined script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["babel-plugin-transform-remove-undefined"]
});
```

## 选项

+ `tdz` - 在声明/初始化之前，检测 let/const(throws) 和 var(void 0) 的用法。
