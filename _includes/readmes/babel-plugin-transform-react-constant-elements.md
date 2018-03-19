# babel-plugin-transform-react-constant-elements

> 将 React JSX 元素视为值类型，并将它们提高到最高级作用域。

## 示例

**输入**

```jsx
const Hr = () => {
  return <hr className="hr" />;
};
```

**输出**

```jsx
const _ref = <hr className="hr" />;

const Hr = () => {
  return _ref;
};
```

**Deopts**

- **展开运算符**

  ```jsx
  <div {...foobar} />
  ```

- **Refs**

  ```jsx
  <div ref="foobar" />
  <div ref={node => this.node = node} />
  ```

## 安装

```sh
npm install --save-dev babel-plugin-transform-react-constant-elements
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

```json
{
  "plugins": ["transform-react-constant-elements"]
}
```

### 通过 CLI

```sh
babel --plugins transform-react-constant-elements script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-react-constant-elements"]
});
```

## 参考

* [[facebook/react#3226] 优化编译器：重用像 ReactElement 这样的常量值类型](https://github.com/facebook/react/issues/3226)
