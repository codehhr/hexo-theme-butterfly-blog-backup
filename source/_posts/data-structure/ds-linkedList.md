---
title: 用 Js 封装单链表
date: 2021-10-12 20:28:45
updated:
tags:
  - 数据结构
  - 单链表
categories:
  - 数据结构
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

```js
/*
 单向链表
*/

// 封装链表类
function LinkedList() {
  // 链表头 (头指针)
  this.head = null;
  // 链表长度
  this.length = 0;

  // 封装节点
  function Node(data) {
    this.data = data;
    this.next = null;
  }

  // 追加节点方法
  // data: 追加节点内容
  LinkedList.prototype.appendNode = function (data) {
    // 创建新节点
    let newNode = new Node(data);

    // 判断追加位置
    // 如果链表长度为 0, 头指针指向这个新节点
    if (this.length == 0) {
      this.head = newNode;
    } else {
      // 把头节点当作临时节点, 一直向后找, 直到临时节点的 next 指向 null
      let currentNode = this.head;
      while (currentNode.next) {
        currentNode = currentNode.next;
      }
      // 此时以找到链表尾部, 可把新节点追加在后面
      currentNode.next = newNode;
    }
    this.length++;
    return true;
  };

  // 插入节点方法
  // position: 插入位置
  // data: 插入内容
  LinkedList.prototype.insertNode = function (position, data) {
    // 先排除几种情况
    if (position < 0 || position > this.length) {
      return false;
    } else {
      let newNode = new Node(data);
      // 如果插入位置为 0, 则让新节点指向原来的第一个节点, 也就是原来头指针指向的节点
      if (position == 0) {
        newNode.next = this.head;
        this.head = newNode;
      } else {
        let index = 0;
        // 临时节点, 去匹配 position
        let currentNode = this.head;
        // 因为插入节点需要两个节点操作, previousNode 为前驱, currentNode 为后继
        let previousNode = null;
        // 找到 position 的位置
        while (index++ < position) {
          previousNode = currentNode;
          currentNode = currentNode.next;
        }
        newNode.next = currentNode;
        previousNode.next = newNode;
      }
      this.length++;
      return true;
    }
  };

  // 获取对应节点数据方法
  LinkedList.prototype.getNodeDataByPosition = function (position) {
    // 排除越界访问情况
    if (position < 0 || position > this.length - 1) {
      return null;
    } else {
      // 从头节点开始往后找
      let currentNode = this.head;
      let index = 0;
      while (index++ < position) {
        currentNode = currentNode.next;
      }
      return currentNode.data;
    }
  };

  // indexOf 方法
  LinkedList.prototype.indexOf = function (data) {
    let currentNode = this.head;
    let index = 0;
    while (currentNode) {
      if (currentNode.data == data) {
        return index;
      } else {
        currentNode = currentNode.next;
        index++;
      }
    }
    return -1;
  };

  // update 方法
  LinkedList.prototype.updateNode = function (position, newData) {
    // 越界情况
    if (position < 0 || position > this.length - 1) {
      return false;
    }
    // 先找到要修改的节点的位置
    let currentNode = this.head;
    let index = 0;
    while (index++ < position) {
      currentNode = currentNode.next;
    }
    currentNode.data = newData;
    return true;
  };

  // removeAt 方法
  LinkedList.prototype.removeAt = function (position) {
    if (position < 0 || position > this.length - 1) {
      return false;
    } else {
      if (position == 0) {
        this.head = this.head.next;
      } else {
        let index = 0;
        let previousNode = null;
        let currentNode = this.head;
        while (index++ < position) {
          previousNode = currentNode;
          currentNode = currentNode.next;
        }
        previousNode.next = currentNode.next;
      }
      this.length--;
      return true;
    }
  };

  // remove 方法
  LinkedList.prototype.remove = function (data) {
    return this.removeAt(this.indexOf(data));
  };

  // isEmpty 方法
  LinkedList.prototype.isEmpty = function () {
    return this.length == 0;
  };

  // size 方法
  LinkedList.prototype.size = function () {
    return this.length;
  };
}
```
