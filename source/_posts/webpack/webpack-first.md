---
title: Webpack 打包初体验
date: 2021-09-17 22:44:25
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

# 安装 Webpack

直接全局安装

```bash
npm install webpack webpack-cli -g
```

# 初始化 package.json

`-y` 参数就是 `yes` , 省得一路回车

```bash
npm init -y
```

# 试着打包几个文件

比如按照 `Vue` 框架的目录 , 创建一个 `src` 的子文件夹 , 在 `src` 里面创建一个 `index.js` 和 `data.js` 的文件 , **把 `index.js` 但当作入口文件**

## 文件目录

- project
  - src
    - index.js
    - data.js

## 文件内容

随便写点东西

### data.json

```js
module.exports = {
  job: "Coding every day",
};
```

### index.js

```js
// 引入 data.json
import data from "./date";
console.log("这是 index.js");
console.log(data);
```

# 安装 Webpack 依赖

`-S` 就是 `--save` , 用于生产环境 , `-D` 就是 `--dev` , 用户开发环境

```bash
npm install webpack webpack-cli -S -D
```

# 打包为开发(生产)环境

**不同版本的 `webpack` 打包命还不太一样**

```bash
webpack --entry ./src/index.js --mode development
```

`--entry` 为入口文件 , `-o` 可以指定输出路径, `--mode` 指定打包模式 , `development` 为开发环境模式 , `production` 为生产环境模式 , 也就是上线用的 ( 压缩的 )
