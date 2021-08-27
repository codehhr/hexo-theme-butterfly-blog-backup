---
title: Js 中 call apply bind 的用法
date: 2021-06-18 08:53:17
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/sunrise.jpg
cover:
tags:
  - js
  - javascript
  - call
  - apply
  - bind
  - this指向
categories:
  - js
comments:
---

# 改变 this 指向的方法

## (1) call 方法

**1. `call()`方法可以进行普通函数的调用**

**例如**

```js
function fn() {
  console.log("666");
}
fn.call();
```

**2. `call()`方法可以改变 `this` 的指向 , 如果没有参数 , `this` 指向 `window`**
**3. `call()`方法可以改变 `this` 的指向 , 如果有一个参数 , `this`指向该参数**
**4. `call()`方法可以改变 `this` 的指向 , 如果有多个参数 , `this` 指向第一个参数，剩下的是参数列表**

## (2) apply 方法

1. `apply()`方法可以进行普通函数的调用
2. `apply()`方法可以改变 `this` 的指向，如果没有参数 , `this` 指向 window
3. `apply()`方法可以改变 `this` 的指向，如果有一个参数 , `this` 指向该参数
4. `apply()`方法可以改变 `this` 的指向，如果有多个参数，第一个参数是 `null` 或者 `window` , 第二个参数是数组

## (3) bind 方法

bind() 除了返回是函数以外，它的参数和用法跟 `call()` 一样。

**案例**

```js
function Person(name, age) {
  this.name = name;
  this.age = age;
}

// call()
var name = "woman";
var age = 40;
var obj1 = {
  name: "man",
  age: 10,
  say: function () {
    console.log(this.name + " : " + this.age);
  },
};
// obj1.say();
// call() 无参数默认指向 windows
// obj1.say.call();
var obj2 = {
  name: "tom",
  age: 12,
};
// call() 有参数指向第一个参数，后面的是参数列表
obj1.say.call(obj2);

function boy(score, name, age) {
  this.score = score;
  // Person.call(this, name, age);
  Person.apply(this, [name, age]); // apply
  this.study = function () {
    console.log(score, this.name, this.age);
  };
}

var boyA = new boy(100, "www", 10);
boyA.study();

// bind
boyA.study.bind()();
```

## 总结

三者微妙的差距！

`call` 、`bind` 、 `apply` 这三个函数的第一个参数都是 `this` 的指向对象，第二个参数差别就来了：

`call` 的参数是直接放进去的，第二第三第 n 个参数全都用逗号分隔，直接放到后面 `obj.myFun.call(db,'city', ... ,'string'...` )。

`apply` 的所有参数都必须放在一个数组里面传进去 `obj.myFun.apply(db,['成都', ..., 'string' ])`。

`bind` 除了返回是函数以外，它 的参数和 `call` 一样。

当然，三者的参数不限定是 `string` 类型，允许是各种类型，包括函数 、 `object` 等等！

# The_End
