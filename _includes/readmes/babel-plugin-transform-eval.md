# babel-plugin-transform-eval

> 该插件允许 Babel 编译带有字符串的 eval 调用。

## 示例

**输入**

```javascript
eval("(() => 'foo')");
```

**输出**

```javascript
eval("(function () { return 'foo'; })");
```

## 安装

```sh
npm install --save-dev babel-plugin-transform-eval
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

```json
{
  "plugins": ["transform-eval"]
}
```

### 通过 CLI

```sh
babel --plugins transform-eval script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-eval"]
});
```
