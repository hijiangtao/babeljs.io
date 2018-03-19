# babel-plugin-transform-proto-to-assign

> 这个插件允许 Babel 将所有 `__proto` 赋值转换为一个方法，该方法会将所有属性进行浅拷贝。

## 详情

这意味着**将会**按以下方式工作：

```javascript
var foo = { a: 1 };
var bar = { b: 2 };
bar.__proto__ = foo;
bar.a; // 1
bar.b; // 2
```

但是**不会**按以下方式：

```javascript
var foo = { a: 1 };
var bar = { b: 2 };
bar.__proto__ = foo;
bar.a; // 1
foo.a = 2;
bar.a; // 1 - 应该是2，但请记住，在没有任何限制的情况下，它是一个简单的拷贝
```

如果你打算使用此插件，则必须注意这种情况。

## 示例

**输入**

```javascript
bar.__proto__ = foo;
```

**输出**

```javascript
var _defaults = ...;

_defaults(bar, foo);
```

## 安装

```sh
npm install --save-dev babel-plugin-transform-proto-to-assign
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

```json
{
  "plugins": ["transform-proto-to-assign"]
}
```

### 通过 CLI

```sh
babel --plugins transform-proto-to-assign script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-proto-to-assign"]
});
```
