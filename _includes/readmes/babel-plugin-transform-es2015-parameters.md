# babel-plugin-transform-es2015-parameters

> 将 ES2015 的默认（defalut）参数和多余（reset）参数编译为 ES5

该插件将 ES2015 的参数转译为 ES2015

- 解构参数（Destructuring parameters）
- 默认参数（Default parameters）
- 多余参数（Rest parameters）

## 安装

```sh
npm install --save-dev babel-plugin-transform-es2015-parameters
```

## 注意事项

默认参数解析为 `let` 声明以保留正确的语义。如果你的环境不支持，那么你需要使用 [transform-block-scoping](http://babeljs.cn/docs/plugins/transform-es2015-block-scoping) 插件。

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

```json
{
  "plugins": ["transform-es2015-parameters"]
}
```

### 通过 CLI

```sh
babel --plugins transform-es2015-parameters script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-es2015-parameters"]
});
```
