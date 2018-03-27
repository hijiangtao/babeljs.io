# babel-plugin-transform-es2015-duplicate-keys

> 将具有重复键的对象编译为严格模式下的 ES5。

该插件实际上会将对象中的重复键转换为计算属性，然后必须由 [transform-es2015-computed-properties](http://babeljs.cn/docs/plugins/transform-es2015-computed-properties) 插件处理。最终结果为不具有重复键的对象字面量。

## 示例

**输入**

```javascript
var x = { a: 5, a: 6 };
var y = {
  get a() {},
  set a(x) {},
  a: 3
};
```

**输出**

```javascript
var x = { a: 5, ["a"]: 6 };
var y = {
  get a() {},
  set a(x) {},
  ["a"]: 3
};
```

## 安装

```sh
npm install --save-dev babel-plugin-transform-es2015-duplicate-keys
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

```json
{
  "plugins": ["transform-es2015-duplicate-keys"]
}
```

### 通过 CLI

```sh
babel --plugins transform-es2015-duplicate-keys script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-es2015-duplicate-keys"]
});
```
