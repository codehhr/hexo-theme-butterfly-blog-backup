---
title: Js 面向对象继承
date: 2021-06-16 18:36:07
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/sunrise.jpg
cover:
tags:
  - js
  - javascript
  - 面向对象
  - 继承
categories:
  - js
comments:
---

# 1. 原型继承

```js
// Person
function Person(name, age) {
  this.name = name;
  this.age = age;
}
// Student
function Student(className, score) {
  this.className = className;
  this.score = score;
}
// 在 Person 原型上添加 play 方法
Person.prototype.play = function () {
  console.log("Person_play");
};
// 让 Student 继承 Person
Student.prototype = new Person("nameA", 20);
// 实例化一个 Student 对象
var stu1 = new Student("A", 60);

stu1.play(); // Person_play
// Student 实例化后
// 在 Student 对象原型上添加 play 方法
Student.prototype.play = function () {
  console.log("Student_play");
};
stu1.play(); // Student_play
console.log(stu1.className); // A
console.log(stu1.score); // 60
console.log(stu1.name); // nameA
console.log(stu1.age); // 20

// 通过原型继承，子类本身构造函数中的属性和方法以及子类原型中的属性和方法都可以获取到，并且父类构造函数中的属性和方法以及父类原型中的属性和方法也可以获取到
```

# 2. 构造函数继承

```js
function Person(name, age) {
  this.name = name;
  this.age = age;
}
// call(),this指向第一个参数,后面的依次传参
function Boy(score, name, age) {
  this.score = score;
  Person.call(this, name, age);
  this.study = function () {
    console.log(score);
  };
}

var boyA = new Boy(100, "tom", 10);
console.log(boyA);
```

# 3. 拷贝继承

```js
var obj1 = {
  gender: "男",
  name: "tom",
};

var obj2 = {}; // 创建一个空对象

for (let key in obj1) {
  obj2[key] = obj1[key];
}
obj2.name = "jerry";
console.log(obj2);
console.log(obj2.name);
```

# 未完待续 . . .
