---
title: Webpack 使用配置文件打包
date: 2021-09-19 14:16:55
updated:
tags:
  - Webpack
categories:
  - Webpack
keywords:
description:
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/sunrise.jpg
cover: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/webpack/logo.jpeg
comments:
copyright:
copyright_author:
copyright_author_href:
copyright_url:
copyright_info:
---

# 创建配置文件

创建 `webpack.config.js` 文件 , 一般放在项目根目录下

## 文件内容

```js
let path = require("path");
module.exports = {
  // 入口文件
  entry: "./src/index.js",
  // 输出
  output: {
    // 输出文件名
    filename: "pack.js",
    // 输出路径 (绝对路径)
    // 利用 path 模块获取当前路径
    path: path.resolve(__dirname, "dist"),
  },
  // 打包模式; 开发环境--development, 生产环境--production
  mode: "development",
};
```

## 试着打包

终端下直接输入 `webpack` , 这次不用输入参数

```bash
webpack
```
