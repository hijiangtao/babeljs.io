# babel-plugin-transform-es2015-classes

> 将 ES2015 的类编译为 ES5

## 注意事项

由于 ES5 中的限制(对于 [es2015-classes](http://babeljs.io/docs/plugins/transform-es2015-classes) 插件来说)，无法对子类（如 `Date`，`Array`，`DOM` 等）进行正确分类。
你可以尝试使用基于 `Object.setPrototypeOf` 和 `Reflect.construct` 的 [babel-plugin-transform-builtin-extend](https://github.com/loganfsmyth/babel-plugin-transform-builtin-extend) 插件，但它同样也有些限制。

## 安装

```sh
npm install --save-dev babel-plugin-transform-es2015-classes
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

```js
// 未包含选项
{
  "plugins": ["transform-es2015-classes"]
}

// 包含选项
{
  "plugins": [
    ["transform-es2015-classes", {
      "loose": true
    }]
  ]
}
```

### 通过 CLI

```sh
babel --plugins transform-es2015-classes script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-es2015-classes"]
});
```

## 选项

### `loose`

`boolean`，默认为 `false`。

#### 方法枚举

请注意，在松散（loose）模式下，类方法**是**可枚举的。这并不符合规范，你可能会遇到问题。

#### 方法分配

松散模式下，方法是在类的原型上通过使用简单赋值的方式来替代定义的方式。这可能导致以下代码不能正常工作：

```javascript
class Foo {
  set bar() {
    throw new Error("foo!");
  }
}

class Bar extends Foo {
  bar() {
    // 当定义该方法时，会引发错误
  }
}
```

当定义了 `Bar.prototype.foo` 时，它会触发 `Foo` 上的 setter。这一般不太可能会出现在生产代码中，但需要记住（可能会出现问题）。
