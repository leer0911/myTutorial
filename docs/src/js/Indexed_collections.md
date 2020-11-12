# 索引集合类

:::tip 问题列表

- 什么是数组？
- 数组常用方法？

:::

## 什么是数组

数组(array)是一个有序的数据集合，我们可以通过数组名称(name)和索引(index)进行访问。例如，我们定义了一个数组 emp，数组中的每个元素包含了一个雇员的名字以及其作为索引的员工号。那么 `emp[1]` 将会代表 1 号员工，`emp[2]` 将会代表 2 号员工，以此类推。

## 创建数组

以下语句创建等效的数组:

```js
var arr = new Array(element0, element1, ..., elementN);
var arr = Array(element0, element1, ..., elementN);
var arr = [element0, element1, ..., elementN];
```

当单个的数字(Number)传递给 Array()构造函数时，将会被解释为数组长度，并非单个元素。

```js
var arr = [42]; // 创建一个只有唯一元素的数组:
// the number 42.
var arr = Array(42); // 创建一个没有元素的数组,
// 但是数组的长度被设置成42.

// 上面的代码与下面的代码等价
var arr = [];
arr.length = 42;
```

## 填充数组(populating an array)

可以通过给元素赋值来填充数组

```js
var emp = [];
emp[0] = "Casey Jones";
emp[1] = "Phil Lesh";
emp[2] = "August West";
```

可以在创建数组的时候去填充它

```js
var myArray = new Array("Hello", myVar, 3.14159);
var myArray = ["Mango", "Apple", "Orange"];
```

## 引用数组元素(referring to array elements)

可以使用元素的序号来引用数组的元素。例如

```js
var myArray = ["Wind", "Rain", "Fire"];
myArray[0]; // Wind
```

> 注意：数组操作符（方括号 [ ]）也可以用来访问数组的属性(在 JavaScript 中，数组也是对象)。例如：

## 理解 length

在实施层面， JavaScript 实际上是将元素作为标准的对象属性来存储，把数组索引作为属性名。长度属性是特殊的，它总是返回最后一个元素的索引值加 1

记住， JavaScript 数组索引是基于 0 的: 他们从 0 开始，而不是 1。这意味着数组长度属性将比最大的索引值大 1

你也可以分配 length 属性。写一个小于数组元素数量的值会缩短数组，写 0 会彻底清空数组

```js
var cats = ["Dusty", "Misty", "Twiggy"];
console.log(cats.length); // 3

cats.length = 2;
console.log(cats); // logs "Dusty,Misty" - Twiggy has been removed

cats.length = 0;
console.log(cats); // logs nothing; the cats array is empty

cats.length = 3;
console.log(cats); // [undefined, undefined, undefined]
```

## 遍历数组(interating over array)

遍历数组元素并以某种方式处理每个元素是一个常见的操作。以下是最简单的方式：

```js
var colors = ["red", "green", "blue"];
for (var i = 0; i < colors.length; i++) {
  console.log(colors[i]);
}
```

[forEach() ](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach)方法提供了遍历数组元素的其他方法：

```js
var colors = ["red", "green", "blue"];
colors.forEach(function(color) {
  console.log(color);
});
```

注意，在数组定义时省略的元素不会在 forEach 遍历时被列出，但是手动赋值为 undefined 的元素是会被列出的：

```js
var array = ["first", "second", , "fourth"];

// returns ['first', 'second', 'fourth'];
array.forEach(function(element) {
  console.log(element);
});

if (array[2] === undefined) {
  console.log("array[2] is undefined");
} // true

var array = ["first", "second", undefined, "fourth"];

// returns ['first', 'second', undefined, 'fourth'];
array.forEach(function(element) {
  console.log(element);
});
```

## 多维数组

数组是可以嵌套的, 这就意味着一个数组可以作为一个元素被包含在另外一个数组里面。利用 JavaScript 数组的这个特性, 可以创建多维数组。

以下代码创建了一个二维数组。

```js
var a = new Array(4);
for (i = 0; i < 4; i++) {
  a[i] = new Array(4);
  for (j = 0; j < 4; j++) {
    a[i][j] = "[" + i + "," + j + "]";
  }
}
```

这个例子创建的数组拥有以下行数据:

```
Row 0: [0,0] [0,1] [0,2] [0,3]
Row 1: [1,0] [1,1] [1,2] [1,3]
Row 2: [2,0] [2,1] [2,2] [2,3]
Row 3: [3,0] [3,1] [3,2] [3,3]
```

## 使用类数组对象(array-like objects)

一些 JavaScript 对象, 例如 document.getElementsByTagName() 返回的 NodeList 或者函数内部可用的 arguments 对象，他们表面上看起来，外观和行为像数组，但是不共享他们所有的方法。例如 arguments 对象就提供一个 length 属性，但是不实现 forEach() 方法。

Array 的原生(prototype)方法可以用来处理类似数组行为的对象，例如：

```js
function printArguments() {
  Array.prototype.forEach.call(arguments, function(item) {
    console.log(item);
  });
}
```

## 数组的方法(array methods)

- [concat()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/concat) 连接两个数组并返回一个新的数组。

- [join(deliminator = ',')](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/join) 将数组的所有元素连接成一个字符串。

- [push()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/push) 在数组末尾添加一个或多个元素，并返回数组操作后的长度。

- [pop()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/pop) 从数组移出最后一个元素，并返回该元素。

- [shift()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/shift) 从数组移出第一个元素，并返回该元素。

- [unshift()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/shift) 在数组开头添加一个或多个元素，并返回数组的新长度。

- [slice(start_index, upto_index)](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/slice) 从数组提取一个片段，并作为一个新数组返回。

- [splice(index, count_to_remove, addElement1, addElement2, ...)](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/splice) 从数组移出一些元素，（可选）并替换它们。

- [reverse()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/reverse) 颠倒数组元素的顺序：第一个变成最后一个，最后一个变成第一个。

- [sort()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/sort) 给数组元素排序。

- [indexOf(searchElement[, fromIndex])](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/indexOf) 在数组中搜索 searchElement 并返回第一个匹配的索引。

- [lastIndexOf(searchElement[, fromIndex])](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/lastIndexOf) 和 indexOf 差不多，但这是从结尾开始，并且是反向搜索。

- [forEach(callback[, thisObject])](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach) 在数组每个元素项上执行 callback。

- [map(callback[, thisObject])](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/map) 在数组的每个单元项上执行 callback 函数，并把返回包含回调函数返回值的新数组（译者注：也就是遍历数组，并通过 callback 对数组元素进行操作，并将所有操作结果放入数组中并返回该数组）。

- [filter(callback[, thisObject])](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/filter) 返回一个包含所有在回调函数上返回为 true 的元素的新数组（译者注：callback 在这里担任的是过滤器的角色，当元素符合条件，过滤器就返回 true，而 filter 则会返回所有符合过滤条件的元素）。

- [every(callback[, thisObject])](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/every) 当数组中每一个元素在 callback 上被返回 true 时就返回 true（译者注：同上，every 其实类似 filter，只不过它的功能是判断是不是数组中的所有元素都符合条件，并且返回的是布尔值）。

- [some(callback[, thisObject])](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/some) 只要数组中有一项在 callback 上被返回 true，就返回 true（译者注：同上，类似 every，不过前者要求都符合筛选条件才返回 true，后者只要有符合条件的就返回 true）。

- [reduce(callback[, initialValue])](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce) 使用回调函数 callback(firstValue, secondValue) 把数组列表计算成一个单一值（译者注：他数组元素两两递归处理的方式把数组计算成一个值）

- [reduceRight(callback[, initalvalue])](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/reduceRight) 和 reduce()相似，但这从最后一个元素开始的。

## 推荐阅读

- [索引集合类](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Indexed_collections)
