# babel-plugin-transform-es2015-computed-properties

> 将 ES2015 计算属性编译为 ES5

## 示例

**输入**

```js
var obj = {
  ["x" + foo]: "heh",
  ["y" + bar]: "noo",
  foo: "foo",
  bar: "bar"
};
```

**输出**

```js
var _obj;

function _defineProperty(obj, key, value) {
  if (key in obj) {
    Object.defineProperty(obj, key, {
      value: value,
      enumerable: true,
      configurable: true,
      writable: true
    });
  } else {
    obj[key] = value;
  }

  return obj;
}

var obj = (
  _obj = {},
  _defineProperty(_obj, "x" + foo, "heh"),
  _defineProperty(_obj, "y" + bar, "noo"),
  _defineProperty(_obj, "foo", "foo"),
  _defineProperty(_obj, "bar", "bar"),
  _obj
);
```

## 安装

```sh
npm install --save-dev babel-plugin-transform-es2015-computed-properties
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

未包含选项：

```json
{
  "plugins": ["transform-es2015-computed-properties"]
}
```

包含选项：

```json
{
  "plugins": [
    ["transform-es2015-computed-properties", {
      "loose": true
    }]
  ]
}
```

### 通过 CLI

```sh
babel --plugins transform-es2015-computed-properties script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-es2015-computed-properties"]
});
```

## 选项

### `loose`

`boolean`，默认为 `false`

就像类中的方法赋值一样，在松散模式下，计算属性名称使用简单的赋值方式而没有使用定义。这在生产代码中不太可能成为问题。

#### 示例

***输入***

```js
var obj = {
  ["x" + foo]: "heh",
  ["y" + bar]: "noo",
  foo: "foo",
  bar: "bar"
};
```

***输出***

```js
var _obj;

var obj = (
  _obj = {},
  _obj["x" + foo] = "heh",
  _obj["y" + bar] = "noo",
  _obj.foo = "foo",
  _obj.bar = "bar",
  _obj
);
```
