# babel-plugin-transform-es2015-spread

> 将 ES2015 的扩展（spread）编译为 ES5

## 示例

**输入**

```js
var a = ['a', 'b', 'c'];
var b = [...a, 'foo'];
```

**输出**

```js
var a = [ 'a', 'b', 'c' ];
var b = [].concat(a, [ 'foo' ]);
```

## 安装

```sh
npm install --save-dev babel-plugin-transform-es2015-spread
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

没有选项：

```json
{
  "plugins": ["transform-es2015-spread"]
}
```

使用选项：

```json
{
  "plugins": [
    ["transform-es2015-spread", {
      "loose": true
    }]
  ]
}
```

### 通过 CLI

```sh
babel --plugins transform-es2015-spread script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-es2015-spread"]
});
```

## 选项

### `loose`

`boolean`，默认为 `false`。

在松散（loose）模式下，**所有**迭代都会被假定为数组。
