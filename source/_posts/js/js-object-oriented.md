---
title: Js 面向对象
date: 2021-06-15 20:18:18
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/sunrise.jpg
cover:
aside:
tags:
  - js
  - javascript
  - 面向对象
categories:
  - js
comments:
---

# 1. JavaScript 面向对象的介绍

## (1) 什么是对象

Everything is object （万物皆对象）
对象是一个容器，封装了属性（ `property` ）和方法（ `method` ）。

ECMAScript-262 把对象定义为：无序属性的集合，其属性可以包含基本值、对象或者函数。严格来讲，这就相当于说对象是一组没有特定顺序的值。对象的每个属性或方法都有一个名字，而每个名字都映射到一个值。

## (2) 什么是面向对象

面向对象是对过程式代码的一种高度封装，目的在于提高代码的开发效率和可维护性。

面向对象编程 —— Object Oriented Programming，简称 OOP ，是一种编程开发思想。它将真实世界各种复杂的关系，抽象为一个个对象，然后由对象之间的分工与合作，完成对真实世界的模拟。

## (3) 面向对象的特征

**封装性**

**继承性**

**多态性**

# 2. 基本类型与引用类型的区别

## (1) 基本类型

**占用空间固定，保存在栈中**（当一个方法执行时，每个方法都会建立自己的内存栈，在这个方法内定义的变量将会逐个放入这块栈内存里，随着方法的执行结束，这个方法的内存栈也将自然销毁了。因此，所有在方法中定义的变量都是放在栈内存中的；栈中存储的是基础变量以及一些对象的引用变量，基础变量的值是存储在栈中，而引用变量存储在栈中的是指向堆中的数组或者对象的地址，这就是为何修改引用类型总会影响到其他指向这个地址的引用变量。
保存与复制的是值本身，使用 `typeof` 检测数据的类型，基本类型数据是值类型

## (2) 引用类型

**占用空间不固定，保存在堆中**（当我们在程序中创建一个对象时，这个对象将被保存到运行时数据区中，以便反复利用（因为对象的创建成本通常较大），这个运行时数据区就是堆内存。堆内存中的对象不会随方法的结束而销毁，即使方法结束后，这个对象还可能被另一个引用变量所引用（方法的参数传递时很常见），则这个对象依然不会被销毁，只有当一个对象没有任何引用变量引用它时，系统的垃圾回收机制才会在核实的时候回收它

**栈**：自动分配内存空间，系统自动释放，里面存放的是基本类型的值和引用类型的地址

**堆**：动态分配的内存，大小不定，也不会自动释放。里面存放引用类型的值。

# 3. 创建对象的四种方法

## 1. 对象字面量

```js
var obj = {
  name: "zs",
  age: 18,
  sex: true
  fun=function(){
    console.log("fun")
  }
};
```

## 2. new Object()创建对象

```js
var person = new Object();
person.name = "lisi";
person.age = 35;
person.job = "codeman";
person.say = function () {
  console.log("Hello");
};
```

## 3. 工厂函数创建对象

```js
function createPerson(name, age, job) {
  var person = new Object();
  person.name = name;
  person.age = age;
  person.job = job;
  person.say = function () {
    console.log("Hello");
  };
  return person;
}
var p1 = createPerson("张三", 22, "actor");
```

## 4. 自定义构造函数

```js
function Person(name, age, job) {
  this.name = name;
  this.age = age;
  this.job = job;
  this.say = function () {
    console.log("Hello");
  };
}
var p1 = new Person("张三", 22, "actor");
```

# 4. 构造函数和实例对象的关系

创建一个实例对象，须使用 new 操作符。以这种方式调用构造函数会经历以下 4 个步骤：

## (1) 解析构造函数代码的执行

1. 创建一个新对象
2. 将构造函数的作用域赋给新对象（因此 `this` 就指向了这个新对象）
3. 执行构造函数中的代码
4. 返回新对象

## (2) constructor 属性

可以通过实例的 `constructor` 属性判断实例和构造函数之间的关系  
构造函数实例化对象的 `constructor` 属性指向的是构造函数本身

```js
console.log(obj1.constructor == Object);
```

## (3) instanceof 关键字

如果要检测对象的类型，还是使用 `instanceof` 操作符更可靠一些,返回 `true` 为对象

```js
console.log(obj1 instanceof Object);
```

## 总结 :

构造函数是根据具体的事物抽象出来的抽象模板  
实例对象是根据抽象的构造函数模板得到的具体实例对象  
每一个实例对象都具有一个 `constructor` 属性，指向创建该实例的构造函数

# 5. 构造函数的问题

## 内存浪费

对于每一个实例对象，如果我们在每一个实例对象的内部创建一个属性，值为函数。假如创建两个对象，属性名也许一致,看似都是一模一样的内容，但是其实每一次生成一个实例，都会多占用一些内存，如果实例对象很多，会造成极大的内存浪费。

# 6. 原型

上述问题的更好的解决方案： `prototype`

`Javascript` 规定，每一个构造函数都有一个 `prototype` 属性，指向另一个对象。这个对象的所有属性和方法，都会被构造函数的实例继承。
这也就意味着，我们可以把所有对象实例需要共享的属性和方法直接定义在 `prototype` 对象上。

```js
function Person(name, age) {
  this.name = name;
  this.age = age;
}
Person.prototype.say = function () {
  console.log("Hello");
};

var p1 = new Person("Tom", 20);
var p2 = new Person("Jerry", 20);

console.log(p1.say === p2.say); // true
```

**构造函数、实例、原型三者之间的关系**

![js-prototype](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/js/jsprototype.png)

任何函数都具有一个 `prototype` 属性，该属性是一个对象

构造函数的 `prototype` 对象默认都有一个 `constructor` 属性，指向 `prototype` 对象所在函数

通过构造函数得到的实例对象内部会包含一个指向构造函数的 `prototype` 对象的指针 \_\_proto\_\_
\_\_proto\_\_ 是非标准属性

**总结 :**

1. 任何函数都具有一个 `prototype` 属性，该属性是一个对象
2. 构造函数有一个 `protoType` 属性，它本身是一个对象，我们称之为原型
3. 构造函数的 `protoType` 原型对象的属性和方法，都可以被构造函数实例化的对象所继承
4. 构造函数的 `protoType` 原型对象有个 `constructor` 属性，指向的是当前原型对象所在的构造函数
5. 实例对象有\_\_proto\_\_属性，它是一个指针，指向的是构造函数的的原型 `prototype`
6. 实例对象都具有一个 `constructor` 属性，指向创建该实例的构造函数

# 7. 把局部变量变为全局变量

```js
(function () {
  var a = 10;
  window.a = a;
})(window);

console.log(a);
```

# 未完待续 ...
