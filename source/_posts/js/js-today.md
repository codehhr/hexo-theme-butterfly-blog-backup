---
title: Js 获取并格式化当前日期
date: 2021-06-15 11:06:04
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/sunrise.jpg
cover:
tags:
  - js
  - javascript
categories:
  - js
aside:
comments:
---

```js
// 返回当前日期
function today() {
  let date = new Date();
  return (
    date.getFullYear() +
    "-" +
    formatTime(date.getMonth() + 1) +
    "-" +
    formatTime(date.getDate()) +
    " " +
    formatTime(date.getHours()) +
    ":" +
    formatTime(date.getMinutes()) +
    ":" +
    formatTime(date.getSeconds())
  );
  function formatTime(t) {
    return t < 10 ? "0" + t : t;
  }
}

console.log(today());
```
