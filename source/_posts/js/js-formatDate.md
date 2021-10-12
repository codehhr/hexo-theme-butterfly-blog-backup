---
title: 日期格式化
date: 2021-10-12 20:44:17
updated:
tags:
  - formatDate
  - js
categories:
  - js
keywords: 日期格式化
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

# 一般用在 Vue 里的 filter 上

```js
function formatDate(d, format) {
  var year = d.getFullYear(),
    month = d.getMonth() + 1,
    date = d.getDate(),
    hour = d.getHours(),
    minute = d.getMinutes(),
    second = d.getSeconds(),
    day = d.getDay(),
    week = ["日", "一", "二", "三", "四", "五", "六"];
  return format
    .replace(/yyyy/, year)
    .replace(/yy/, formatNum(year % 100))
    .replace(/MM/, formatNum(month))
    .replace(/M/, month)
    .replace(/dd/, formatNum(date))
    .replace(/d/, date)
    .replace(/HH/, formatNum(hour))
    .replace(/H/, hour)
    .replace(/hh/, formatNum(hour % 12))
    .replace(/h/, hour % 12)
    .replace(/mm/, formatNum(minute))
    .replace(/m/, minute)
    .replace(/ss/, formatNum(second))
    .replace(/s/, second)
    .replace(/w/, week[day]);
}

function formatNum(n) {
  return n < 10 ? "0" + +n : n;
}
```
