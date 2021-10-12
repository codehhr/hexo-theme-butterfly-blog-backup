---
title: 用 Js 封装优先级队列
date: 2021-10-12 20:23:10
updated:
tags:
  - 数据结构
  - 队列
categories:
  - 数据结构
keywords: 优先级队列
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

```js
/*
 优先级队列
*/

// 封装一个类来实现: 优先级队列
function PriorityQueue() {
  // 封装属性
  this.list = [];
  // 封装一个类来承载带优先级的数据
  function Element(data, priority) {
    this.data = data;
    this.priority = priority;
  }

  PriorityQueue.prototype.add = function (data, priority) {
    let element = new Element(data, priority);
    // 判断优先级并将元素加入队列
    // 如果队列长度为 0,直接加入队列
    if (!this.list.length) {
      this.list.push(element);
    } else {
      // 立一个 flag,当 element 加入 list 了就把 added 改为 true
      let added = false;
      // 遍历 list,比较优先级
      for (let i = 0; i < this.list.length; i++) {
        if (element.priority < this.list[i].priority) {
          this.list.splice(i, 0, element);
          added = true;
          break;
        }
      }
      // 如果遍历完 list 都没有找到合适的位置,就直接加到后面
      if (!added) {
        this.list.push(element);
      }
    }
    return this.list;
  };
}

// 创建一个优先级队列实例
let priorityQueue = new PriorityQueue();
// 试着添加元素
priorityQueue.add("A", 10);
priorityQueue.add("B", 40);
priorityQueue.add("C", 20);
priorityQueue.add("D", 100);
priorityQueue.add("E", 60);
console.log(priorityQueue);
```
