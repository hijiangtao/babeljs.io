# babel-plugin-transform-merge-sibling-variables

将兄弟变量合并成一个声明。

## 示例

**输入**

```javascript
// 合并为一个变量声明（VariableDeclaration）
var foo = "bar";
var bar = "foo";
foobar();

// 合并到下一个循环中
var i = 0;
for (var x = 0; x < 10; x++) {}
```

**输出**

```javascript
var foo = "bar",
    bar = "foo";
foobar();

for (var i = 0, x = 0; x < 10; x++) {}
```

## 安装

```sh
npm install babel-plugin-transform-merge-sibling-variables
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

```json
{
  "plugins": ["transform-merge-sibling-variables"]
}
```

### 通过 CLI

```sh
babel --plugins transform-merge-sibling-variables script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-merge-sibling-variables"]
});
```
