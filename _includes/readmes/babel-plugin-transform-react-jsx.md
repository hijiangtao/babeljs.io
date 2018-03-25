# babel-plugin-transform-react-jsx

> 将 JSX 转换为 React 的函数调用。

## 示例

### React

**输入**

```javascript
var profile = <div>
  <img src="avatar.png" className="profile" />
  <h3>{[user.firstName, user.lastName].join(' ')}</h3>
</div>;
```

**输出**

```javascript
var profile = React.createElement("div", null,
  React.createElement("img", { src: "avatar.png", className: "profile" }),
  React.createElement("h3", null, [user.firstName, user.lastName].join(" "))
);
```

### 自定义

**输入**

```javascript
/** @jsx dom */

var { dom } = require("deku");

var profile = <div>
  <img src="avatar.png" className="profile" />
  <h3>{[user.firstName, user.lastName].join(' ')}</h3>
</div>;
```

**输出**

```javascript
/** @jsx dom */

var dom = require("deku").dom;

var profile = dom( "div", null,
  dom("img", { src: "avatar.png", className: "profile" }),
  dom("h3", null, [user.firstName, user.lastName].join(" "))
);
```

## 安装

```sh
npm install --save-dev babel-plugin-transform-react-jsx
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

没有配置:

```json
{
  "plugins": ["transform-react-jsx"]
}
```

使用配置:

```json
{
  "plugins": [
    ["transform-react-jsx", {
      "pragma": "dom" // default pragma is React.createElement
    }]
  ]
}
```

### 通过 CLI

```sh
babel --plugins transform-react-jsx script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-react-jsx"]
});
```

## 选项

### `pragma`

`string`，默认为 `React.createElement`。

替换在编译 JSX 表达式时使用到的函数。

请注意 `@jsx React.DOM` 编译指示从 React v0.12 开始已被弃用。

### `useBuiltIns`

`boolean`，默认为 `false`。

当传递 props 时，直接使用 Object.assign 而不是使用 Babel 的 helper 扩展。
