# babel-plugin-transform-react-jsx-source

> 将源文件和行号添加到 JSX 元素中。

## 示例

**输入**

```
<sometag />
```

**输出**

```
<sometag __source={ { fileName: 'this/file.js', lineNumber: 10 } } />
```

## 安装

```sh
npm install --save-dev babel-plugin-transform-react-jsx-source
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

```json
{
  "plugins": ["transform-react-jsx-source"]
}
```

### 通过 CLI

```sh
babel --plugins transform-react-jsx-source script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-react-jsx-source"]
});
```
