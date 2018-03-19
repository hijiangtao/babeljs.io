# babel-plugin-transform-flow-comments

> 将 flow 类型注释转换为注释。

你应该使用这个插件而不是 `babel-plugin-flow-strip-types`，以保存 `/* @flow */` 指令并仍然使用流。

[Flow 注释博客](http://flowtype.org/blog/2015/02/20/Flow-Comments.html)

## 示例

**输入**

```javascript
function foo(bar?) {}
function foo2(bar?: string) {}
function foo(x: number): string {}
type B = {
  name: string;
};
export type GraphQLFormattedError = number;
import type A, { B, C } from './types';
import typeof D, { E, F } from './types';
```

**输出**

```javascript
"use strict";

function foo(bar /*:: ?*/) {}
function foo2(bar /*:: ?: string*/) {}
function foo(x /*: number*/) /*: string*/ {}
/*:: type B = {
  name: string;
};*/
/*:: export type GraphQLFormattedError = number;*/
/*:: import type A, { B, C } from './types';*/
/*:: import typeof D, { E, F } from './types';*/
```

## 安装

```sh
npm install --save-dev babel-plugin-transform-flow-comments
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

```json
{
  "plugins": ["transform-flow-comments"]
}
```

### 通过 CLI

```sh
babel --plugins transform-flow-comments script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-flow-comments"]
});
```
