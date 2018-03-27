# babel-plugin-transform-es2015-modules-systemjs

> 该插件将 ES2015 模块转译为 [SystemJS](https://github.com/systemjs/systemjs)。

## 示例

**输入**

```javascript
export default 42;
```

**输出**

```javascript
System.register([], function (_export, _context) {
  return {
    setters: [],
    execute: function () {
      _export("default", 42);
    }
  };
});
```

## 安装

```sh
npm install --save-dev babel-plugin-transform-es2015-modules-systemjs
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

未包含选项：

```json
{
  "plugins": ["transform-es2015-modules-systemjs"]
}
```

包含选项：

```json
{
  "plugins": [
    ["transform-es2015-modules-systemjs", {
      // outputs SystemJS.register(...)
      "systemGlobal": "SystemJS"
    }]
  ]
}
```

### 通过 CLI

```sh
babel --plugins transform-es2015-modules-systemjs script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-es2015-modules-systemjs"]
});
```
