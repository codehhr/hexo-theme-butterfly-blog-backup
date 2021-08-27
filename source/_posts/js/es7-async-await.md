---
title: ES7 中的 Async/await
date: 2021-06-25 20:34:37
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/sunrise.jpg
cover:
tags:
  - js
  - javascript
  - ES6
  - async
  - await
categories:
  - js
  - ES7
comments:
---

# Async/await

## 为什么要有 Async/await ?

`Promise` 虽然跳出了异步嵌套的怪圈 , 解决了回调地狱的问题 , 用链式表达更加清晰 , 但是我们也发现如果有大量的异步请求的时候 , 流程复杂的情况下 , 会发现充满了屏幕的 `then` , 看起来非常吃力 , 而 `ES7` 的 `Async/Await` 的出现就是为了解决这种复杂的情况

## Async/await 的基本使用

`async` 用于申明一个 `function` 是异步的 , 返回一个 `promise` 对象 , 而 `await` 可以认为是 `async wait` 的简写 , 等待一个异步方法执行完成 , `async` 必须声明的是一个 `function` , `await` 必须在声明的函数内部使用

```js
// async 用于声明一个 function 是异步的 , 返回一个 Promise 对象
async function demo() {
  setTimeout(() => {
    console.log("我是 async 声明的异步函数");
  }, 3000);

  return "我是 async 声明的异步函数的返回值";
}
demo();
console.log(demo());
demo().then((res) => {
  console.log(res);
});

// 打印结果:
//  Promise {<fulfilled>: "我是 async 声明的异步函数的返回值"}
//  我是 async 声明的异步函数的返回值
//  我是 async 声明的异步函数 ( 调用了三次,打印了三遍 )
```

`await` 可以认为是 `async wait` 的简写 , `await` 必须在声明的函数内部使用 , 不能单独使用
`await` 等待的虽然是 `Promise` 对象 , 但不必写 `.then()` , 直接可以得到返回值

```js
async function demo2() {
  let res = await Promise.resolve(123);
  console.log(res);
}
demo2();
```
