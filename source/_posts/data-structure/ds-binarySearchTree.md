---
title: Js 封装二叉搜索树
date: 2021-10-19 21:51:50
updated:
tags:
  - 数据结构
  - 二叉树
categories:
  - 数据结构
  - 树结构
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

<!-- {% note info no-icon %}
二叉搜索树的封装
{% endnote %} -->

```js
/*
 * 二叉搜索树的封装
 */

function BinarySearchTree() {
  // 节点类 (每个节点都包含左右两个子节点以及自身的 key)
  function Node(key) {
    this.key = key;
    this.left = null;
    this.right = null;
  }

  //  根节点
  this.root = null;

  // 方法
  // 插入数据
  BinarySearchTree.prototype.insertNode = function (key) {
    console.log(this);
    // 创建一个节点
    let newNode = new Node(key);
    // 先判断根节点是否存在
    if (this.root == null) {
      this.root = newNode;
    } else {
      insert(this.root, newNode);
    }

    // 内部方法: insert
    function insert(currentNode, newNode) {
      // 向左查找
      if (newNode.key < currentNode.key) {
        // 找到 currentNode 的左子节点为 null 时放入
        if (currentNode.left == null) {
          currentNode.left = newNode;
        } else {
          insert(currentNode.left, newNode);
        }
      } else {
        // 向右查找
        if (currentNode.right == null) {
          currentNode.right = newNode;
        } else {
          insert(currentNode.right, newNode);
        }
      }
    }
  };
}
```
