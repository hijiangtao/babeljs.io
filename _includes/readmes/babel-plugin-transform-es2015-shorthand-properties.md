# babel-plugin-transform-es2015-shorthand-properties

> 将 ES2015 属性简写（shorthand properties）编译为 ES5

## 示例

**输入**

```js
var o = { a, b, c };
```

**输出**

```js
var o = { a: a, b: b, c: c };
```

**输入**

```js
var cat = {
  getName() {
    return name;
  }
};
```

**输出**

```js
var cat = {
  getName: function () {
    return name;
  }
};
```

## 安装

```sh
npm install --save-dev babel-plugin-transform-es2015-shorthand-properties
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

```json
{
  "plugins": ["transform-es2015-shorthand-properties"]
}
```

### 通过 CLI

```sh
babel --plugins transform-es2015-shorthand-properties script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-es2015-shorthand-properties"]
});
```
