# babel-plugin-transform-react-inline-elements

> 使用更适合生产环境的 `babelHelpers.jsx` 函数替换 `React.createElement` 。

## 示例

**输入**

```javascript
<Baz foo="bar" key="1"></Baz>;
```

**输出**

```javascript
babelHelpers.jsx(Baz, {
  foo: "bar"
}, "1");

/**
 * 替代
 *
 * React.createElement(Baz, {
 *   foo: "bar",
 *   key: "1",
 * });
 */
```

**Deopt**

```js
// 当使用 `ref` 或 `object rest spread` 时，插件仍然会使用 React.createElement。
<Foo ref="bar" />
<Foo {...bar} />
```

## 安装

```sh
npm install --save-dev babel-plugin-transform-react-inline-elements
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

```json
{
  "plugins": ["transform-react-inline-elements"]
}
```

### 通过 CLI

```sh
babel --plugins transform-react-inline-elements script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-react-inline-elements"]
});
```

## 参考

* [[facebook/react#3228] 优化编译器：内联 React 元素](https://github.com/facebook/react/issues/3228)
