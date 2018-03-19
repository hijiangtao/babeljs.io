# babel-plugin-transform-inline-consecutive-adds

该插件内嵌连续的属性赋值，数组 push 等。

## 示例

**输入**

```javascript
const foo = {};
foo.a = 42;
foo.b = ["hi"];
foo.c = bar();
foo.d = "str";

...
const bar = [];
bar.push(1);
bar.push(2);
```

**输出**

```javascript
const foo = {
  a: 42,
  b: ["hi"],
  c: bar(),
  d: "str"
};

...
const bar = [1, 2];
```

## 安装

```sh
npm install babel-plugin-transform-inline-consecutive-adds
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

```json
{
  "plugins": ["transform-inline-consecutive-adds"]
}
```

### 通过 CLI

```sh
babel --plugins transform-inline-consecutive-adds script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-inline-consecutive-adds"]
});
```
