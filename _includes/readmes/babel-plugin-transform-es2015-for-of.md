# babel-plugin-transform-es2015-for-of

> 将 ES2015 的 for...of 编译为 ES5

## 示例

**输入**

```js
for (var i of foo) {}
```

**输出**

```js
var _iteratorNormalCompletion = true;
var _didIteratorError = false;
var _iteratorError = undefined;

try {
  for (var _iterator = foo[Symbol.iterator](), _step; !(_iteratorNormalCompletion = (_step = _iterator.next()).done); _iteratorNormalCompletion = true) {
    var i = _step.value;
  }
} catch (err) {
  _didIteratorError = true;
  _iteratorError = err;
} finally {
  try {
    if (!_iteratorNormalCompletion && _iterator.return) {
      _iterator.return();
    }
  } finally {
    if (_didIteratorError) {
      throw _iteratorError;
    }
  }
}
```

## 安装

```sh
npm install --save-dev babel-plugin-transform-es2015-for-of
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

未包含选项:

```js
{
  "plugins": ["transform-es2015-for-of"]
}
```

包含选项:

```json
{
  "plugins": [
    ["transform-es2015-for-of", {
      "loose": true
    }]
  ]
}
```

### 通过 CLI

```sh
babel --plugins transform-es2015-for-of script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-es2015-for-of"]
});
```

## 选项

### `loose`

`boolean`，默认为 `false`

在松散（loose）模式下，数组被放置在一个快速路径下，从而大大提高性能。
所有其他可迭代项将继续正常工作。

#### 示例

**输入**

```js
for (var i of foo) {}
```

**输出**

```js
for (var _iterator = foo, _isArray = Array.isArray(_iterator), _i = 0, _iterator = _isArray ? _iterator : _iterator[Symbol.iterator]();;) {
  var _ref;

  if (_isArray) {
    if (_i >= _iterator.length) break;
    _ref = _iterator[_i++];
  } else {
    _i = _iterator.next();
    if (_i.done) break;
    _ref = _i.value;
  }

  var i = _ref;
}
```

#### Abrupt completions

在松散模式下，迭代器的 `return` 方法不会因抛出错误而导致 abrupt completions。

请参与 [google/traceur-compiler#1773](https://github.com/google/traceur-compiler/issues/1773) 和
[babel/babel#838](https://github.com/babel/babel/issues/838) 了解更多详情。

### 优化

如果使用基本数组，Babel 会将 for-of 循环编译为常规 for 循环。

**输入**

```js
for (let a of [1,2,3]) {}
```

**输出**

```js
var _arr = [1, 2, 3];
for (var _i = 0; _i < _arr.length; _i++) {
  var a = _arr[_i];
}
```
