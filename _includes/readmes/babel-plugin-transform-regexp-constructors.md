# babel-plugin-transform-regexp-constructors

如果 RegExp 参数是字符串，这会将 RegExp 构造函数更改为字符串。

## 示例

**输入**

```javascript
const foo = 'ab+';
var a = new RegExp(foo+'c', 'i');
```

**输出**

```javascript
const foo = 'ab+';
var a = /ab+c/i;
```

## 安装

```sh
npm install babel-plugin-transform-regexp-constructors
```

## 用法

### 通过 `.babelrc`（Recommended）

**.babelrc**

```json
{
  "plugins": ["transform-regexp-constructors"]
}
```

### 通过 CLI

```sh
babel --plugins transform-regexp-constructors script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-regexp-constructors"]
});
```
