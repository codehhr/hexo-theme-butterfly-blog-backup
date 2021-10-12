---
title: 面试题-击鼓传花 ( 队列 )
date: 2021-10-12 20:07:56
updated:
tags:
  - 数据结构
  - 击鼓传花
  - 队列
categories:
  - 数据结构
keywords: 击鼓传花
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

{% note warning no-icon %}
设有 `N` 个人围成一个圈 , 随机选一个数字 , 从第一个人开始数数 , 数到该数字的人出列 , 直到剩下最后一人 , 即为赢家
{% endnote %}

```js
/* 
  击鼓传花
*/
// 创建队列结构

function Queue() {
  this.queue = [];
  // 队尾添加新元素
  Queue.prototype.add = function (e) {
    this.queue.push(e);
  };
  // 队首删除
  Queue.prototype.del = function () {
    return this.queue.shift();
  };
  // 查看队首元素
  Queue.prototype.head = function () {
    return this.queue[0];
  };
  // 检查队列的长度
  Queue.prototype.size = function () {
    return this.queue.length;
  };
}

// 封装函数实现: 击鼓传花
function passFlower(list, n) {
  // 创建队列结构
  let queue = new Queue();
  // 将所有人加入队列
  list.forEach((item) => {
    queue.add(item);
  });

  // 开始数数,数了的人排到后面,重新依次加入队列,数到 n 的人淘汰,从队列中删除
  // 因为是数到 n 的人淘汰,所以前 n-1 的人 (下标 0<i<n-1) 重新加入队列
  // 重复此操作,直到剩下一人
  while (queue.size() > 1) {
    for (let i = 0; i < n - 1; i++) {
      queue.add(queue.del());
    }
    // 剩下的这个人 (第 n 个人) 被淘汰
    queue.del();
  }

  // 拿到最后剩下的那个人 (赢家) 及下标
  return {
    name: queue.head(),
    index: list.indexOf(queue.head()),
  };
}

let list = ["A", "B", "C", "D", "E"];
console.log(passFlower(list, 3));
```
