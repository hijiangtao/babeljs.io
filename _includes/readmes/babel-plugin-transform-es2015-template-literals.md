# babel-plugin-transform-es2015-template-literals

> 将 ES2015 模板字符串编译为 ES5

## 示例

**输入**

```javascript
`foo${bar}`;
```

**输出**

```javascript
"foo" + bar;
```

## 安装

```sh
npm install --save-dev babel-plugin-transform-es2015-template-literals
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

没有选项：

```json
{
  "plugins": ["transform-es2015-template-literals"]
}
```

使用选项：

```json
{
  "plugins": [
    ["transform-es2015-template-literals", {
      "loose": true,
      "spec": true
    }]
  ]
}
```

### 通过 CLI

```sh
babel --plugins transform-es2015-template-literals script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-es2015-template-literals"]
});
```

## 选项

### `loose`

`boolean`，默认为 `false`。

在松散（loose）模式下，被标记的模板字符串对象不会被冻结。

### `spec`

`boolean`，默认为 `false`。

该选项用 `String` 包装所有模板字符串的表达式。请查阅 [babel/babel#1065](https://github.com/babel/babel/issues/1065) 了解更多。

**输入**

```javascript
`foo${bar}`;
```

**输出**

```javascript
"foo" + String(bar);
```
