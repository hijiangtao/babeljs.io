# babel-plugin-transform-flow-strip-types

> 从输出的代码中去除所有 [flow](http://flowtype.org) 类型的注释和声明。

## 示例

**输入**

```javascript
function foo(one: any, two: number, three?): string {}
```

**输出**

```javascript
function foo(one, two, three) {}
```

## 安装

```sh
npm install --save-dev babel-plugin-transform-flow-strip-types
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

```json
{
  "plugins": ["transform-flow-strip-types"]
}
```

### 通过 CLI

```sh
babel --plugins transform-flow-strip-types script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-flow-strip-types"]
});
```
