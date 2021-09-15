---
title: TypeScript 环境安装
date: 2021-09-15 23:33:41
updated:
tags:
  - TypeScript
  - ts
  - ts-node
categories:
  - TypeScript
keywords:
description:
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/sunrise.jpg
cover: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/cover/tree.png
comments:
copyright:
copyright_author:
copyright_author_href:
copyright_url:
copyright_info:
---

# TypeScript

`TypeScript` 是 `JavaScript` 的一个超集 , 支持 `ECMAScript 6` 标准 ( [**关于 ES6**](https://codehhr.cn/categories/js/ES6/) )
`TypeScript` 由微软开发的自由和开源的编程语言 , `TypeScript` 设计目标是开发大型应用 , 它可以编译成纯 `JavaScript` , 编译出来的 `JavaScript` 可以运行在任何浏览器上

![TypeScript](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/ts/ts.jpeg)

# TypeScript 安装

## 使用 `npm` 安装

```bash
npm install typescript -g
```

**Linux 用户的话 , `-g` 全局安装会出现 `permission denied` , 意思就是权限不够嘛 , 用 `sudo` 或 `root` 用户就可以了**

## 安装完成后可以使用 `tsc` 命令来执行 `TypeScript` 的相关代码 , 比如查看版本号 :

```bash
tsc -v
```

```bash
Version 4.4.3
```

## 把 ts 文件转换为 js 文件

```bash
tsc index.ts
```

结果会多出一个 `js` 文件 , 然后你可以用 `node index.js` 来执行 , 确实有点麻烦 , 当然有解决办法 , 安装 `ts-node`

## 安装 ts-node

```bash
npm install ts-node -g
```

## 用 ts-node 来执行

就是略慢 , 他得转换一下

```bash
ts-node index.ts
```

# The_End
