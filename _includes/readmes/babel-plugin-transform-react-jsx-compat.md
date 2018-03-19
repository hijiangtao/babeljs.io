# babel-plugin-transform-react-jsx-compat

> 将 JSX 转换为 React Pre-0.12 的函数调用方式。

## 示例

**输入**

```javascript
var profile = <div>
  <img src="avatar.png" class="profile" />
  <h3>{[user.firstName, user.lastName].join(' ')}</h3>
</div>;
```

**输出**

```javascript
var profile = React.DOM.div(null,
  React.DOM.img({ src: "avatar.png", "class": "profile" }),
  React.DOM.h3(null, [user.firstName, user.lastName].join(" "))
);
```

## 安装

```sh
npm install --save-dev babel-plugin-transform-react-jsx-compat
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

```json
{
  "plugins": ["transform-react-jsx-compat"]
}
```

### 通过 CLI

```sh
babel --plugins transform-react-jsx-compat script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-react-jsx-compat"]
});
```
