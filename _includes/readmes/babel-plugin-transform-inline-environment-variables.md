# babel-plugin-transform-inline-environment-variables

内联环境变量

## 示例

### 输入

```js
// 假设 process.env.NODE_ENV 实际上是 "development"
process.env.NODE_ENV;
```

### 输出

```js
"development";
```

## 安装

```sh
npm install babel-plugin-transform-inline-environment-variables
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

```json
// 没有选项：
{
  "plugins": ["transform-inline-environment-variables"]
}

// 使用选项：
{
  "plugins": [
    ["transform-inline-environment-variables", {
      "include": [
        "NODE_ENV"
      ]
    }]
  ]
}
```

### 通过 CLI

```sh
babel --plugins transform-inline-environment-variables script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-inline-environment-variables"]
});
```

## 选项

+ `include` - 需要使用环境变量的数组
+ `exclude` - 不需要使用环境变量的数组
