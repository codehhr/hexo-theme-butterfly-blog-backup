---
title: ES6 新增用法 ( 五 )
date: 2021-06-25 17:02:58
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/sunrise.jpg
cover:
tags:
  - js
  - javascript
  - ES6
  - Promise
  - then
  - catch
  - resolve
  - reject
categories:
  - js
  - ES6
comments:
---

# ES6 的 Promise 对象

## Promise 设计初衷

如果存在多个请求操作层层依赖的话 , 那么以上的嵌套就有可能不止三层那么少了 , 加上每一层还会有复杂的业务逻辑处理 , 代码可读性也越来越差 , 不直观 , 调试起来也不方便。如果多人开发的时候没有足够的沟通协商 , 大家的代码风格不一致的话 , 更是雪上加霜 , 给后面的维护带来极大的不便 , 既然使用这种回调函数层层嵌套( 又称 : 回调地狱 ) 的形式存在缺点 , `ES6` 想了办法治它 , 所以就有了 Promise 的出现了

## Promise 基本用法

`Promise` 对象是全局对象 , 你也可以理解为一个类 , 创建 `Promise` 实例的时候 , 要有那个 `new` 关键字。参数是一个匿名函数 , 其中有两个参数 : `resolve` ( 解决 ) 和 `reject` ( 拒绝 ) , 两个函数均为方法 , `resolve` 方法用于处理异步操作成功后业务 ; `reject` 方法用于操作异步操作失败后的业务

```js
let promise = new Promise(function (resolve, reject) {
  //
});
```

## Promise 的三种状态

`Promise` 对象有三种状态 :

1. `pending` : 刚刚创建一个 Promise 实例的时候 , 表示初始状态 ;
2. `fulfilled` : resolve 方法调用的时候 , 表示操作成功 ;
3. `rejected` : reject 方法调用的时候 , 表示操作失败 ;
   状态只能从 初始化 -> 成功 或者 初始化 -> 失败 , 不能逆向转换 , 也不能在成功 `fulfilled` 和失败 `rejected` 之间转换

```js
let promise = new Promise(function (resolve, reject) {
  // 实例化后状态 : pending
  if ("操作成功") {
    resolve("resolved"); // resolve 方法调用 , 状态为 : fulfilled
  } else {
    reject("rejected"); // reject 方法调用 , 状态为 : rejected
  }
});
```

## Then( )

`then()` 方法 : 用于绑定处理操作后的处理程序
参数是两个函数 , 第一个用于处理操作成功后的业务 , 第二个用于处理操作异常后的业务

```js
promise.then(
  function (res) {
    // 成功后处理的程序
  },
  function (error) {
    // 失败后处理的程序
  }
);
```

## Catch( )

对于操作异常的程序 , `Promise` 专门提供了一个实例方法来处理 : `catch()` 方法
`catch` 只接受一个参数 , 用于处理操作异常后的业务

```js
promise.catch(function (error) {
  // 失败后处理的程序
});
```

建议将 `then` 方法用于处理操作成功 , `catch` 方法用于处理操作异常 , 也就是

```js
promise
  .then(function (res) {
    // 操作成功的处理程序
  })
  .catch(function (error) {
    // 操作失败的处理程序
  });
```

之所以能够使用链式调用 , 是因为 `then` 方法和 `catch` 方法调用后 , 都会返回 `promise` 对象

**案例 1**

```js
// 用 new 关键字创建一个 Promise 实例
let promise = new Promise(function (resolve, reject) {
  // 假设 condition 的值为 true
  let condition = true;

  if (condition) {
    // 调用操作成功方法
    resolve("操作成功"); // 状态 : pending -> fulfilled
  } else {
    // 调用操作异常方法
    reject("操作异常"); //状态 : pending -> rejected
  }
});

//用then处理操作成功，catch处理操作异常
promise
  .then(function (res) {
    // 操作成功的处理程序
    console.log(res);
  })
  .catch(function (error) {
    // 操作失败的处理程序
    console.log(error);
  });

// 控制台输出 : 操作成功
```

**案例 2 链式调用**

```js
let promise = new Promise(function (resolve, reject) {
  if (true) {
    // 调用操作成功方法
    resolve("操作成功");
  } else {
    // 调用操作异常方法
    reject("操作异常");
  }
});

// 用 then 处理操作成功 , catch 处理操作异常
promise.then(requestA).then(requestB).then(requestC).catch(requestError);

function requestA() {
  console.log("请求A成功");
  return "请求B，下一个就是你了";
}
function requestB(res) {
  console.log("上一步的结果：" + res);
  console.log("请求B成功");
  return "请求C，下一个就是你了";
}
function requestC(res) {
  console.log("上一步的结果：" + res);
  console.log("请求C成功");
}
function requestError() {
  console.log("请求失败");
}
// 打印结果:
//  请求A成功
//  上一步的结果：请求B，下一个就是你了
//  请求B成功
//  上一步的结果：请求C，下一个就是你了
//  请求C成功
```

## Promise.all( )

`Promise.all()` 方法 : 接受一个数组作为参数 , 数组的元素是 `Promise` 实例对象 , 当参数中的实例对象的状态都为 `fulfilled` 时 , `Promise.all()` 才会有返回

```js
// 创建实例 promise1
let promise1 = new Promise(function (resolve) {
  setTimeout(function () {
    resolve("实例1操作成功");
  }, 5000);
});

// 创建实例 promise2
let promise2 = new Promise(function (resolve) {
  setTimeout(function () {
    resolve("实例2操作成功");
  }, 1000);
});

Promise.all([promise1, promise2]).then(function (result) {
  console.log(result);
});
// 打印结果:
// 5秒后打印 : ["实例1操作成功", "实例2操作成功"]
```

这个方法有什么用呢 ? 一般这样的场景 : 我们执行某个操作 , 这个操作需要得到需要多个接口请求回来的数据来支持 , 但是这些接口请求之前互不依赖 , 不需要层层嵌套 , 这种情况下就适合使用 `Promise.all()` 方法 , 因为它会得到所有接口都请求成功了 , 才会进行操作

## Promise.race( )

`Promise.race()` 方法 : 它的参数要求跟 `Promise.all()` 方法一样 , 不同的是 , 它参数中的 `promise` 实例 , 只要有一个状态发生变化 ( 不管是成功 `fulfilled` 还是异常 `rejected` ) , 它就会有返回 , 其他实例中再发生变化 , 它也不管了

```js
// 初始化实例 promise1
let promise1 = new Promise(function (resolve) {
  setTimeout(function () {
    resolve("实例1操作成功");
  }, 4000);
});

// 初始化实例 promise2
let promise2 = new Promise(function (resolve, reject) {
  setTimeout(function () {
    reject("实例2操作失败");
  }, 2000);
});

Promise.race([promise2, promise1])
  .then(function (result) {
    console.log(result);
  })
  .catch(function (error) {
    console.log(error);
  });
// 打印结果:
// 两秒后打印 : 实例2操作失败
```

# The_End
