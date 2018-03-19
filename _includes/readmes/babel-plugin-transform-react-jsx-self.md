# babel-plugin-transform-react-jsx-self

> 将 `__self` props 添加到 JSX 元素中，React 将使用它来生成一些运行时警告。所有 React 用户都应该在开发模式下启用此插件。

## 示例

**输入**

```
<sometag />
```

**输出**

```
<sometag __self={this} />
```

## 安装

```sh
npm install --save-dev babel-plugin-transform-react-jsx-self
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

```json
{
  "plugins": ["transform-react-jsx-self"]
}
```

### 通过 CLI

```sh
babel --plugins transform-react-jsx-self script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-react-jsx-self"]
});
```
