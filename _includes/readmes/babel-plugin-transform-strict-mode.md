# babel-plugin-transform-strict-mode

> 该插件会在所有文件顶部放置 `"use strict";`，以启用[严格模式](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Strict_mode)。

该插件可以通过 `babel-plugin-transform-es2015-modules-commonjs` 来启用。
如果你想禁用它，你可以关闭 `strict` 或者在 commonjs 转换中添加 `strictMode: false` 选项。

## 示例

**输入**

```javascript
foo();
```

**输出**

```javascript
"use strict";

foo();
```

## 安装

```sh
npm install --save-dev babel-plugin-transform-strict-mode
```

## 使用

### 通过 `.babelrc`（推荐）

**.babelrc**

未包含选项:

```json
{
  "plugins": ["transform-strict-mode"]
}
```

包含选项:

```json
{
  "plugins": [
    ["transform-strict-mode", {
      "strict": true
    }]
  ]
}
```

### 通过 CLI

```sh
babel --plugins transform-strict-mode script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-strict-mode"]
});
```
