# babel-plugin-transform-es2015-literals

> 将 ES2015 的 unicode 字符串和数字字面量编译为 ES5。

## 示例

**输入**

```js
var b = 0b11; // 二进制整型字面量
var o = 0o7; // 八进制整型字面量
const u = 'Hello\u{000A}\u{0009}!'; // unicode 字符串字面量，换行符和制表符
```

**输出**

```js
var b = 3; // 二进制整型字面量
var o = 7; // 八进制整型字面量
const u = 'Hello\n\t!'; // unicode 字符串字面量，换行符和制表符
```

## 安装

```sh
npm install --save-dev babel-plugin-transform-es2015-literals
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

```json
{
  "plugins": ["transform-es2015-literals"]
}
```

### 通过 CLI

```sh
babel --plugins transform-es2015-literals script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-es2015-literals"]
});
```
