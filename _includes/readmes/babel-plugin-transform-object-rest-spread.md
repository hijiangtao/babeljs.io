# babel-plugin-transform-object-rest-spread

> 该插件允许 Babel 转译对象析构赋值的 rest 属性和对象字面量的 spread 属性。

## 示例

### Rest 属性

```js
let { x, y, ...z } = { x: 1, y: 2, a: 3, b: 4 };
console.log(x); // 1
console.log(y); // 2
console.log(z); // { a: 3, b: 4 }
```

### Spread 属性

```js
let n = { x, y, ...z };
console.log(n); // { x: 1, y: 2, a: 3, b: 4 }
```

## 安装

```sh
npm install --save-dev babel-plugin-transform-object-rest-spread
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

```json
{
  "plugins": ["transform-object-rest-spread"]
}
```

### 通过 CLI

```sh
babel --plugins transform-object-rest-spread script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-object-rest-spread"]
});
```

## 选项

### `useBuiltIns`

`boolean`，默认为 `false`。

默认情况下，此插件使用 `extends` helper 来填充 `Object.assign`。启用此选项将直接使用 `Object.assign`。

**.babelrc**

```json
{
  "plugins": [
    ["transform-object-rest-spread", { "useBuiltIns": true }]
  ]
}
```

**输入**

```js
z = { x, ...y };
```

**输出**

```js
z = Object.assign({ x }, y);
```

## 参考

* [提案：ECMAScript 对象中的 Rest/Spread 属性](https://github.com/sebmarkbage/ecmascript-rest-spread)
* [Spec](http://sebmarkbage.github.io/ecmascript-rest-spread)
