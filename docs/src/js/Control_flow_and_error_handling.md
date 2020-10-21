# 流程控制与错误处理

:::tip 问题列表

- 什么是语句?
- 条件语句有哪些，怎么用？
- 什么是 Falsy？
- 异常处理语句？

:::

JavaScript 提供一套灵活的语句集，特别是控制流语句，你可以用它在你的应用程序中实现大量的交互性功能。

这一章中的语句，在 [JavaScript 参考](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements) 中包含更为详尽的细节。在 JavaScript 代码中，分号（;）字符被用来分割语句。

在 JavaScript 中，任何表达式(expression)都可以看作一条语句(statement),如果你想了解表达式的详细信息，可以阅读[表达式与运算符（Expressions and operators）](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators)这一章节。

## 语句块

最基本的语句是用于组合语句的语句块。该块由一对大括号界定：

```
{
   statement_1;
   statement_2;
   statement_3;
   .
   .
   .
   statement_n;
}
```

语句块通常用于流程控制，如 if，for，while 等等。

```js
while (x < 10) {
  x++;
}
```

这里 `{ x++; }` 就是语句块。

## 条件判断语句

条件判断语句指的是根据指定的条件所返回的结果（真或假或其它预定义的），来执行特定的语句。JavaScript 支持两种条件判断语句：`if...else` 和 `switch`。

### `if...else 语句`

当一个逻辑条件为真，用 if 语句执行一个语句。当这个条件为假，使用可选择的 else 从句来执行这个语句。if 语句如下所示：

```js
if (condition) {
  statement_1;
} else {
  statement_2;
} //推荐使用严格的语句块模式，语句else可选
```

条件可以是任何返回结果被计算为 true 或 false 的表达式。如果条件表达式返回的是 true，statement_1 语句会被执行；否则，statement_2 被执行。statement_1 和 statement_2 可以是任何语句，甚至你可以将另一个 if 语句嵌套其中。

你也可以组合语句通过使用 else if 来测试连续多种条件判断，就像下面一样:

```js
if (condition_1) {
  statement_1;
} else if (condition_2) {
  statement_2;
} else if (condition_n_1) {
  statement_n;
} else {
  statement_last;
}
```

### 错误的值

下面这些值将被计算出 false (also known as [Falsy](https://developer.mozilla.org/zh-CN/docs/Glossary/Falsy) values):

- false
- undefined
- null
- 0
- NaN
- 空字符串（""）

当传递给条件语句所有其他的值，包括所有对象会被计算为真 。

请不要混淆原始的布尔值 true 和 false 与 Boolean 对象的真和假。例如：

```js
var b = new Boolean(false);
if (b) //结果视为真
if (b == true) // 结果视为假
```

## switch 语句

switch 语句允许一个程序求一个表达式的值并且尝试去匹配表达式的值到一个 case 标签。如果匹配成功，这个程序执行相关的语句。switch 语句如下所示：

```js
switch (expression) {
   case label_1:
      statements_1
      [break;]
   case label_2:
      statements_2
      [break;]
   ...
   default:
      statements_def
      [break;]
}
```

程序首先查找一个与 expression 匹配的 case 语句，然后将控制权转移到该子句，执行相关的语句。如果没有匹配值， 程序会去找 default 语句，如果找到了，控制权转移到该子句，执行相关的语句。如果没有找到 default，程序会继续执行 switch 语句后面的语句。default 语句通常出现在 switch 语句里的最后面，当然这不是必须的。

可选的 break 语句与每个 case 语句相关联， 保证在匹配的语句被执行后程序可以跳出 switch 并且继续执行 switch 后面的语句。如果 break 被忽略，则程序将继续执行 switch 语句中的下一条语句。

## 异常处理语句

你可以用 throw 语句抛出一个异常并且用 try...catch 语句捕获处理它。

### 异常类型

JavaScript 可以抛出任意对象。然而，不是所有对象能产生相同的结果。尽管抛出数值或者字母串作为错误信息十分常见，但是通常用下列其中一种异常类型来创建目标更为高效：

- [ECMAScript exceptions](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Error)
- [DOMException](https://developer.mozilla.org/zh-CN/docs/Web/API/DOMException)、[DOMError](https://developer.mozilla.org/zh-CN/docs/Web/API/DOMError)

```js
function f() {
  try {
    console.log(0);
    throw "bogus";
  } catch (e) {
    console.log(1);
    return true; // this return statement is suspended
    // until finally block has completed
    console.log(2); // not reachable
  } finally {
    console.log(3);
    return false; // overwrites the previous "return"
    console.log(4); // not reachable
  }
  // "return false" is executed now
  console.log(5); // not reachable
}
f(); // console 0, 1, 3; returns false
```
