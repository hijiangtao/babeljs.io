# babel-plugin-transform-undefined-to-void

许多 JavaScript 实现允许 undefined 被覆盖，这可能会导致代码出现难以追踪的特殊错误。

如果返回的 undefined 被覆盖，该插件会将 `undefined` 转译成 `void 0`。

## 示例

**输入**

```javascript
foo === undefined;
```

**输出**

```javascript
foo === void 0;
```

## 安装

```sh
npm install babel-plugin-transform-undefined-to-void
```

## 使用

### 通过 `.babelrc`（推荐）

**.babelrc**

```json
{
  "plugins": ["transform-undefined-to-void"]
}
```

### 通过 CLI

```sh
babel --plugins transform-undefined-to-void script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-undefined-to-void"]
});
```
