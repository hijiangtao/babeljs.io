# babel-traverse

> babel-traverse 维护整个树(AST)状态，负责替换、删除和添加节点。

## 安装

```sh
$ npm install --save babel-traverse
```

## 使用

它可以与 Babylon 搭配使用，用于遍历和更新节点:

```js
import * as babylon from "babylon";
import traverse from "babel-traverse";

const code = `function square(n) {
  return n * n;
}`;

const ast = babylon.parse(code);

traverse(ast, {
  enter(path) {
    if (path.isIdentifier({ name: "n" })) {
      path.node.name = "x";
    }
  }
});
```
[:book: **阅读完整文档**](https://github.com/thejameskyle/babel-handbook/blob/master/translations/en/plugin-handbook.md#babel-traverse)
