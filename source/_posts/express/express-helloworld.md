---
title: express 起步 - HelloWorld
date: 2021-10-12 23:56:14
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

# 初始化 package.json

随便找个目录 , 使用 `npm` 初始化 `package.json`

```bash
npm init -y
```

`-y` 这个参数意思是默认所有操作都为 `yes`

# 创建入口文件

先创建一个 `js` 文件 , 比如 `app.js` , 然后简单写一些内容

```js
// 加载 express 模块
const express = require("express");
// 获得一个应用实例
const app = express();

// 添加一个路由, 比如用 get 请求 " / " 响应一个 "HelloWorld"
app.get("/", (req, res) => {
  res.send("HelloWorld");
});

// 设置服务启动端口, 回调函数
app.listen(3000, () => {
  console.log("Server is running at http://localhost:3000");
});
```

# 启动服务

```bash
node app.js
```

此时打开 `http://localhost:3000` 就能看到 `HelloWorld` 了
