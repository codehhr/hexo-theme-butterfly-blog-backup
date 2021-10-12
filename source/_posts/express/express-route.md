---
title: express 路由
date: 2021-10-13 00:32:39
updated:
tags:
  - express
categories:
  - express
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

# 基础

路由是指确定应用程序如何响应客户端对特定端点的请求, 该特定端点是 `URL` (路径) 和特定的 `HTTP` 请求方法 (`GET`, `POST` 等)
每个路由可以具有一个或多个处理程序函数, 这些函数在匹配该路由时执行
路由定义采用以下结构 :

```js
app.METHOD(PATH, HANDLER);
```

- `app` 是 `Express` 实例
- `METHOD` 是小写的 `HTTP` 请求方法
- `PATH` 是服务器上的路径
- `HANDLER` 是当路由匹配时执行的功能

# 一些简单实例

**可以用 `postman` 来测试**

## 在根路径响应 `HelloWorld`

```js
app.get("/", (req, res) => {
  res.send("HelloWorld");
});
```

## 在根路径响应 `POST` 请求

```js
app.post("/", (req, res) => {
  res.send("POST request");
});
```

## 响应对 `/user` 路径的 `PUT` 请求

```js
app.put("/user", (req, res) => {
  res.send("PUT request at /user");
});
```

## 响应对 `/user` 路由的 `DELETE` 请求

```js
app.delete("/user", (req, res) => {
  res.send("DELETE request at /user");
});
```
