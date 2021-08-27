---
title: Js 数组去重方法总结
date: 2021-06-19 16:12:01
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/sunrise.jpg
cover:
tags:
  - js
  - javascript
  - 数组去重
categories:
  - js
comments:
---

# 利用 indexOf() 方法判断当新数组里原数组某一项不存在时返回 -1 就 push()

```js
let arr = [1, 2, 1, 1, 4, 4, 6, 7, 7, 7, 9, 9, 0, 0, 3, 3, 2];
function A(arr) {
  let newArr = [];
  arr.forEach(function (value) {
    if (newArr.indexOf(value) == -1) {
      newArr.push(value);
    }
  });
  return newArr;
}
// console.log(A(arr));
```

# 利用 indexOf() 方法判断当原数组里某一项返回值与下标相同时就 push

```js
function B(arr) {
  let newArr = [];
  arr.forEach(function (value, index) {
    if (arr.indexOf(value) == index) {
      newArr.push(value);
    }
  });
  return newArr;
}
// console.log(B(arr));
```

# 利用对象属性不重复这一特点

```js
function C(arr) {
  let newArr = [];
  let obj = {};
  arr.forEach(function (value) {
    if (!obj[value]) {
      newArr.push(value);
      obj[value] = true;
    }
  });
  return newArr;
}
// console.log(C(arr));
```

# 利用数组的 includes() 方法

```js
function D(arr) {
  let newArr = [];
  arr.forEach(function (value) {
    if (!newArr.includes(value)) {
      newArr.push(value);
    }
  });
  return newArr;
}
console.log(D(arr));
```

# 利用 Set 结构成员不重复

```js
function deduplication(arr) {
  return Array.from(new Set(arr));
}

console.log(deduplication(arr));
```

# 未完待续 ...
