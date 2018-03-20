# babel-plugin-transform-es2015-modules-umd

> 该插件将 ES2015 模块转译为 [Universal Module Definition (UMD)](https://github.com/umdjs/umd)。

## 示例

**输入**

```javascript
export default 42;
```

**输出**

```javascript
(function (global, factory) {
  if (typeof define === "function" && define.amd) {
    define(["exports"], factory);
  } else if (typeof exports !== "undefined") {
    factory(exports);
  } else {
    var mod = {
      exports: {}
    };
    factory(mod.exports);
    global.actual = mod.exports;
  }
})(this, function (exports) {
  "use strict";

  Object.defineProperty(exports, "__esModule", {
    value: true
  });

  exports.default = 42;
});
```

## 安装

```sh
npm install --save-dev babel-plugin-transform-es2015-modules-umd
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

```json
{
  "plugins": ["transform-es2015-modules-umd"]
}
```

当模块在浏览器中运行时，你可以覆盖特定的库的名称。例如 `es-promise` 库将自己公开为 `global.Promise` 而不是 `global.es6Promise`。这可以通过：

```json
{
  "plugins": [
    ["transform-es2015-modules-umd", {
      "globals": {
        "es6-promise": "Promise"
      }
    }]
  ]
}
```

#### 默认语义（semantics）

关于默认语义有几点需要注意。

_首先_，该转译使用 [basename](https://en.wikipedia.org/wiki/Basename) 在 UMD 输出中生成全局名称。这意味着你可以导入多个具有相同名称的 basename 的模块，比如：

```js
import fooBar1 from "foo-bar";
import fooBar2 from "./mylib/foo-bar";
```

它会将两个引用传递给同一个浏览器全局：

```js
factory(global.fooBar, global.fooBar);
```

如果你设置插件选项：

```json
{
  "globals": {
    "foo-bar": "fooBAR",
    "./mylib/foo-bar": "mylib.fooBar"
  }
}
```

它仍然会传递给同一个浏览器全局：

```js
factory(global.fooBAR, global.fooBAR);
```

因为转译知识使用导入的 basename。

_其次_，指定的覆盖仍然会传递给 [babel-types/src/converters](https://github.com/babel/babel/blob/master/packages/babel-types/src/converters.js) 中的 `toIdentifier` 函数。
这意味着如果你重写指定为成员的表达式，如：

```json
{
  "globals": {
    "fizzbuzz": "fizz.buzz"
  }
}
```

这将_不会_传递给 `factory(global.fizz.buzz)`。相反，它会根据 `toIdentifier` 中的逻辑传递给 `factory(global.fizzBuzz)`。

_然后_，你无法覆盖导出的全局名称。

#### `exactGlobals: true` 具有更灵活的语义

所有这些行为都会限制 `globals` 映射的灵活性。要删除这些限制，你可以将 `exactGlobals` 选项设置为 `true`。
这样做会告诉插件：

1. 生成全局名称时，始终使用完成的导入字符串而不是 basename
2. 跳过将 `globals` 覆盖传递到 `toIdentifier` 函数。相反，它们完全按照书面使用，所以如果你不使用有效的标识符，或者有效的 uncomputed（点）成员表达式，你会得到 error。
3. 允许导出的全局名称通过 `globals` 映射覆盖。任何覆盖必须再次成为有效的表示符或有效的成员表达式。

因此，如果你将 `exactGlobals` 设置为 `true` 并且并通过任何覆盖，那么第一个例子为：

```js
import fooBar1 from "foo-bar";
import fooBar2 from "./mylib/foo-bar";
```

将传递给：

```js
factory(global.fooBar, global.mylibFooBar);
```

如果你将插件选项设置为：

```json
{
  "globals": {
    "foo-bar": "fooBAR",
    "./mylib/foo-bar": "mylib.fooBar"
  },
  "exactGlobals": true
}
```

那么它会转化为：

```js
factory(global.fooBAR, global.mylib.fooBar)
```

最终，将插件选项设置为：

```json
{
  "plugins": [
    "external-helpers",
    ["transform-es2015-modules-umd", {
      "globals": {
        "my/custom/module/name": "My.Custom.Module.Name"
      },
      "exactGlobals": true
    }]
  ],
  "moduleId": "my/custom/module/name"
}
```

它会传递给：

```js
factory(mod.exports);
global.My = global.My || {};
global.My.Custom = global.My.Custom || {};
global.My.Custom.Module = global.My.Custom.Module || {};
global.My.Custom.Module.Name = mod.exports;
```

### 通过 CLI

```sh
babel --plugins transform-es2015-modules-umd script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-es2015-modules-umd"]
});
```
