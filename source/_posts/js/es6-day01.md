---
title: ES6 新增用法 ( 一 )
date: 2021-06-19 19:06:39
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/sunrise.jpg
cover:
tags:
  - js
  - javascript
  - ES6
  - let
  - var
  - const
  - babel
  - 兼容
categories:
  - js
  - ES6
comments:
---

# let 关键字

## let 是块级别作用域

任何一对花括号 ( **这玩意 : { }** ) 中的语句都属于一个块 , 在花括号里面用 `let` 定义的所有变量在花括号外都是不可见的 , 我们称之为块级作用域

**案例 :**

```js
// 使用 var 声明
var list = [];
for (var i = 0; i < 10; i++) {
  list[i] = function () {
    console.log(i);
  };
}
// 遍历完后 i 已变成 10
list[1](); // 10
list[2](); // 10
list[3](); // 10
list[4](); // 10

// 使用 let 声明
var list = [];
for (let i = 0; i < 10; i++) {
  list[i] = function () {
    console.log(i);
  };
}
list[1](); // 1
list[2](); // 2
list[3](); // 3
list[4](); // 4
```

## let 不会变量提升

**案例 :**

```js
// 使用 var 声明
var a = 1;
(function () {
  console.log(a); // undefined
  var a = 2;
});
// 结果是 undefined , 因为 var 使变量提升,相当于 a 定义了,但未赋值

// 使用 let 声明
var a = 1;
(function () {
  console.log(a); // 报错 : a 未定义
  let a = 2;
});
// 结果报错 : a 未定义
// 用let关键字来定义a；这样a在代码块内就不会提升了。
// 那为什么又报错了呢，因为用let声明的变量，在其块级作用域内是封闭的，是不会受到外面的全局变量a影响的，
// 并且要先声明再使用，所以a的值即不是1（因为不受外面的影响）
// 也不是undefined（因为先声明后使用）
// 更不是2，未声明定义就使用，只有报错啦
```

## 同一个块级作用域内不允许重复声明同一个变量

**错误示范 :**

```js
// 错误示范 1
var a = 1;
let a = 2;
// 错误示范 2
let a = 1;
let a = 2;
```

## 函数内不能用 let 重新声明函数的参数

**错误示范 :**

```js
function hello(world) {
  let world = "hello tom"; // 报错 : 用 let 重新声明 world 参数
  console.log(world);
}
hello("hello world");
```

# const 关键字

`const` 是 `constant` ( 常量 ) 的缩写 , `const` 和 `let` 一样 , 也是用来声明变量的 , 但是 `const` 是专门用于声明一个常量的 , 常量的值是不可改变的

**const 的特点**

## 声明的常量不可修改

```js
const person = "张三";
person = "李四"; // 报错,不能修改常量
```

**如果用 `const` 声明的是复杂数据类型的变量,只是变量的指针不可修改,指针指向的堆中的内容可以修改**

```js
// 下面两种情况就可以 , 也不会报错
const arr = [1, 2, 3];
arr[0] = 666;
//
const obj = {
  name: "tom",
  age: 20,
};
obj.name = "jerry";
```

## 只在块级作用域起作用,这点与 let 关键字一样

```js
if (1) {
  const person = "张三";
}
console.log(person); // 错误,在代码快 {} 之外, person 失效
```

## 不存在变量提升,必须先声明后使用,这点也跟 let 关键字一样

```js
if (1) {
  console.log(person); // 错误,使用前未声明
  const person = "张三";
}
```

## 不可重复声明同一个变量,这点跟 let 也一样

```js
var person = "张三";
const person = "李四"; // 错误,声明一个已存在的变量 person
```

## 声明后必须要赋值

```js
const person; // 错误,声明后没有赋值
```

# 快速让浏览器兼容 ES6 的方法

## 安装 node

> ## 官网 https://nodejs.org/
>
> ## 中文网 http://nodejs.cn/

**检测 `node` 是否安装成功,可查看版本号**

```shell
node -v
```

## 安装 babel

**后面的 @5 是版本号,可以不写**

```shell
npm install babel-core@5
```

安装 `babel` 成功后 , 当前目录下的 `/node_modules/babel-core` 里有 `babel` 的浏览器版本 `browser.js` ( 未压缩版 ) 和 `browser.min.js` ( 压缩版 )

## 使用 babel

```html
<script src="brower.js"></script>
<script type="text/babel">
  const name = "张三"; // 测试 : 使用 ES6 新增关键字 const 来声明变量
  console.log(name);
</script>
```

这个时候 IE9 能正常运行 `ES6` 新特性了 , 也就是 `babel` 转换起作用了，把 `const` 转换成 IE9 能执行的代码了

# The_End
