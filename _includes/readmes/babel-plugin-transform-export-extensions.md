# babel-plugin-transform-export-extensions

> 额外的导出语句编译为 ES2015

## 示例

```js
export * as ns from 'mod';
export v from 'mod';
```

## 安装

```sh
npm install --save-dev babel-plugin-transform-export-extensions
```

## 使用

### 通过 `.babelrc`（推荐）

**.babelrc**

```json
{
  "plugins": ["transform-export-extensions"]
}
```

### 通过 CLI

```sh
babel --plugins transform-export-extensions script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-export-extensions"]
});
```
## 参考

* ~~[提案：ES7 中额外的 export-from 语句](https://github.com/leebyron/ecmascript-more-export-from)~~ (Withdrawn)
* [ECMAScript 提案：export ns from](https://github.com/leebyron/ecmascript-export-ns-from)
* [ECMAScript 提案：export default from](https://github.com/leebyron/ecmascript-export-default-from)
