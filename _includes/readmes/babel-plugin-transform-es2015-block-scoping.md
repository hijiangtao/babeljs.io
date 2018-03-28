# babel-plugin-transform-es2015-block-scoping

> 将 ES2015 的块级作用域（const 和 let）编译为 ES5。

## 安装

```sh
npm install --save-dev babel-plugin-transform-es2015-block-scoping
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

未包含选项：

```json
{
  "plugins": ["transform-es2015-block-scoping"]
}
```

包含选项：

```json
{
  "plugins": [
    ["transform-es2015-block-scoping", {
      "throwIfClosureRequired": true
    }]
  ]
}
```

### 通过 CLI

```sh
babel --plugins transform-es2015-block-scoping script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-es2015-block-scoping"]
});
```

## 选项 `throwIfClosureRequired`

在下列情况中，无法在转换时添加其他函数和闭包来重写 let/const：

```javascript
for (let i = 0; i < 5; i++) {
  setTimeout(() => console.log(i), 1);
}
```

在对性能要求较高的代码中，这是不可取的。如果设置了 `"throwIfClosureRequired": true`，当 Babel 转译这些代码时会抛出异常，而不是自动附加函数。
