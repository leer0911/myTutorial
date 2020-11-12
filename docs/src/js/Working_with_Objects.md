# 使用对象

:::tip 问题列表

- 什么是对象？
- 枚举一个对象有哪些方法？

:::

一个对象就是一系列属性的集合，一个属性包含一个名和一个值。一个属性的值可以是函数，这种情况下属性也被称为方法。除了浏览器里面预定义的那些对象之外，你也可以定义你自己的对象。

```js
const obj = { name: "lee" };
```

可以通过点符号来访问一个对象的属性

```js
obj.name;
```

## 枚举一个对象的所有属性

- [for...in](https://developer.mozilla.org/zh-CN/docs/JavaScript/Reference/Statements/for...in) 循环。该方法依次访问一个对象及其原型链中所有可枚举的属性。

- [Object.keys(o)](https://developer.mozilla.org/zh-CN/docs/JavaScript/Reference/Global_Objects/Object/keys) 该方法返回对象 o 自身包含（不包括原型中）的所有可枚举属性的名称的数组。

- [Object.getOwnPropertyNames(o)](https://developer.mozilla.org/zh-CN/docs/JavaScript/Reference/Global_Objects/Object/getOwnPropertyNames) 该方法返回对象 o 自身包含（不包括原型中）的所有属性(无论是否可枚举)的名称的数组。

## 创建新对象

- 使用对象字面量

```js
var obj = {
  property_1: value_1, // property_# 可以是一个标识符...
  2: value_2, // 或一个数字...
  ["property" + 3]: value_3, //  或一个可计算的key名...
  "property n": value_n, // 或一个字符串
};
```

- 使用构造函数
  - 通过创建一个构造函数来定义对象的类型。首字母大写是非常普遍而且很恰当的惯用法。
  - 通过 new 创建对象实例。

```js
function Car(make, model, year) {
  this.make = make;
  this.model = model;
  this.year = year;
}

var mycar = new Car("Eagle", "Talon TSi", 1993);
```

## 使用 Object.create 方法

```js
// Animal properties and method encapsulation
var Animal = {
  type: "Invertebrates", // 属性默认值
  displayType: function() {
    // 用于显示type属性的方法
    console.log(this.type);
  },
};

// 创建一种新的动物——animal1
var animal1 = Object.create(Animal);
```

## 定义 getters 与 setters

一个 [getter](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Functions/get) 是一个获取某个特定属性的值的方法。一个 [setter](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Functions/set) 是一个设定某个属性的值的方法。

```js
var o = {
  a: 7,
  get b() {
    return this.a + 1;
  },
  set c(x) {
    this.a = x / 2;
  },
};

console.log(o.a); // 7
console.log(o.b); // 8
o.c = 50;
console.log(o.a); // 25
```

## 删除属性

你可以用 [delete](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/delete) 操作符删除一个不是继承而来的属性

```js
//Creates a new object, myobj, with two properties, a and b.
var myobj = new Object();
myobj.a = 5;
myobj.b = 12;

//Removes the a property, leaving myobj with only the b property.
delete myobj.a;
```

## 比较对象

在 JavaScript 中 objects 是一种引用类型。两个独立声明的对象永远也不会相等，即使他们有相同的属性，只有在比较一个对象和这个对象的引用时，才会返回 true

```js
// 两个变量, 两个具有同样的属性、但不相同的对象
var fruit = { name: "apple" };
var fruitbear = { name: "apple" };

fruit == fruitbear; // return false
fruit === fruitbear; // return false
```

```js
// 两个变量, 同一个对象
var fruit = { name: "apple" };
var fruitbear = fruit; // 将fruit的对象引用(reference)赋值给 fruitbear
// 也称为将fruitbear“指向”fruit对象
// fruit与fruitbear都指向同样的对象
fruit == fruitbear; // return true
fruit === fruitbear; // return true
```

## 推荐阅读

- [深入理解](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Details_of_the_Object_Model)
- [classes](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Classes)
