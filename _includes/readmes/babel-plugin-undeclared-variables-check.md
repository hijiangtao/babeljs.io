# babel-plugin-undeclared-variables-check

> 在引用未声明变量时，使用该插件会在编译时抛出异常错误。

## 示例

**输入**

```javascript
function foo() {}
foo();
bar();
```

**输出**

```
ReferenceError: stdin: Line 3: Reference to undeclared variable "bar" - did you mean "foo"?
  1 | function foo() {}
  2 | foo();
> 3 | bar();
    | ^
  4 |
```

## 安装

```sh
npm install --save-dev babel-plugin-undeclared-variables-check
```

## 使用

### 通过 `.babelrc` （推荐）

**.babelrc**

```json
{
  "plugins": ["undeclared-variables-check"]
}
```

### 通过 CLI

```sh
babel --plugins undeclared-variables-check script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["undeclared-variables-check"]
});
```
