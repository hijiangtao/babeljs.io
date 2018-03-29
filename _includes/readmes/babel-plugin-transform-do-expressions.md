# babel-plugin-transform-do-expressions

> 将 `do` 表达式编译为 ES5

## 详情

> `do { .. }` 表达式执行一个代码块（包含一个或多个语句），并且块内的最终语句结果将作为 do 表达式的结果。

来自 [You Don't Know JS](https://github.com/getify/You-Dont-Know-JS/blob/master/types%20%26%20grammar/ch5.md#statement-completion-values)

它可以被看作是[三元运算符](http://mdn.io/ternary)的复杂版本：

```js
let a = do {
  if(x > 10) {
    'big';
  } else {
    'small';
  }
};
// 相当于：
let a = x > 10 ? 'big' : 'small';
```


这个例子并不是最好的用法，因为它太简单了，使用三元运算符会是更好的选择，但是你可以在 `do { ... }` 表达式中使用多个 `if ... else` 链：

```js
let x = 100;
let y = 20;

let a = do {
  if(x > 10) {
    if(y > 20) {
      'big x, big y';
    } else {
      'big x, small y';
    }
  } else {
    if(y > 10) {
      'small x, big y';
    } else {
      'small x, small y';
    }
  }
};
```

## 示例

### 在 JSX 中
`do` 表达式的一个最有用的用法就是再 JSX 内部。如果我们想要有条件的显示一个组件，我们通常必须调用另一个函数来实现条件并返回正确的值，例如：

```js
const getColoredComponent = color => {
  if(color === 'blue') { return <BlueComponent/>; }
  if(color === 'red') { return <RedComponent/>; }
  if(color === 'green') { return <GreenComponent/>; }
}

const Component = props =>
  <div className='myComponent'>
    {getColoredComponent()}
  </div>
;
```

使用 do 表达式可以在 JSX 中添加逻辑：

```js
const Component = props =>
  <div className='myComponent'>
    {do {
      if(color === 'blue') { <BlueComponent/>; }
      else if(color === 'red') { <RedComponent/>; }
      else if(color === 'green') { <GreenComponent/>; }
    }}
  </div>
;
```


## 安装

```sh
npm install --save-dev babel-plugin-transform-do-expressions
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

```json
{
  "plugins": ["transform-do-expressions"]
}
```

### 通过 CLI

```sh
babel --plugins transform-do-expressions script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-do-expressions"]
});
```

## 参考
- [提案](http://wiki.ecmascript.org/doku.php?id=strawman:do_expressions)
- [You Don't Know JS](https://github.com/getify/You-Dont-Know-JS/blob/master/types%20%26%20grammar/ch5.md#statement-completion-values)
- JSX 内部条件的简洁写法: [reactjs/react-future#35](https://github.com/reactjs/react-future/issues/35#issuecomment-120009203)
