# babel-plugin-transform-member-expression-literals

将有效的成员变量表达式字面量转换为普通标识符。

## 示例

**输入**

```javascript
obj["foo"] = "isValid";

obj.const = "isKeyword";
obj["var"] = "isKeyword";
```

**输出**

```javascript
obj.foo = "isValid";

obj["const"] = "isKeyword";
obj["var"] = "isKeyword";
```

## 安装

```sh
npm install babel-plugin-transform-member-expression-literals
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

```json
{
  "plugins": ["transform-member-expression-literals"]
}
```

### 通过 CLI

```sh
babel --plugins transform-member-expression-literals script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-member-expression-literals"]
});
```
