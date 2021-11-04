---
title: Js 封装双向链表
date: 2021-11-01 19:30:25
updated:
tags:
  - 数据结构
  - 双向链表
categories:
  - 数据结构
  - 链表结构
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

# 总代码

{% hideToggle %}

```js
/*
 * 双向链表
 * */

function DoublyLinkedList() {
  this.head = null;
  this.tail = null;
  this.length = 0;

  // 节点类
  function Node(data) {
    this.prev = null;
    this.next = null;
    this.data = data;
  }

  // 追加节点
  DoublyLinkedList.prototype.append = function (data) {
    let newNode = new Node(data);
    if (this.length == 0) {
      this.head = newNode;
      this.tail = newNode;
    } else {
      newNode.prev = this.tail;
      this.tail.next = newNode;
      this.tail = newNode;
    }
    this.length += 1;
  };

  // 插入节点
  DoublyLinkedList.prototype.insert = function (position, data) {
    let newNode = new Node(data);
    // 先判断插入位置是否合法
    if (position < 0) {
      console.log("Illegal position !");
      return false;
    } else {
      if (this.length == 0) {
        this.head = newNode;
        this.tail = newNode;
      } else {
        if (position == 0) {
          newNode.next = this.head;
          this.head.prev = newNode;
          this.head = newNode;
        } else if (position == this.length) {
          // this.append(data);
          newNode.prev = this.tail;
          this.tail.next = newNode;
          this.tail = newNode;
        } else if (position > this.length) {
          this.append(data);
        } else {
          // 先找到要插入的位置
          // 插入位置的节点 (原后继节点)
          let currentNode = this.head;
          // 插入位置的前一个节点 (前驱节点)
          let previousNode = null;
          // 去匹配 position
          let index = 0;

          while (index++ < position) {
            previousNode = currentNode;
            currentNode = currentNode.next;
          }
          // 已找到要插入的位置
          newNode.next = currentNode;
          newNode.prev = previousNode;
          currentNode.prev = newNode;
          previousNode.next = newNode;
        }
      }
      this.length += 1;
      return true;
    }
  };

  // 打印双链表
  DoublyLinkedList.prototype.print = function () {
    let arr = [];
    let currentNode = this.head;
    arr.push(currentNode.data);
    while (currentNode.next) {
      arr.push(currentNode.next.data);
      currentNode = currentNode.next;
    }
    return arr;
  };

  // 获取指定位置节点数据
  // 可以根据链表长度决定从前开始找还是从后开始找, 这样效率高一些, 此处略, 默认从前面开始找
  DoublyLinkedList.prototype.get = function (position) {
    // 排除越界情况
    if (position < 0 || position >= this.length) {
      console.log("Illegal position !");
      return false;
    } else {
      let index = 0;
      let currentNode = this.head;
      while (index++ < position) {
        currentNode = currentNode.next;
      }
      return currentNode.data;
    }
  };
}

// 测试
let doublyLinkedList = new DoublyLinkedList();

// append
doublyLinkedList.append(4);
doublyLinkedList.append(5);
doublyLinkedList.append(6);
doublyLinkedList.append(7);
doublyLinkedList.append(8);
doublyLinkedList.append(9);
doublyLinkedList.append(10);
doublyLinkedList.append(11);
doublyLinkedList.append(12);

// print
// insert
console.log(doublyLinkedList.print());
console.log(doublyLinkedList.insert(999, 999));
console.log(doublyLinkedList.print());

// get
console.log(doublyLinkedList.get(999));
```

{% endhideToggle %}

# 创建双向链表类

```js
function DoublyLinkedList() {
  this.head = null;
  this.tail = null;
  this.length = 0;
}
```

# 创建节点类, 用于承载每个节点

```js
// 节点类
function Node(data) {
  this.prev = null;
  this.next = null;
  this.data = data;
}
```

# 封装一些方法

## 追加节点方法

```js
// 追加节点
DoublyLinkedList.prototype.append = function (data) {
  let newNode = new Node(data);
  if (this.length == 0) {
    this.head = newNode;
    this.tail = newNode;
  } else {
    newNode.prev = this.tail;
    this.tail.next = newNode;
    this.tail = newNode;
  }
  this.length += 1;
};
```

## 插入节点方法

```js
// 插入节点
DoublyLinkedList.prototype.insert = function (position, data) {
  let newNode = new Node(data);
  // 先判断插入位置是否合法
  if (position < 0) {
    console.log("Illegal position !");
    return false;
  } else {
    if (this.length == 0) {
      this.head = newNode;
      this.tail = newNode;
    } else {
      if (position == 0) {
        newNode.next = this.head;
        this.head.prev = newNode;
        this.head = newNode;
      } else if (position == this.length) {
        // this.append(data);
        newNode.prev = this.tail;
        this.tail.next = newNode;
        this.tail = newNode;
      } else if (position > this.length) {
        this.append(data);
      } else {
        // 先找到要插入的位置
        // 插入位置的节点 (原后继节点)
        let currentNode = this.head;
        // 插入位置的前一个节点 (前驱节点)
        let previousNode = null;
        // 去匹配 position
        let index = 0;

        while (index++ < position) {
          previousNode = currentNode;
          currentNode = currentNode.next;
        }
        // 已找到要插入的位置
        newNode.next = currentNode;
        newNode.prev = previousNode;
        currentNode.prev = newNode;
        previousNode.next = newNode;
      }
    }
    this.length += 1;
    return true;
  }
};
```

## 打印双链表

```js
// 打印双链表
DoublyLinkedList.prototype.print = function () {
  let arr = [];
  let currentNode = this.head;
  arr.push(currentNode.data);
  while (currentNode.next) {
    arr.push(currentNode.next.data);
    currentNode = currentNode.next;
  }
  return arr;
};
```

## 获取指定位置节点数据

```js
// 获取指定位置节点数据
// 可以根据链表长度决定从前开始找还是从后开始找, 这样效率高一些, 此处略, 默认从前面开始找
DoublyLinkedList.prototype.get = function (position) {
  // 排除越界情况
  if (position < 0 || position >= this.length) {
    console.log("Illegal position !");
    return false;
  } else {
    let index = 0;
    let currentNode = this.head;
    while (index++ < position) {
      currentNode = currentNode.next;
    }
    return currentNode.data;
  }
};
```

# 未完待续...
