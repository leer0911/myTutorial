# 表达式与运算符

:::tip 问题列表

- JavaScript 有哪些赋值操作符？
- JavaScript 有哪些比较操作符？
- JavaScript 有哪些逻辑操作符？
- 什么是短路求值？
- typeof 的作用？
- instanceof 的作用？
- 什么是 JavaScript 表达式？

:::

本章描述了 JavaScript 的表达式和运算符，包括了赋值，比较，算数，位运算，逻辑，字符串，三元等等。属于记忆性内容，可以跟着[教程](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Expressions_and_Operators)详细过一遍，可以阅读本篇梳理后的内容。

完整详细的运算符列表和表达式可以参见 [reference](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators)

JavaScript 拥有如下类型的运算符：

- 赋值运算符(Assignment operators)
- 比较运算符(Comparison operators)
- 算数运算符(Arithmetic operators)
- 位运算符(Bitwise operators)
- 逻辑运算符(Logical operators)
- 字符串运算符(String operators)
- 条件（三元）运算符(Conditional operator)
- 逗号运算符(Comma operator)
- 一元运算符(Unary operators)
- 关系运算符(Relational operator)

## 赋值运算符

一个 赋值运算符(assignment operator) 将它右边操作数的值赋给它左边的操作数。最简单的赋值运算符是等于（=），它将右边的操作数值赋给左边的操作数。那么 x = y 就是将 y 的值赋给 x。

还有一些复合赋值操作符，它们是下表列出的这些操作的缩写：

<table class="standard-table"> <caption> 复合赋值运算符 </caption> <thead> <tr> <th>名字</th> <th>简写的操作符</th> <th>含义</th> </tr> </thead> <tbody> <tr> <td> <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Assignment_Operators#Assignment" >赋值(Assignment)</a > </td> <td><code>x = y</code></td> <td><code>x = y</code></td> </tr> <tr> <td> <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Assignment_Operators#Addition_assignment" >加法赋值(Addition assignment)</a > </td> <td><code>x += y</code></td> <td><code>x = x + y</code></td> </tr> <tr> <td> <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Assignment_Operators#Subtraction_assignment" >减法赋值(Subtraction assignment)</a > </td> <td><code>x -= y</code></td> <td><code>x = x - y</code></td> </tr> <tr> <td> <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Assignment_Operators#Multiplication_assignment" >乘法赋值(Multiplication assignment)</a > </td> <td><code>x *= y</code></td> <td><code>x = x * y</code></td> </tr> <tr> <td> <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Assignment_Operators#Division_assignment" >除法赋值(Division assignment)</a > </td> <td><code>x /= y</code></td> <td><code>x = x / y</code></td> </tr> <tr> <td> <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Assignment_Operators#Remainder_assignment" >求余赋值(Remainder assignment)</a > </td> <td><code>x&nbsp;%= y</code></td> <td><code>x = x&nbsp;% y</code></td> </tr> <tr> <td> <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Assignment_Operators#Exponentiation_assignment" >求幂赋值(Exponentiation assignment)</a > </td> <td><code>x **= y</code></td> <td><code>x = x ** y</code></td> </tr> <tr> <td> <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Assignment_Operators#Left_shift_assignment" >左移位赋值(Left shift assignment)</a > </td> <td><code>x &lt;&lt;= y</code></td> <td><code>x = x &lt;&lt; y</code></td> </tr> <tr> <td> <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Assignment_Operators#Right_shift_assignment" >右移位赋值(Right shift assignment)</a > </td> <td><code>x &gt;&gt;= y</code></td> <td><code>x = x &gt;&gt; y</code></td> </tr> <tr> <td> <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Assignment_Operators#Unsigned_right_shift_assignment" >无符号右移位赋值(Unsigned right shift assignment)</a > </td> <td><code>x &gt;&gt;&gt;= y</code></td> <td><code>x = x &gt;&gt;&gt; y</code></td> </tr> <tr> <td> <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Assignment_Operators#Bitwise_AND_assignment" >按位与赋值(Bitwise AND assignment)</a > </td> <td><code>x &amp;= y</code></td> <td><code>x = x &amp; y</code></td> </tr> <tr> <td> <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Assignment_Operators#Bitwise_XOR_assignment" >按位异或赋值(Bitwise XOR assignment)</a > </td> <td><code>x ^= y</code></td> <td><code>x = x ^ y</code></td> </tr> <tr> <td> <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Assignment_Operators#Bitwise_OR_assignment" >按位或赋值(Bitwise OR assignment)</a > </td> <td><code>x |= y</code></td> <td><code>x = x | y</code></td> </tr> </tbody> </table>

## 比较运算符

比较运算符比较它的操作数并返回一个基于表达式是否为真的逻辑值，比较运算符比较它的操作数并返回一个基于表达式是否为真的逻辑值。操作数可以是数字，字符串，逻辑，对象值。

字符串比较是基于标准的字典顺序，使用 Unicode 值。在多数情况下，如果两个操作数不是相同的类型， JavaScript 会尝试转换它们为恰当的类型来比较。这种行为通常发生在数字作为操作数的比较。

类型转换的例外是使用 `===` 和 `!==` 操作符，它们会执行严格的相等和不相等比较。这些运算符不会在检查相等之前转换操作数的类型。

**避免记忆复杂的转换规则，建议实际编码时采用 `===` 和 `!==` 操作符**

## 算术运算符

算术运算符使用数值(字面量或者变量)作为操作数并返回一个数值.标准的算术运算符就是加减乘除(+ - \* /)。当操作数是浮点数时，这些运算符表现得跟它们在大多数编程语言中一样（特殊要注意的是，除零会产生 Infinity）。例如：

```js
1 / 2; // 0.5
1 / 2 == 1.0 / 2.0; // true
```

除了标准的算术运算符（+， - ，\* /），JavaScript 还提供了：

- 求余(%) 二元运算符. 返回相除之后的余数。如 `12 % 5 返回 2`

- 自增(++) 一元运算符. 将操作数的值加一. 如果放在操作数前面 (++x), 则返回加一后的值; 如果放在操作数后面 (x++), 则返回操作数原值,然后再将操作数加一

- 自减(--) 一元运算符. 将操作数的值减一. 前后缀两种用法的返回值类似自增运算符

- 指数运算符(\*\*) 计算 base(底数) 的 exponent(指数)次方, 表示为 baseexponent。如 `2 ** 3 returns 8`

## 逻辑运算符

逻辑运算符常用于布尔（逻辑）值之间; 当操作数都是布尔值时，返回值也是布尔值。 不过实际上&&和||返回的是一个特定的操作数的值，所以当它用于非布尔值的时候，返回值就可能是非布尔值。

<table class="fullwidth-table" style="height: 190px; width: 1316px"> <thead> <tr> <th scope="col">运算符</th> <th scope="col">范例</th> <th scope="col">描述</th> </tr> </thead> <tbody> <tr> <td> <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_Operators#Logical_AND" >逻辑与</a ><code>&nbsp;(&amp;&amp;</code>) </td> <td><code>expr1 &amp;&amp; expr2</code></td> <td> (逻辑与) 如果expr1能被转换为false，那么返回expr1；否则，返回<code>expr2</code>。因此<code>，&amp;&amp;</code>用于布尔值时，当操作数都为true时返回true；否则返回false. </td> </tr> <tr> <td> <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_Operators#Logical_OR" >逻辑或&nbsp;</a >(<code>||</code>) </td> <td><code>expr1 || expr2</code></td> <td> (逻辑或) 如果expr1能被转换为true，那么返回expr1；否则，返回<code>expr2</code>。因此，||用于布尔值时，当任何一个操作数为true则返回true；如果操作数都是false则返回false。 </td> </tr> <tr> <td> <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_Operators#Logical_NOT" >逻辑非</a ><code>&nbsp;(!)</code> </td> <td><code>!expr</code></td> <td>(逻辑非) 如果操作数能够转换为true则返回false；否则返回true。</td> </tr> </tbody> </table>

下面是&&（逻辑"与"）操作符的示例

```js
var a1 = true && true; // t && t returns true
var a2 = true && false; // t && f returns false
var a3 = false && true; // f && t returns false
var a4 = false && 3 == 4; // f && f returns false
var a5 = "Cat" && "Dog"; // t && t returns Dog
var a6 = false && "Cat"; // f && t returns false
var a7 = "Cat" && false; // t && f returns false
```

下面是||（逻辑"或"）操作符的示例

```js
var o1 = true || true; // t || t returns true
var o2 = false || true; // f || t returns true
var o3 = true || false; // t || f returns true
var o4 = false || 3 == 4; // f || f returns false
var o5 = "Cat" || "Dog"; // t || t returns Cat
var o6 = false || "Cat"; // f || t returns Cat
var o7 = "Cat" || false; // t || f returns Cat
```

下面是！（逻辑"非"）操作符的示例

```js
var n1 = !true; // !t returns false
var n2 = !false; // !f returns true
var n3 = !"Cat"; // !t returns false
```

### 短路求值

作为逻辑表达式进行求值是从左到右，它们是为可能的“短路”的出现而使用以下规则进行测试：

- false && anything // 被短路求值为 false
- true || anything // 被短路求值为 true

逻辑的规则，保证这些评估是总是正确的。请注意，上述表达式的 anything 部分不会被求值，所以这样做不会产生任何副作用。

## 条件（三元）运算符

条件运算符是 JavaScript 中唯一需要三个操作数的运算符。运算的结果根据给定条件在两个值中取其一。语法为：

```
条件 ? 值1 : 值2
```

如果条件为真，则结果取值 1。否则为值 2。你能够在任何允许使用标准运算符的地方使用条件运算符。

```js
var status = age >= 18 ? "adult" : "minor";
```

## 逗号操作符

逗号操作符（,）对两个操作数进行求值并返回最终操作数的值。它常常用在 for 循环中，在每次循环时对多个变量进行更新。

```js
var x = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];
var a = [x, x, x, x, x];

for (var i = 0, j = 9; i <= j; i++, j--)
  console.log("a[" + i + "][" + j + "]= " + a[i][j]);
```

## 一元操作符

一元操作符仅对应一个操作数。

[delete](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/delete) 操作符，删除一个对象或一个对象的属性或者一个数组中某一个键值。语法如下:

```js
delete objectName;
delete objectName.property;
delete objectName[index];
```

objectName 是一个对象名，property 是一个已经存在的属性，index 是数组中的一个已经存在的键值的索引值。

你能使用 delete 删除各种各样的隐式声明， 但是被 var 声明的除外。

如果 delete 操作成功，属性或者元素会变成 undefined。如果 delete 可行会返回 true，如果不成功返回 false。

### 删除数组元素

删除数组中的元素时，数组的长度是不变的，例如删除 a[3], a[4]，a[4]和 a[3] 仍然存在变成了 undefined。

```js
var trees = new Array("redwood", "bay", "cedar", "oak", "maple");
delete trees[3];
if (3 in trees) {
  // 不会被执行
}
```

## `typeof`

typeof 操作符 可通过下面 2 种方式使用：

```js
typeof operand;
typeof operand;
```

```js
var myFun = new Function("5 + 2");
var shape = "round";
var size = 1;
var today = new Date();

typeof myFun; // returns "function"
typeof shape; // returns "string"
typeof size; // returns "number"
typeof today; // returns "object"
typeof dontExist; // returns "undefined"
```

其他类型

```js
typeof true; // returns "boolean"
typeof null; // returns "object"
typeof 62; // returns "number"
typeof "Hello world"; // returns "string"
typeof Date; // returns "function"
typeof Function; // returns "function"
typeof Math; // returns "object"
typeof Option; // returns "function"
typeof String; // returns "function"
```

## void

void 运算符运用方法如下：

```js
void expression;
void expression;
```

void 运算符,表明一个运算没有返回值。expression 是 javaScript 表达式，括号中的表达式是一个可选项，当然使用该方式是一种好的形式。

## 关系操作符

关系操作符对操作数进行比较，根据比较结果真或假，返回相应的布尔值。

### `in`

in 操作符，如果所指定的属性确实存在于所指定的对象中，则会返回 true，语法如下：

```
propNameOrNumber in objectName
```

在这里 propNameOrNumber 可以是一个代表着属性名的字符串或者是一个代表着数组索引的数值表达式，而 objectName 则是一个对象名。

常见用法

```js
// Arrays
var trees = new Array("redwood", "bay", "cedar", "oak", "maple");
0 in trees; // returns true
3 in trees; // returns true
6 in trees; // returns false
"bay" in trees; // returns false (you must specify the index number,
// not the value at that index)
"length" in trees; // returns true (length is an Array property)

// Predefined objects
"PI" in Math; // returns true
var myString = new String("coral");
"length" in myString; // returns true

// Custom objects
var mycar = { make: "Honda", model: "Accord", year: 1998 };
"make" in mycar; // returns true
"model" in mycar; // returns true
```

### `instanceof`

如果所判别的对象确实是所指定的类型，则返回 true。其语法如下：

```
objectName instanceof objectType
```

objectName 是需要做判别的对象的名称,而 objectType 是假定的对象的类型, 例如 Date 或 Array.

当你需要确认一个对象在运行时的类型时，可使用 instanceof. 例如，需要 catch 异常时，你可以针对抛出异常的类型，来做不同的异常处理。

例如, 下面的代码使用 instanceof 去判断 theDay 是否是一个 Date 对象. 因为 theDay 是一个 Date 对象, 所以 if 中的代码会执行.

```js
var theDay = new Date(1995, 12, 17);
if (theDay instanceof Date) {
  // statements to execute
}
```

## 运算符优先级

运算符的优先级，用于确定一个表达式的计算顺序。在你不能确定优先级时，可以通过使用括号显式声明运算符的优先级。

下表列出了描述符的优先级，从最高到最低。

<table class="standard-table"> <thead> <tr> <th scope="col">Operator type</th> <th scope="col">Individual operators</th> </tr> </thead> <tbody> <tr> <td>member</td> <td><code>. []</code></td> </tr> <tr> <td>call / create instance</td> <td><code>() new</code></td> </tr> <tr> <td>negation/increment</td> <td><code>! ~ - + ++ -- typeof void delete</code></td> </tr> <tr> <td>multiply/divide</td> <td><code>* / %</code></td> </tr> <tr> <td>addition/subtraction</td> <td><code>+ -</code></td> </tr> <tr> <td>bitwise shift</td> <td><code>&lt;&lt; &gt;&gt; &gt;&gt;&gt;</code></td> </tr> <tr> <td>relational</td> <td><code>&lt; &lt;= &gt; &gt;= in instanceof</code></td> </tr> <tr> <td>equality</td> <td><code>== != === !==</code></td> </tr> <tr> <td>bitwise-and</td> <td><code>&amp;</code></td> </tr> <tr> <td>bitwise-xor</td> <td><code>^</code></td> </tr> <tr> <td>bitwise-or</td> <td><code>|</code></td> </tr> <tr> <td>logical-and</td> <td><code>&amp;&amp;</code></td> </tr> <tr> <td>logical-or</td> <td><code>||</code></td> </tr> <tr> <td>conditional</td> <td><code>?:</code></td> </tr> <tr> <td>assignment</td> <td> <code >= += -= *= /= %= &lt;&lt;= &gt;&gt;= &gt;&gt;&gt;= &amp;= ^= |=</code > </td> </tr> <tr> <td>comma</td> <td><code>,</code></td> </tr> </tbody> </table>

## 表达式

表达式是一组代码的集合，它返回一个值。

每一个合法的表达式都能计算成某个值，但从概念上讲，有两种类型的表达式：有副作用的（比如赋值）和单纯计算求值的。

JavaScript 有以下表达式类型：

- 算数: 得出一个数字, 例如 3.14159. (通常使用 arithmetic operators.)
- 字符串: 得出一个字符串, 例如, "Fred" 或 "234". (通常使用 string operators.)
- 逻辑值: 得出 true 或者 false. (经常涉及到 logical operators.)
- 基本表达式: javascript 中基本的关键字和一般表达式。
- 左值表达式: 分配给左值。
