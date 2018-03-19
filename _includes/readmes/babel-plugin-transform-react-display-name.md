# babel-plugin-transform-react-display-name

> 将 displayName 添加到 `createReactClass`（以及 `React.createClass`） 的调用中。

## 示例

**输入**

```js
var foo = React.createClass({}); // React <= 15
var bar = createReactClass({});  // React 16+
```

**输出**

```js
var foo = React.createClass({
  displayName: "foo"
}); // React <= 15
var bar = createReactClass({
  displayName: "bar"
}); // React 16+
```

## 安装

```sh
npm install --save-dev babel-plugin-transform-react-display-name
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

```json
{
  "plugins": ["transform-react-display-name"]
}
```

### 通过 CLI

```sh
babel --plugins transform-react-display-name script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-react-display-name"]
});
```
