---
title: Nodejs EventEmitter
date: 2021-09-08 22:24:57
updated:
tags:
  - node
  - EventEmitter
categories:
  - node
keywords:
description:
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/sunrise.jpg
cover: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/node/node.jpg
comments:
copyright:
copyright_author:
copyright_author_href:
copyright_url:
copyright_info:
---

{% note info flat %}

**Node.js EventEmitter**
`Node.js` 所有的异步 `I/O` 操作在完成时都会发送一个事件到事件队列
`Node.js` 里面的许多对象都会分发事件 : 一个 `net.Server` 对象会在每次有新连接时触发一个事件 , 一个 `fs.readStream` 对象会在文件被打开的时候触发一个事件 , 所有这些产生事件的对象都是 `events.EventEmitter` 的实例
{% endnote %}

# EventEmitter 类

`events` 模块只提供了一个对象： `events.EventEmitter` , `EventEmitter` 的核心就是事件触发与事件监听器功能的封装

可以通过 `require("events")` 来访问该模块

```js
// 引入 events 模块
let events = require("events");
// 创建 eventEmitter 对象
let eventEmitter = new events.EventEmitter();
```

# EventEmitter 的事件监听和触发

`EventEmitter` 的每个事件由一个`事件名`和`若干个参数`组成 , 事件名是一个自定义的字符串 , 通常表达一定的语义 , 对于每个事件 , `EventEmitter` 支持若干个事件监听器
当事件触发时 , 注册到这个事件的事件监听器被依次调用 , 事件参数作为回调函数参数传递

让我们以下面的例子解释这个过程 :

```js
// 引入 events 模块
let events = require("events");
// 创建 eventEmitter 对象
let eventEmitter = new events.EventEmitter();
eventEmitter.on("someEvent", function (arg1, arg2) {
  console.log("listener1", arg1, arg2);
});
eventEmitter.on("someEvent", function (arg1, arg2) {
  console.log("listener2", arg1, arg2);
});
eventEmitter.emit("someEvent", "参数 1", "参数 2");
```

执行结果 :

```
listener1 参数 1 参数 2
listener2 参数 1 参数 2
```

以上例子中 , `eventEmitter` 为事件 `someEvent` 注册了两个事件监听器 , 然后触发了 `someEvent` 事件
运行结果中可以看到两个事件监听器回调函数被先后调用 , 这就是 `EventEmitter` 最简单的用法
**`EventEmitter` 提供了多个属性 , 如 `on` 和 `emit` , `on` 函数用于绑定事件函数 , `emit` 属性用于触发一个事件**
