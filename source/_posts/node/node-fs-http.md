---
title: Node
date: 2021-07-12 19:57:44
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/sunrise.jpg
cover: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/node/node.jpg
tags:
  - node
  - js
  - javascript
  - fs
  - http
categories:
  - node
comments:
---

# Node

![node](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/node/nodeall.png)

# Node.js 介绍

`Node.js` 不是一门语言 , 不是库或者框架 , `Node.js` 是一个 `JavaScript` 运行时的环境 , `Node.js` 可以解析和执行 `JavaScript` 代码

## 浏览器中 JavaScript 由什么组成

- `EcmaScript` : 基本语法 , `if` , `var` , `function` , `Object` , `Array`
- `DOM`
- `BOM`

## Node.js 中的 JavaScript

- **没有 `BOM` 和 `DOM` , 只有 `EcmaScript`**
- 在 `Node.js` 这个 `JavaScript` 执行环境中为 `JavaScript` 提供了一些服务器级别的操作 `API` , 例如 : 文件读写 , 网络服务构建 , 网络请求与响应等 , 其实 `node` 学习相当于在学习后台服务处理开发 , 只不过后台服务编程使用的是 `JavaScript` 语言而已
- **特性 : 事件驱动 , 非阻塞 `I/O` 模型 ( 简单说就是异步操作 ) , 轻量高效 , 随着学习的深入大家会明白这些特性的**
- `npm` 是世界上最大的 `Node.js` 开源库生态系统 , 用来管理 `JavaScript` 相关的包 , 这样的目的是为了更方便的让开发人员使用它

### 使用 `npm` 安装相关包的命令 ( 以 `jquery` 为例 , 先了解即可 ) :

```bash
npm install jquery
```

**包名后面加 `@` 可指定版本号**

```bash
npm install jquery@2
```

## Node.js 能够做什么

- `Web` 服务器后台
- 命令行工具 , 例如 : `npm` , `git` , `webpack` 等
- 前端工程师接触 `node` 最多的是命令行工具 , 一般很少自己写 , 主要使用别人写好的第三方包

## 小结

- `B/S` 编程模型
  - `Browser - Server`
  - `back-end` ( 后台开发 )
  - 任何服务端技术这种 `BS` 编程模型都一样 , 与语言无关
  - `Node` 只是我们学习 `BS` 编程模型的一个工具而已
- 模块化编程
  **模块化**就是将不同功能的函数封装起来 , 并提供使用接口 , 他们彼此之间互不影响
  - `RequireJS`
  - `SeaJs`
  - 简单的来说 , 以前在我们 `JavaScript` 中只能通过`<script>`标签来引入 `js` 脚本文件 , 在 `node` 中可以更多方式来引入加载 `JavaScript` 脚本
- `Node` 常用 `API`

# Node 起步

## 安装 Node 环境

安装依赖 : `npm install 依赖名字` , `install` 可简写为 `i`
后面加 `@` 可指定版本号 , 比如

```bash
npm i jquery@2.2
```

**参数 :**

- `-g` 表示全局安装
- `--save` 表示生产环境 , 简写是 `-S`
- `-dev` 是开发环境 , 简写是 `-D`

**国内 npm 比较慢 , 可安装淘宝镜像版的 cnpm**

```bash
npm install cnpm --registry=https://registry.npm.taobao.org
```

## Hello World

- 第一步 : 创建编写 `JavaScript` 脚本文件

```js
console.log("Hello World");
```

- 第二步 : 打开终端 , 定位到脚本文件所属目录
- 第三步 : 输入 `node 文件名` 执行对应的文件

```bash
node HelloWorld.js
```

## 读写文件

浏览器中 `JavaScript` 是没有文件操作能力的 , 但是 `Node` 中的 `JavaScript` 具有文件操作的能力 , `Node` 中有一个 `fs` 模块 , `fs` 是 `file-system` 的简写 , 就是文件系统的意思 , 在 `Node` 中如果想要进行文件操作 , 就必须引入 `fs` 这个核心模块

- 引入 `fs` 核心模块

```js
let fs = require("fs");
```

- 用来读取文件的方法

```js
fs.readFile();
```

- 用来写文件的方法

```js
fs.writeFile();
```

## http 服务

服务器是干嘛的 ?

- 提供服务：对数据的服务
- 发请求
- 接收请求
- 处理请求
- 给个响应

我们可以使用 `Node` 非常轻松的构建一个 `Web` 服务器 , 在 `Node` 中 , `专门有个核心模块：http`
思路 :

- 加载 `http` 核心模块

```js
// 1. 加载 http 核心模块
let http = require("http");
```

- 创建一个 `Web` 服务器

```js
// 2.使用 http.createServer() 方法创建一个Web服务器 , 返回一个 Server 实例
let server = http.createServer();
```

- 注册 `request` 请求事件

```js
// 3. 注册 request 请求事件
// 还记得刚才说的 node.js 的特性 : 事件驱动么 , 就是这种用法
// 还记得刚才说的 node.js 的特性 : 回调函数么 , 就是第二个参数的用法

server.on("request", function () {
  console.log("收到客户端的请求了啊");
});
```

- 绑定端口号 , 启动服务器

```js
// 4. 绑定端口号 , 启动服务器
server.listen(3000, function () {
  console.log(
    "服务器启动成功了 , 可以通过浏览器访问http:localhost:3000发请求了"
  );
});
```
