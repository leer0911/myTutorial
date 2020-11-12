# 函数

:::tip 问题列表

- 什么是函数？
- 定义函数有哪些方式？
- 什么是闭包？

:::

一个 JavaScript 函数用 function 关键字定义，后面跟着函数名和圆括号。要使用一个函数，你必须将其定义在你希望调用它的作用域内。

查看 [JavaScript 函数详细参考文档](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions) 了解更多。

## 函数声明

一个函数定义（也称为函数声明，或函数语句）由一系列的 function 关键字组成，依次为：

- 函数的名称。
- 函数参数列表，包围在括号中并由逗号分隔。
- 定义函数的 JavaScript 语句，用大括号{}括起来。

例如，以下的代码定义了一个简单的 square 函数：

```js
function square(number) {
  return number * number;
}
```

## 函数表达式

虽然上面的函数声明在语法上是一个语句，但函数也可以由函数表达式创建。这样的函数可以是匿名的；它不必有一个名称。例如，函数 square 也可这样来定义：

```js
const square = function(number) {
  return number * number;
};
var x = square(4); // x gets the value 16
```

然而，函数表达式也可以提供函数名，并且可以用于在函数内部代指其本身，或者在调试器堆栈跟踪中识别该函数：

```js
const factorial = function fac(n) {
  return n < 2 ? 1 : n * fac(n - 1);
};

console.log(factorial(3));
```

## 调用函数

定义一个函数并不会自动的执行它。定义了函数仅仅是赋予函数以名称并明确函数被调用时该做些什么。调用函数才会以给定的参数真正执行这些动作。

```js
square(5);
```

函数一定要处于调用它们的域中，但是函数的声明可以被提升(出现在调用语句之后)，如下例：

```js
console.log(square(5));
/* ... */
function square(n) {
  return n * n;
}
```

函数域是指函数声明时的所在的地方，或者函数在顶层被声明时指整个程序。

## 函数作用域

在函数内定义的变量不能在函数之外的任何地方访问，因为变量仅仅在该函数的域的内部有定义。相对应的，一个函数可以访问定义在其范围内的任何变量和函数。

```js
// 下面的变量定义在全局作用域(global scope)中
var num1 = 20,
  num2 = 3,
  name = "Chamahk";

// 本函数定义在全局作用域
function multiply() {
  return num1 * num2;
}

multiply(); // 返回 60

// 嵌套函数的例子
function getScore() {
  var num1 = 2,
    num2 = 3;

  function add() {
    return name + " scored " + (num1 + num2);
  }

  return add();
}

getScore(); // 返回 "Chamahk scored 5"
```

## 作用域和函数堆栈

### 递归

一个函数可以指向并调用自身。有三种方法可以达到这个目的：

- 函数名
- arguments.callee
- 作用域下的一个指向该函数的变量名

例如，思考一下如下的函数定义：

```js
var foo = function bar() {
  // statements go here
};
```

在这个函数体内，以下的语句是等价的：

- bar()
- arguments.callee() （译者注：ES5 禁止在严格模式下使用此属性）
- foo()

调用自身的函数我们称之为递归函数。在某种意义上说，递归近似于循环。两者都重复执行相同的代码，并且两者都需要一个终止条件（避免无限循环或者无限递归）。例如以下的循环：

```js
var x = 0;
while (x < 10) {
  // "x < 10" 是循环条件
  // do stuff
  x++;
}
```

可以被转化成一个递归函数和对其的调用：

```js
function loop(x) {
  if (x >= 10)
    // "x >= 10" 是退出条件（等同于 "!(x < 10)"）
    return;
  // 做些什么
  loop(x + 1); // 递归调用
}
loop(0);
```

## 嵌套函数和闭包

你可以在一个函数里面嵌套另外一个函数。嵌套（内部）函数对其容器（外部）函数是私有的。它自身也形成了一个闭包。一个闭包是一个可以自己拥有独立的环境与变量的表达式（通常是函数）。

既然嵌套函数是一个闭包，就意味着一个嵌套函数可以”继承“容器函数的参数和变量。换句话说，内部函数包含外部函数的作用域。

可以总结如下：

- 内部函数只可以在外部函数中访问。
- 内部函数形成了一个闭包：它可以访问外部函数的参数和变量，但是外部函数却不能使用它的参数和变量。

下面的例子展示了嵌套函数：

```js
function addSquares(a, b) {
  function square(x) {
    return x * x;
  }
  return square(a) + square(b);
}
a = addSquares(2, 3); // returns 13
b = addSquares(3, 4); // returns 25
c = addSquares(4, 5); // returns 41
```

一个闭包必须保存它可见作用域中所有参数和变量。因为每一次调用传入的参数都可能不同，每一次对外部函数的调用实际上重新创建了一遍这个闭包。

## 多层函数嵌套

函数可以被多层嵌套。例如，函数 A 可以包含函数 B，函数 B 可以再包含函数 C。B 和 C 都形成了闭包，所以 B 可以访问 A，C 可以访问 B 和 A。因此，闭包可以包含多个作用域；他们递归式的包含了所有包含它的函数作用域。这个称之为作用域链。

```js
function A(x) {
  function B(y) {
    function C(z) {
      console.log(x + y + z);
    }
    C(3);
  }
  B(2);
}
A(1); // logs 6 (1 + 2 + 3)
```

## 命名冲突

当同一个闭包作用域下两个参数或者变量同名时，就会产生命名冲突。更近的作用域有更高的优先权，所以最近的优先级最高，最远的优先级最低。这就是作用域链。链的第一个元素就是最里面的作用域，最后一个元素便是最外层的作用域。

```js
function outside() {
  var x = 5;
  function inside(x) {
    return x * 2;
  }
  return inside;
}

outside()(10); // returns 20 instead of 10
```

## 闭包

闭包是 JavaScript 中最强大的特性之一。JavaScript 允许函数嵌套，并且内部函数可以访问定义在外部函数中的所有变量和函数，以及外部函数能访问的所有变量和函数。

但是，外部函数却不能够访问定义在内部函数中的变量和函数。这给内部函数的变量提供了一定的安全性。

此外，由于内部函数可以访问外部函数的作用域，因此当内部函数生存周期大于外部函数时，外部函数中定义的变量和函数的生存周期将比内部函数执行时间长。当内部函数以某一种方式被任何一个外部函数作用域访问时，一个闭包就产生了。

```js
var pet = function(name) {
  //外部函数定义了一个变量"name"
  var getName = function() {
    //内部函数可以访问 外部函数定义的"name"
    return name;
  };
  //返回这个内部函数，从而将其暴露在外部函数作用域
  return getName;
};
myPet = pet("Vivie");

myPet(); // 返回结果 "Vivie"
```

> 使用闭包时仍然要小心避免一些陷阱。如果一个闭包的函数定义了一个和外部函数的某个变量名称相同的变量，那么这个闭包将无法引用外部函数的这个变量。

```js
var createPet = function(name) {
  // Outer function defines a variable called "name"
  return {
    setName: function(name) {
      // Enclosed function also defines a variable called "name"
      name = name; // ??? How do we access the "name" defined by the outer function ???
    },
  };
};
```

## 推荐阅读

[闭包](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Closures)
[箭头函数](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Functions/Arrow_functions)
[this](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/this)
