---
title: Js 闭包
date: 2021-06-19 08:41:03
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/sunrise.jpg
cover:
tags:
  - javascript
  - js
  - closure
  - 闭包
categories:
  - js
comments:
---

# 1. 定义

闭包就是能够读取其他函数内部变量的函数，由于在 `Javascript` 语言中，只有函数内部的子函数才能读取局部变量，因此可以把闭包简单理解成 " 定义在一个函数内部的函数 "。所以，在本质上，闭包就是将函数内部和函数外部连接起来的一座桥梁。

`JavaScript` 变量可以是局部变量或全局变量。
私有变量可以用到闭包。

**闭包的用途 :**

可以在函数外部读取函数内部成员
让函数内成员始终存活在内存中

**案例 1**

```html
<button>按钮</button>

<script>
  document.querySelector("button").onclick = (function () {
    var num = 0;
    return function () {
      console.log(++num);
    };
  })();
</script>
```

**案例 2**

```js
var name = "this window";
var obj1 = {
  name: "this object",
  getName: function () {
    var name = "this func1";
    console.log(this.name); // this object (obj1调用它，this 指向 obj1)
    console.log(name); // this func1 ( 作用域由内指向外 )
    return function () {
      // 闭包函数
      console.log(name); //this func1 ( 作用域由内指向外 )
      console.log(this.name); // this window ( this 指向 windows )
    };
    console.log(this.name); // retuen 后面的语句不会再执行
    console.log(name); // 同上
  },
};
obj1.getName()();
```

**案例 3**

```js
function getRandom(min, max) {
  var num = Math.floor(Math.random() * (max - min + 1)) + min;
  console.log("num:" + num); // 19行 getRandom 被调用,打印随机数
  // 闭包
  return function () {
    console.log(num);
  };
}
var result = getRandom(1, 10); // getRandom 被调用, 执行13行打印随机数,返回 function(){} 赋给 result
result(); // 相当于 ( function(){console.log(num)} )() , 打印 num , 作用域由内指向外, 打印 12行的生成的随机数
result(); // result 没变 , 同上
```

# The_End
