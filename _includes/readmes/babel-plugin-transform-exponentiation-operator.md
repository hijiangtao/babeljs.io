# babel-plugin-transform-exponentiation-operator

> 指数运算符编译为 ES5

## 示例

```js
// x ** y

let squared = 2 ** 2;
// 等同于：2 * 2

let cubed = 2 ** 3;
// 等同于：2 * 2 * 2


// x **= y

let a = 2;
a **= 2;
// 等同于：a = a * a;

let b = 3;
b **= 3;
// 等同于：b = b * b * b;
```

## 安装

```sh
npm install --save-dev babel-plugin-transform-exponentiation-operator
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

```json
{
  "plugins": ["transform-exponentiation-operator"]
}
```

### 通过 CLI

```sh
babel --plugins transform-exponentiation-operator script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-exponentiation-operator"]
});
```

## 参考

* [提案: 指数运算符（Exponentiation Operator）](https://github.com/rwaldron/exponentiation-operator)
* [Spec: 指数运算符（Exponential Operator）](https://rwaldron.github.io/exponentiation-operator/)
