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
keywords: js 封装二叉搜索树
description: Js 封装二叉搜索树
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/sunrise.jpg
cover:
comments:
copyright:
copyright_author:
copyright_author_href:
copyright_url:
copyright_info:
---

# 二叉搜索树的封装

{% note info no-icon %}
二叉搜索树的封装
{% endnote %}

```js
/*
 * 二叉搜索树的封装
 */

function BinarySearchTree() {
  // 节点类 (每个节点都包含左右两个子节点以及自身的 key & value )
  function Node(obj) {
    this.key = obj.key;
    this.value = obj.value;
    this.left = null;
    this.right = null;
  }

  //  根节点
  this.root = null;

  // 方法
  // 插入数据
  BinarySearchTree.prototype.insertNode = function (obj) {
    // 创建一个节点
    let newNode = new Node(obj);
    // 先判断根节点是否存在
    if (this.root == null) {
      this.root = newNode;
    } else {
      insert(this.root, newNode);
    }

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

  // 树的遍历
  // 1.先序遍历
  BinarySearchTree.prototype.preorderTraversal = function (handler) {
    console.log("===== 先序遍历 =====");
    preorderTraversalNode(this.root);
    function preorderTraversalNode(currentNode) {
      if (currentNode != null) {
        // 传一个回调 handler, 让 handler 处理当前 (经过的节点) 节点的数据
        handler({ key: currentNode.key, value: currentNode.value });

        // 查找子节点的左子节点
        preorderTraversalNode(currentNode.left);

        // 查找子节点的右子节点
        preorderTraversalNode(currentNode.right);
      }
    }
  };

  // 2.中序遍历
  BinarySearchTree.prototype.inOrderTraversal = function (handler) {
    console.log("===== 中序遍历 =====");
    inOrderTraversalNode(this.root);
    function inOrderTraversalNode(currentNode) {
      if (currentNode != null) {
        // 查找子节点的左子节点
        inOrderTraversalNode(currentNode.left);

        // 让 handler 处理当前 (经过的节点) 节点的数据
        handler({ key: currentNode.key, value: currentNode.value });

        // 查找子节点的右子节点
        inOrderTraversalNode(currentNode.right);
      }
    }
  };

  // 3.后序遍历
  BinarySearchTree.prototype.postorderTraversal = function (handler) {
    console.log("===== 后序遍历 =====");
    postorderTraversalNode(this.root);
    function postorderTraversalNode(currentNode) {
      if (currentNode != null) {
        // 查找子节点的左子节点
        postorderTraversalNode(currentNode.left);

        // 查找子节点的右子节点
        postorderTraversalNode(currentNode.right);

        // 让 handler 处理当前 (经过的节点) 节点的数据
        handler({ key: currentNode.key, value: currentNode.value });
      }
    }
  };

  // 寻找最值
  // 寻找最大值
  BinarySearchTree.prototype.max = function () {
    // 获取根节点
    let currentNode = this.root;
    // 默认 value 值
    let value = null;
    // 一直向右查找,直到节点的右子节点为 null, 当前节点就是最大值
    while (currentNode.right != null) {
      value = currentNode.value;
      currentNode = currentNode.right;
    }
    return { key: currentNode.key, value };
  };

  // 寻找最小值
  BinarySearchTree.prototype.min = function () {
    // 获取根节点
    let currentNode = this.root;
    // 默认 value 值
    let value = null;
    // 一直向左查找,直到节点的左子节点为 null, 当前节点就是最小值
    while (currentNode.left != null) {
      value = currentNode.value;
      currentNode = currentNode.left;
    }
    return { key: currentNode.key, value };
  };
}

// 测试

let binarySearchTree = new BinarySearchTree();
binarySearchTree.insertNode({ key: 11, value: "I'm 11 !" });
binarySearchTree.insertNode({ key: 7, value: "I'm 7 !" });
binarySearchTree.insertNode({ key: 15, value: "I'm 15 !" });
binarySearchTree.insertNode({ key: 5, value: "I'm 5 !" });
binarySearchTree.insertNode({ key: 3, value: "I'm 3 !" });
binarySearchTree.insertNode({ key: 9, value: "I'm 9 !" });
binarySearchTree.insertNode({ key: 8, value: "I'm 8 !" });
binarySearchTree.insertNode({ key: 10, value: "I'm 10 !" });
binarySearchTree.insertNode({ key: 6, value: "I'm 6 !" });
binarySearchTree.insertNode({ key: 13, value: "I'm 13 !" });
binarySearchTree.insertNode({ key: 12, value: "I'm 12 !" });
binarySearchTree.insertNode({ key: 14, value: "I'm 14 !" });
binarySearchTree.insertNode({ key: 20, value: "I'm 20 !" });
binarySearchTree.insertNode({ key: 18, value: "I'm 18 !" });
binarySearchTree.insertNode({ key: 25, value: "I'm 25 !" });
binarySearchTree.preorderTraversal(function (value) {
  console.log(value);
});
binarySearchTree.inOrderTraversal(function (value) {
  console.log(value);
});
binarySearchTree.postorderTraversal(function (value) {
  console.log(value);
});

console.log(binarySearchTree.max());
console.log(binarySearchTree.min());
```
