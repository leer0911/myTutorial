# JavaScript 声明与类型

:::tip 问题列表

- var、let、const 的区别？
- var 中什么是变量提升，声明和未声明变量之前有什么差异？
- 什么是暂存死区？
- 什么是全局变量？
- JavaScript 有哪些数据类型？
- 写出各个数据类型的字面量形式？

:::

## 声明

JavaScript 有三种声明方式。

- [var](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/var) 声明一个变量

- [let](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/let) 声明一个块作用域的局部变量

- [const](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/const) 声明一个块作用域的只读常量

### var

声明和未声明变量之间的差异是：

1. 声明变量的作用域限制在其声明位置的上下文中，而非声明变量总是全局的。
2. 声明变量在任何代码执行前创建，而非声明变量只有在执行赋值操作的时候才会被创建。
3. 声明变量是它所在上下文环境的不可配置属性，非声明变量是可配置的（如非声明变量可以被删除）。

由于这三个差异，未能声明变量将很可能导致意想不到的结果。因此，建议始终声明变量，无论它们是在函数还是全局作用域内。 而且，在 ECMAScript 5 严格模式下，分配给未声明的变量会引发错误。

#### 变量提升

由于变量声明（以及其他声明）总是在任意代码执行之前处理的，所以在代码中的任意位置声明变量总是等效于在代码开头声明。这意味着变量可以在声明之前使用，这个行为叫做“hoisting”。“hoisting”就像是把所有的变量声明移动到函数或者全局代码的开头位置。

**建议始终在作用域顶部声明变量（全局代码的顶部和函数代码的顶部），这可以清楚知道哪些变量是函数作用域（本地），哪些变量在作用域链上解决**

### let

let 允许你声明一个作用域被限制在 [块](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/statements/block)级中的变量、语句或者表达式。与 var 关键字不同的是， var 声明的变量只能是全局或者整个函数块的。 var 和 let 的不同之处在于后者是在编译时才初始化。

```js
function varTest() {
  var x = 1;
  {
    var x = 2; // 同样的变量!
    console.log(x); // 2
  }
  console.log(x); // 2
}

function letTest() {
  let x = 1;
  {
    let x = 2; // 不同的变量
    console.log(x); // 2
  }
  console.log(x); // 1
}
```

在程序和方法的最顶端，let 不像 var 一样，let 不会在全局对象里新建一个属性。比如：

位于函数或代码顶部的 var 声明会给全局对象新增属性, 而 let 不会。例如:

```js
var x = "global";
let y = "global";
console.log(this.x); // "global"
console.log(this.y); // undefined
```

#### 重复声明

在同一个函数或块作用域中重复声明同一个变量会引起 [SyntaxError](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/SyntaxError)。

在 switch 语句中只有一个块，你可能因此而遇到错误：

```js
let x = 1;
switch (x) {
  case 0:
    let foo;
    break;

  case 1:
    let foo; // SyntaxError for redeclaration.
    break;
}
```

#### 暂存死区

与通过 var 声明的有初始化值 undefined 的变量不同，通过 let 声明的变量直到它们的定义被执行时才初始化。在变量初始化前访问该变量会导致 [ReferenceError](https://developer.mozilla.org/en-US/docs/JavaScript/Reference/Global_Objects/ReferenceError)。该变量处在一个自块顶部到初始化处理的“暂存死区”中。

```js
function do_something() {
  console.log(bar); // undefined
  console.log(foo); // ReferenceError
  var bar = 1;
  let foo = 2;
}
```

### const

常量是块级范围的，非常类似用 let 语句定义的变量。但常量的值是无法（通过重新赋值）改变的，也不能被重新声明。

const 声明创建一个值的只读引用。但这并不意味着它所持有的值是不可变的，只是变量标识符不能重新分配。例如，在引用内容是对象的情况下，这意味着可以改变对象的内容（例如，其参数）。

关于“暂存死区”的所有讨论都适用于 let 和 const。

## 变量

在应用程序中，使用变量来作为值的符号名。变量的名字又叫做标识符，其需要遵守一定的规则。

在 JavaScript 中，标识符只能包含字母或数字或下划线（“\_”）或美元符号（“\$”），且不能以数字开头。标识符与字符串不同之处在于字符串是数据，而标识符是代码的一部分。在 JavaScript 中，无法将标识符转换为字符串，但有时可以将字符串解析为标识符。

### 变量的作用域

在函数之外声明的变量，叫做全局变量，因为它可被当前文档中的任何其他代码所访问。在函数内部声明的变量，叫做局部变量，因为它只能在当前函数的内部访问。

### 函数提升

对于函数来说，只有函数声明会被提升到顶部，而函数表达式不会被提升。

```js
/* 函数声明 */

foo(); // "bar"

function foo() {
  console.log("bar");
}

/* 函数表达式 */

baz(); // 类型错误：baz 不是一个函数

var baz = function() {
  console.log("bar2");
};
```

### 全局变量

实际上，全局变量是全局对象的属性。在网页中，（译注：缺省的）全局对象是 window ，所以你可以用形如 window.variable 的语法来设置和访问全局变量。

## 数据类型

最新的 ECMAScript 标准定义了 8 种数据类型：

- 七种基本数据类型:

  - 布尔值（Boolean），有 2 个值分别是：true 和 false.

  - null ， 一个表明 null 值的特殊关键字。 JavaScript 是大小写敏感的，因此 null 与 Null、NULL 或变体完全不同。

  - undefined ，和 null 一样是一个特殊的关键字，undefined 表示变量未赋值时的属性。

  - 数字（Number），整数或浮点数，例如： 42 或者 3.14159。任意精度的整数 (BigInt) ，可以安全地存储和操作大整数，甚至可以超过数字的安全整数限制。

  - 字符串（String），字符串是一串表示文本值的字符序列，例如："Howdy" 。

  - 代表（Symbol） ( 在 ECMAScript 6 中新添加的类型).。一种实例是唯一且不可改变的数据类型。

- 以及对象（Object）。

虽然这些数据类型相对来说比较少，但是通过他们你可以在程序中开发有用的功能。对象（[Objects](https://developer.mozilla.org/zh-CN/docs/JavaScript/Reference/Global_Objects/Object)）和函数（[functions](https://developer.mozilla.org/zh-CN/docs/JavaScript/Reference/Global_Objects/Function)）是这门语言的另外两个基本元素。你可以把对象当作存放值的一个命名容器，然后将函数当作你的程序能够执行的步骤。

### 数据类型的转换

JavaScript 是一种动态类型语言(dynamically typed language)。这意味着你在声明变量时可以不必指定数据类型，而数据类型会在代码执行时会根据需要自动转换。

在包含的数字和字符串的表达式中使用加法运算符（+），JavaScript 会把数字转换成字符串。例如，观察以下语句：

```js
x = "The answer is " + 42; // "The answer is 42"
y = 42 + " is the answer"; // "42 is the answer"
```

在涉及其它运算符（译注：如下面的减号'-'）时，JavaScript 语言不会把数字变为字符串。例如（译注：第一例是数学运算，第二例是字符串运算）：

```js
"37" - 7; // 30
"37" + 7; // "377"
```

### 字面量

字面量是由语法表达式定义的常量；或，通过由一定字词组成的语词表达式定义的常量

在 JavaScript 中，你可以使用各种字面量。这些字面量是脚本中按字面意思给出的固定的值，而不是变量

#### 数组字面量 (Array literals)

```js
var coffees = ["French Roast", "Colombian", "Kona"];
var a = [3];
```

数组字面值中的多余逗号：你不必列举数组字面值中的所有元素。若你在同一行中连写两个逗号（,），数组中就会产生一个没有被指定的元素，其初始值是 undefined

```js
var fish = ["Lion", , "Angel"];
```

理解多余的逗号（在脚本运行时会被如何处理）的含义，对于从语言层面理解 JavaScript 是十分重要的。但是，在你自己写代码时：**显式地将缺失的元素声明为 undefined，将大大提高你的代码的清晰度和可维护性**。

#### 布尔字面量 (Boolean literals)

布尔类型有两种字面量：true 和 false。

不要混淆作为布尔对象的真和假与布尔类型的原始值 true 和 false。布尔对象是原始布尔数据类型的一个包装器。参见 [布尔对象](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Boolean)。

#### 整数 (Integers)

整数可以用十进制（基数为 10）、十六进制（基数为 16）、八进制（基数为 8）以及二进制（基数为 2）表示。

- 十进制整数字面量由一串数字序列组成，且没有前缀 0。
- 八进制的整数以 0（或 0O、0o）开头，只能包括数字 0-7。
- 十六进制整数以 0x（或 0X）开头，可以包含数字（0-9）和字母 a~f 或 A~F。
- 二进制整数以 0b（或 0B）开头，只能包含数字 0 和 1。

#### 浮点数字面量 (Floating-point literals)

浮点数字面值可以有以下的组成部分：

- 一个十进制整数，可以带正负号（即前缀“+”或“ - ”），
- 小数点（“.”），
- 小数部分（由一串十进制数表示），
- 指数部分。

#### 对象字面量 (Object literals)

对象字面值是封闭在花括号对({})中的一个对象的零个或多个"属性名-值"对的（元素）列表

```js
var Sales = "Toyota";

function CarTypes(name) {
  return name === "Honda" ? name : "Sorry, we don't sell " + name + ".";
}

var car = { myCar: "Saturn", getCar: CarTypes("Honda"), special: Sales };

console.log(car.myCar); // Saturn
console.log(car.getCar); // Honda
console.log(car.special); // Toyota
```

#### RegExp 字面值

一个正则表达式是字符被斜线（译注：正斜杠“/”）围成的表达式。下面是一个正则表达式文字的一个例子。

```js
var re = /ab+c/;
```

#### 字符串字面量 (String literals)

字符串字面量是由双引号（"）对或单引号（'）括起来的零个或多个字符。字符串被限定在同种引号之间；也即，必须是成对单引号或成对双引号。下面的例子都是字符串字面值：

```js
"foo";
"bar";
"1234";
"one line \n another line";
"John's cat";
```

#### 模板字面量（template literals）

```js
var name = "Bob",
  time = "today";

`Hello ${name}, how are you ${time}?`;
```

除非有特别需要使用字符串对象，否则,你应当始终使用字符串字面值。要查看字符串对象的有关细节，请参见[字符串对象](https://developer.mozilla.org/zh-CN/docs/JavaScript/Guide/Predefined_Core_Objects#String_Object)。

#### 在字符串中使用的特殊字符

<table class="standard-table"> <caption> 表 2.1 JavaScript 特殊字符 </caption> <thead> <tr> <th scope="col">字符</th> <th scope="col">意思</th> </tr> </thead> <tbody> <tr> <td>\0</td> <td>Null字节</td> </tr> <tr> <td>\b</td> <td>退格符</td> </tr> <tr> <td>\f</td> <td>换页符</td> </tr> <tr> <td>\n</td> <td>换行符</td> </tr> <tr> <td>\r</td> <td>回车符</td> </tr> <tr> <td>\t</td> <td>Tab (制表符)</td> </tr> <tr> <td>\v</td> <td>垂直制表符</td> </tr> <tr> <td>\'</td> <td>单引号</td> </tr> <tr> <td>\"</td> <td>双引号</td> </tr> <tr> <td>\\</td> <td>反斜杠字符（\）</td> </tr> <tr> <td>\<em>XXX</em></td> <td> 由从0到377最多三位八进制数<em>XXX</em>表示的 Latin-1&nbsp;字符。例如，\251是版权符号的八进制序列。 </td> </tr> <tr> <td>\x<em>XX</em></td> <td> 由从00和FF的两位十六进制数字XX表示的Latin-1字符。例如，\ xA9是版权符号的十六进制序列。 </td> </tr> <tr> <td><em>\uXXXX</em></td> <td> 由四位十六进制数字XXXX表示的Unicode字符。例如，\ u00A9是版权符号的Unicode序列。见<a href="/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#String_literals" >Unicode escape sequences</a >&nbsp;(Unicode 转义字符). </td> </tr> <tr> <td>\u<em>{XXXXX}</em></td> <td> Unicode代码点 (code point) 转义字符。例如，\u{2F804} 相当于Unicode转义字符 \uD87E\uDC04的简写。 </td> </tr> </tbody> </table>
