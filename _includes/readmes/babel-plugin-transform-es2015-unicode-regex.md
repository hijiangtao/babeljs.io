# babel-plugin-transform-es2015-unicode-regex

> 将 ES2015 的 unicode 正则表达式编译为 ES5

## 示例

**输入**

```js
var string = "foo💩bar";
var match = string.match(/foo(.)bar/u);
```

**输出**

```js
var string = "foo💩bar";
var match = string.match(/foo((?:[\0-\t\x0B\f\x0E-\u2027\u202A-\uD7FF\uE000-\uFFFF]|[\uD800-\uDBFF][\uDC00-\uDFFF]|[\uD800-\uDBFF](?![\uDC00-\uDFFF])|(?:[^\uD800-\uDBFF]|^)[\uDC00-\uDFFF]))bar/);
```

## 安装

```sh
npm install --save-dev babel-plugin-transform-es2015-unicode-regex
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

```json
{
  "plugins": ["transform-es2015-unicode-regex"]
}
```

### 通过 CLI

```sh
babel --plugins transform-es2015-unicode-regex script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-es2015-unicode-regex"]
});
```
