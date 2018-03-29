# babel-plugin-transform-es2015-arrow-functions

> 将 ES2015 的箭头函数编译为 ES5。

## 示例

**输入**

```javascript
var a = () => {};
var a = (b) => b;

const double = [1,2,3].map((num) => num * 2);
console.log(double); // [2,4,6]

var bob = {
  _name: "Bob",
  _friends: ["Sally", "Tom"],
  printFriends() {
    this._friends.forEach(f =>
      console.log(this._name + " knows " + f));
  }
};
console.log(bob.printFriends());
```

**输出**

```javascript
var a = function () {};
var a = function (b) {
  return b;
};

const double = [1, 2, 3].map(function (num) {
  return num * 2;
});
console.log(double); // [2,4,6]

var bob = {
  _name: "Bob",
  _friends: ["Sally", "Tom"],
  printFriends() {
    var _this = this;

    this._friends.forEach(function (f) {
      return console.log(_this._name + " knows " + f);
    });
  }
};
console.log(bob.printFriends());
```

## 安装

```sh
npm install --save-dev babel-plugin-transform-es2015-arrow-functions
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

未包含选项：

```json
{
  "plugins": ["transform-es2015-arrow-functions"]
}
```

包含选项：

```json
{
  "plugins": [
    ["transform-es2015-arrow-functions", { "spec": true }]
  ]
}
```

### 通过 CLI

```sh
babel --plugins transform-es2015-arrow-functions script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-es2015-arrow-functions"]
});
```

## 选项

### `spec`

`boolean`，默认为 `false`。

该选项将生成的函数包装在 `.bind(this)` 中，并保持使用原函数的 `this`，而不是使用重命名的 `this`。它还添加了运行时检查以确保函数是否实例化。
