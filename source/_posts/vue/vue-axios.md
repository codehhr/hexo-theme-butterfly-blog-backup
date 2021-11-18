---
title: Axios 的使用
date: 2021-07-21 22:28:53
updated:
tags:
  - Vue
  - axios
categories:
  - Vue
  - Vue 基础
keywords:
description:
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/sunrise.jpg
cover: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/vue/axios.png
comments:
copyright:
copyright_author:
copyright_author_href:
copyright_url:
copyright_info:
---

# 主要是 GET 和 POST 请求

{% tabs axios %}

<!-- tab GET 请求 -->

# GET 请求

```js
axios
  .get("/img?number=4")
  .then((res) => {
    console.log(res);
  })
  .catch((err) => {
    console.log(err);
  });
```

或者

```js
axios
  .get("/img", {
    params: {
      number: 4,
    },
  })
  .then((res) => {
    console.log(res);
  })
  .catch((err) => {
    console.log(err);
  });
```

或者

```js
axios({
  method: "GET",
  url: "https://img",
  // get 请求参数
  params: {
    name: "zs",
    age: 20,
  },
}).then((res) => {
  console.log(res);
});
```

<!-- endtab -->

<!-- tab POST 请求 -->

# POST 请求

传参方式大致用的有 `2` 种

## ① Content-Type = multipart/form-data 和 Content-Type= application/x-www-form-urlencoded

传参格式为 `formData`

```js
let formData = new FormData();
formData.append("type", "free");
formData.append("pageNum", 1);
formData.append("pageSize", 10);
axios
  .post("/course", formData)
  .then((res) => {
    console.log(res);
  })
  .catch((err) => {
    console.log(err);
  });
```


传参格式为 `query` 形式

```js
axios
  .post(
    "/course",
    JSON.stringify({
      type: "free",
      pageNum: 1,
      pageSize: 10,
    })
  )
  .then((res) => {
    console.log("res=>", res);
  })
  .catch((err) => {
    console.log(err);
  });
```

## ② Content-Type= application/json

传参格式为 `raw` ( `JSON` 格式)

```js
axios
  .post("/course", {
    type: "free",
    pageNum: 1,
    pageSize: 10,
  })
  .then((res) => {
    console.log(res);
  });
```

或者

```js
axios
  .post(
    "/course",
    JSON.stringify({
      type: "free",
      pageNum: 1,
      pageSize: 10,
    })
  )
  .then((res) => {
    console.log(res);
  })
  .catch((err) => {
    console.log(err);
  });
```

<!-- endtab -->

{% endtabs %}

# The_End
