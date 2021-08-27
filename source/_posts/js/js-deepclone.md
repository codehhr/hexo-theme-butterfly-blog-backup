---
title: Js 实现递归深拷贝
date: 2021-06-19 10:09:41
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/sunrise.jpg
cover:
tags:
  - js
  - deepClone
  - 递归
  - 深拷贝
categories:
  - js
comments:
---

# 利用循环和递归的方式实现深拷贝

```js
function deepClone(obj, newObj) {
  var newObj = newObj || {};
  for (let key in obj) {
    if (typeof obj[key] == "object") {
      newObj[key] = obj[key].constructor === Array ? [] : {};
      deepClone(obj[key], newObj[key]);
    } else {
      newObj[key] = obj[key];
    }
  }
  return newObj;
}
```
