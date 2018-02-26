# babel-preset-stage-2

> 为包含 stage 2 状态插件准备的 Babel preset。

Stage 2 的要点是：

> **Stage 2:** 草案
>
> **它是什么？** 将会进入规范的提案的第一个版本。从这一点来说，该特性可能最终将被包含在标准中。
>
> **要求是？** 该提案必须包含对该功能的语法和语义的正式说明（使用 ECMAScript 规范的形式语言）。该说明应尽可能完整，但也可以包含待办事项和占位符。该特性必须有两个实验性实现，其中一个可以用诸如 Babel 等转译器实现。
>
> **下一阶段是？** 从现在起，只可进行增量更改。

## 安装

```sh
npm install --save-dev babel-preset-stage-2
```

## 使用

### 通过 `.babelrc` 文件（推荐）

**.babelrc**

```json
{
  "presets": ["stage-2"]
}
```

### 通过 CLI

```sh
babel script.js --presets stage-2
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  presets: ["stage-2"]
});
```
## References

- Axel Rauschmayer 的文章 “Exploring ES2016 and ES2017” 中 "[The TC39 process for ECMAScript features](http://exploringjs.com/es2016-es2017/ch_tc39-process.html)" 相关章节。
