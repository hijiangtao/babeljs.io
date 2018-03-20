# babel-plugin-transform-es2015-sticky-regex

> 将 ES2015 的粘性（sticky）正则表达式编译为 ES5 的 RegExp  构造函数

## 安装

```sh
npm install --save-dev babel-plugin-transform-es2015-sticky-regex
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

```json
{
  "plugins": ["transform-es2015-sticky-regex"]
}
```

### 通过 CLI

```sh
babel --plugins transform-es2015-sticky-regex script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-es2015-sticky-regex"]
});
```
