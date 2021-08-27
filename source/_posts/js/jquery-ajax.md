---
title: jQuery Ajax 模板
date: 2021-07-01 22:34:13
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/sunrise.jpg
cover:
tags:
  - js
  - javascript
  - jQuery
  - Ajax
categories:
  - js
  - jQuery
comments:
---

```js
$.ajax({
  url: "",
  type: "POST", //GET
  async: true, //或 false,是否异步
  data: {
    name: "llc",
    age: 22,
  },
  timeout: 5000, //超时时间
  dataType: "json", //返回的数据格式：json/xml/html/script/jsonp/text
  beforeSend: function (xhr) {
    console.log(xhr);
    console.log("发送前");
  },
  success: function (data, textStatus, jqXHR) {
    console.log(data);
  },
  error: function (xhr, textStatus) {
    console.log(xhr.responseText);
    console.log(xhr);
    console.log(textStatus);
  },
});
```
