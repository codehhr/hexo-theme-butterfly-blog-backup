---
title: 实现 promiseAll 方法
date: 2021-10-12 19:42:01
updated:
tags:
  - javascript
  - js
  - promiseAll
categories:
  - js
keywords:
description:
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/sunrise.jpg
cover:
comments:
copyright:
copyright_author:
copyright_author_href:
copyright_url:
copyright_info:
---

```js
let p1 = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve("I'm p1");
  }, 1000);
});

let p2 = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve("I'm p2");
  }, 2000);
});

function dealPromiseAll(list) {
  let promiseArr = [];
  return new Promise((resolve, reject) => {
    list.forEach((item, index) => {
      item.then((res) => {
        promiseArr.push(res);
        if (index == list.length - 1) {
          resolve(promiseArr);
        }
      });
    });
  });
}

dealPromiseAll([p1, p2]).then((res) => {
  console.log(res); // [ "I'm p1", "I'm p2" ]
});
```
