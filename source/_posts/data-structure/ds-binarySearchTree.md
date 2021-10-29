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

{% note info no-icon %}

# 二叉搜索树的封装

{% endnote %}

# 完整代码

{% hideToggle code %}

```js
/*
 * 二叉搜索树的封装
 *
 */

function BinarySearchTree() {
  // 节点类 (每个节点都包含左右两个子节点以及自身的 key & value )
  function Node(obj = {}) {
    this.key = obj.key;
    this.value = obj.value;
    this.left = null;
    this.right = null;
  }

  //  根节点
  this.root = null;

  // 方法
  // 插入数据
  BinarySearchTree.prototype.insert = function (obj) {
    // 创建一个节点
    let newNode = new Node(obj);
    // 先判断根节点是否存在
    if (this.root == null) {
      this.root = newNode;
    } else {
      insertNode(this.root, newNode);
    }

    function insertNode(currentNode, newNode) {
      // 向左查找
      if (newNode.key < currentNode.key) {
        // 找到 currentNode 的左子节点为 null 时放入
        if (currentNode.left == null) {
          currentNode.left = newNode;
        } else {
          insertNode(currentNode.left, newNode);
        }
      } else {
        // 向右查找
        if (currentNode.right == null) {
          currentNode.right = newNode;
        } else {
          insertNode(currentNode.right, newNode);
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
      } else {
        return null;
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
      } else {
        return null;
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
      } else {
        return null;
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

  // // 层序遍历方法 1
  // BinarySearchTree.prototype.levelTraversal = function () {
  //   let currentNode = this.root;
  //   let result = [];
  //   levelTraversalNode(currentNode, 0);
  //   function levelTraversalNode(currentNode, level) {
  //     if (currentNode != null) {
  //       if (!result[level]) {
  //         result[level] = [];
  //       }
  //       result[level].push(currentNode.value);
  //       if (currentNode.left) {
  //         levelTraversalNode(currentNode.left, level + 1);
  //       }
  //       if (currentNode.right) {
  //         levelTraversalNode(currentNode.right, level + 1);
  //       }
  //     }
  //   }
  //   return result;
  // };

  // 层序遍历方法 2
  BinarySearchTree.prototype.levelTraversal = function levelTraversal() {
    let result = []; // 最后输出的多维数组
    let length = 0;
    let item = new Node();
    if (!this.root) {
      return result;
    } else {
      let layer = []; // 临时数组, 存放某一层的节点
      layer.push(this.root); // 把根节点作为第一层放进数组
      while (layer.length != 0) {
        result.push([]); // 添加新的一层
        length = layer.length; // 下面 shift 会改变 layer 数组长度, 所以先保存下
        for (let i = 0; i < length; i++) {
          item = layer.shift(); // 层虚遍历从左到右
          result[result.length - 1].push(item.key); // 把这个节点的值, 添加到当前层的数组里面
          // 将下一层的节点加入 layer
          if (item.left) {
            layer.push(item.left);
          }
          if (item.right) {
            layer.push(item.right);
          }
        }
      }
    }
    return result;
  };

  // 搜索 key 值
  // BinarySearchTree.prototype.search = function (key) {
  //   return searchNode(this.root, key);
  //   function searchNode(currentNode, key) {
  //     if (currentNode == null) {
  //       return false;
  //     } else {
  //       if (key < currentNode.key) {
  //         return searchNode(currentNode.left, key);
  //       } else if (key > currentNode.key) {
  //         return searchNode(currentNode.right, key);
  //       } else {
  //         return true;
  //       }
  //     }
  //   }
  // };

  // 搜索 key 值 ( 非递归式 )
  BinarySearchTree.prototype.search = function (key) {
    let currentNode = this.root;
    while (currentNode != null) {
      if (key < currentNode.key) {
        currentNode = currentNode.left;
      } else if (key > currentNode.key) {
        currentNode = currentNode.right;
      } else {
        return true;
      }
    }
    return false;
  };

  // 删除节点
  BinarySearchTree.prototype.remove = function (key) {
    if (!key) return false;
    // 先寻找要删除的节点
    // 涉及到当前节点和父节点, 以及具体关系 ( 是左子节点还是右子节点 )
    let parentNode = this.root;
    let currentNode = this.root;
    let isLeftChild = true;

    while (key != currentNode.key) {
      parentNode = currentNode;
      if (key < currentNode.key) {
        isLeftChild = true;
        currentNode = currentNode.left;
      } else {
        isLeftChild = false;
        currentNode = currentNode.right;
      }
      // 没找到要删除的节点
      if (!currentNode) {
        return false;
      }
    }

    // while 循环结束, 已找到要删除的节点, 下面分几种情况
    // 1. 要删除的节点是叶子节点
    if (currentNode.left == null && currentNode.right == null) {
      if (currentNode == this.root) {
        this.root = null;
      } else {
        // 判断当前节点和父节点的关系
        if (isLeftChild) {
          parentNode.left = null;
        } else {
          parentNode.right = null;
        }
      }
    }
    // 2. 要删除的节点只有一个子节点 ( 只有左子节点 )
    else if (!currentNode.right) {
      if (currentNode == this.root) {
        this.root == currentNode.left;
      }
      // 判断当前节点和父节点的关系
      else if (isLeftChild) {
        parentNode.left = currentNode.left;
      } else {
        parentNode.right = currentNode.left;
      }
    }
    // 3. 要删除的节点只有一个子节点 ( 只有右子节点 )
    else if (!currentNode.left) {
      if (currentNode == this.root) {
        this.root == currentNode.left;
      }
      // 判断当前节点和父节点的关系
      else if (isLeftChild) {
        parentNode.left = currentNode.right;
      } else {
        parentNode.right = currentNode.right;
      }
    }
    // 4. 要删除的节点有两个子节点
    else {
      // 通过找规律发现, 该节点即在左子树中找最大的值 或者 在右子树中找最小的值
      // By the way, it's fucking complicated !
      // 有两种方案, 这里只展示向删除节点的左子树方向查找

      if (currentNode == this.root) this.root = null;

      let candidateNode = currentNode.left; // 初始候选替补节点
      let candidateParentNode = currentNode.left; // 初始候选替补节点的父节点
      // 寻找合适的节点
      while (candidateNode.right) {
        candidateParentNode = candidateNode;
        candidateNode = candidateNode.right;
      }
      // 如果候选节点没有右子树, 则当前节点就是最终替补节点
      if (candidateNode == candidateParentNode) {
        candidateNode.right = currentNode.right;
        if (isLeftChild) {
          parentNode.left = candidateNode;
        } else {
          parentNode.right = candidateNode;
        }
      }
      // 如果候选节点有右子树
      else {
        // 再判断是否有左子树 (隔代)
        if (candidateNode.left) {
          candidateParentNode.right = candidateNode.left;
        } else {
          candidateParentNode.right = null;
          candidateNode.left = currentNode.left;
          candidateNode.right = currentNode.right;
          if (isLeftChild) {
            parentNode.left = candidateNode;
          } else {
            parentNode.right = candidateNode;
          }
        }
      }
    }
    return true;
  };
}

/*
 * 测试
 *
 * */

let binarySearchTree = new BinarySearchTree();
binarySearchTree.insert({ key: 11, value: "I'm 11 !" });
binarySearchTree.insert({ key: 7, value: "I'm 7 !" });
binarySearchTree.insert({ key: 15, value: "I'm 15 !" });
binarySearchTree.insert({ key: 5, value: "I'm 5 !" });
binarySearchTree.insert({ key: 3, value: "I'm 3 !" });
binarySearchTree.insert({ key: 9, value: "I'm 9 !" });
binarySearchTree.insert({ key: 8, value: "I'm 8 !" });
binarySearchTree.insert({ key: 10, value: "I'm 10 !" });
binarySearchTree.insert({ key: 13, value: "I'm 13 !" });
binarySearchTree.insert({ key: 12, value: "I'm 12 !" });
binarySearchTree.insert({ key: 14, value: "I'm 14 !" });
binarySearchTree.insert({ key: 20, value: "I'm 20 !" });
binarySearchTree.insert({ key: 18, value: "I'm 18 !" });
binarySearchTree.insert({ key: 25, value: "I'm 25 !" });
binarySearchTree.insert({ key: 19, value: "I'm 19 !" });
//
//                            11
//                  7                     15
//            5         9             13      20
//        3           8  10         12 14   18   25
//                                           19
//

// 先序
// binarySearchTree.preorderTraversal(function (value) {
//   console.log(value);
// });
// 中序
// binarySearchTree.inOrderTraversal(function (value) {
//   console.log(value);
// });
// 后序
// binarySearchTree.postorderTraversal(function (value) {
//   console.log(value);
// });
// 层序
// console.log(binarySearchTree.levelTraversal());
// 最大值
// console.log(binarySearchTree.max());
// 最小值
// console.log(binarySearchTree.min());
// 搜索 key
// console.log(binarySearchTree.search(11));
// console.log(binarySearchTree.search(7));
// console.log(binarySearchTree.search(15));
// console.log(binarySearchTree.search(5));
// console.log(binarySearchTree.search(3));
// console.log(binarySearchTree.search(9));
// console.log(binarySearchTree.search(8));
// console.log(binarySearchTree.search(10));
// console.log(binarySearchTree.search(6));
// console.log(binarySearchTree.search(13));
// console.log(binarySearchTree.search(12));
// console.log(binarySearchTree.search(14));
// console.log(binarySearchTree.search(20));
// console.log(binarySearchTree.search(18));
// console.log(binarySearchTree.search(25));
console.log(binarySearchTree.levelTraversal());
console.log(binarySearchTree.remove(11));
console.log(binarySearchTree.levelTraversal());
```

{% endhideToggle %}

---

# 创建二叉搜索树这个类

**顺便定义根节点, 先让它为空**

```js
function BinarySearchTree() {
  this.root = null;
}
```

# 创建节点类, 用于承载每个节点

```js
function Node(obj = {}) {
  this.key = obj.key;
  this.value = obj.value;
  this.left = null;
  this.right = null;
}
```

# 封装二叉搜索树的一些方法

## 插入数据

```js
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
```

## 先序遍历

```js
// 先序遍历
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
    } else {
      return null;
    }
  }
};
```

## 中序遍历

```js
// 中序遍历
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
    } else {
      return null;
    }
  }
};
```

## 后序遍历

```js
// 后序遍历
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
    } else {
      return null;
    }
  }
};
```

## 寻找最大值

```js
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
```

## 寻找最小值

```js
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
```

## 层序遍历

### 层序遍历方法 1

```js
// 层序遍历方法 1
BinarySearchTree.prototype.levelTraversal = function () {
  let currentNode = this.root;
  let result = [];
  levelTraversalNode(currentNode, 0);
  function levelTraversalNode(currentNode, level) {
    if (currentNode != null) {
      if (!result[level]) {
        result[level] = [];
      }
      result[level].push(currentNode.value);
      if (currentNode.left) {
        levelTraversalNode(currentNode.left, level + 1);
      }
      if (currentNode.right) {
        levelTraversalNode(currentNode.right, level + 1);
      }
    }
  }
  return result;
};
```

### 层序遍历方法 2

```js
BinarySearchTree.prototype.levelTraversal = function levelTraversal() {
  let result = []; // 最后输出的结构 (多维数组)
  let length = 0; // layer 数组长度; 声明在外面是为了尽量不在 while 内部使用 let
  let item = {}; // layer 数组里的每一个节点; 声明在外面是为了尽量不在 while 内部使用 let
  if (!this.root) {
    return result;
  } else {
    let layer = []; // 临时数组, 存放某一层的节点
    layer.push(this.root); // 把根节点作为第一层放进数组
    while (layer.length != 0) {
      result.push([]); // 添加新的一层
      length = layer.length; // 下面 shift() 会改变 layer 数组长度, 所以先保存下来
      for (let i = 0; i < length; i++) {
        item = layer.shift(); // 层虚遍历从左到右
        result[result.length - 1].push(item.key); // 把这个节点的值, 添加到当前层的数组里面
        // 将下一层的节点加入 layer
        if (item.left) {
          layer.push(item.left);
        }
        if (item.right) {
          layer.push(item.right);
        }
      }
    }
  }
  return result;
};
```

## 搜索

### 搜索 ( 递归式 )

```js
// 搜索 key 值
BinarySearchTree.prototype.search = function (key) {
  return searchNode(this.root, key);
  function searchNode(currentNode, key) {
    if (currentNode == null) {
      return false;
    } else {
      if (key < currentNode.key) {
        return searchNode(currentNode.left, key);
      } else if (key > currentNode.key) {
        return searchNode(currentNode.right, key);
      } else {
        return true;
      }
    }
  }
};
```

### 搜索 ( 非递归式 )

```js
// 搜索 key 值 ( 非递归式 )
BinarySearchTree.prototype.search = function (key) {
  let currentNode = this.root;
  while (currentNode != null) {
    if (key < currentNode.key) {
      currentNode = currentNode.left;
    } else if (key > currentNode.key) {
      currentNode = currentNode.right;
    } else {
      return true;
    }
  }
  return false;
};
```

## 删除节点

```js
// 删除节点
BinarySearchTree.prototype.remove = function (key) {
  if (!key) return false;
  // 先寻找要删除的节点
  // 涉及到当前节点和父节点, 以及具体关系 ( 是左子节点还是右子节点 )
  let parentNode = this.root;
  let currentNode = this.root;
  let isLeftChild = true;

  while (key != currentNode.key) {
    parentNode = currentNode;
    if (key < currentNode.key) {
      isLeftChild = true;
      currentNode = currentNode.left;
    } else {
      isLeftChild = false;
      currentNode = currentNode.right;
    }
    // 没找到要删除的节点
    if (!currentNode) {
      return false;
    }
  }

  // while 循环结束, 已找到要删除的节点, 下面分几种情况
  // 1. 要删除的节点是叶子节点
  if (currentNode.left == null && currentNode.right == null) {
    if (currentNode == this.root) {
      this.root = null;
    } else {
      // 判断当前节点和父节点的关系
      if (isLeftChild) {
        parentNode.left = null;
      } else {
        parentNode.right = null;
      }
    }
  }
  // 2. 要删除的节点只有一个子节点 ( 只有左子节点 )
  else if (!currentNode.right) {
    if (currentNode == this.root) {
      this.root == currentNode.left;
    }
    // 判断当前节点和父节点的关系
    else if (isLeftChild) {
      parentNode.left = currentNode.left;
    } else {
      parentNode.right = currentNode.left;
    }
  }
  // 3. 要删除的节点只有一个子节点 ( 只有右子节点 )
  else if (!currentNode.left) {
    if (currentNode == this.root) {
      this.root == currentNode.left;
    }
    // 判断当前节点和父节点的关系
    else if (isLeftChild) {
      parentNode.left = currentNode.right;
    } else {
      parentNode.right = currentNode.right;
    }
  }
  // 4. 要删除的节点有两个子节点
  else {
    // 通过找规律发现, 该节点即在左子树中找最大的值 或者 在右子树中找最小的值
    // By the way, it's fucking complicated !
    // 有两种方案, 这里只展示向删除节点的左子树方向查找

    if (currentNode == this.root) this.root = null;

    let candidateNode = currentNode.left; // 初始候选替补节点
    let candidateParentNode = currentNode.left; // 初始候选替补节点的父节点
    // 寻找合适的节点
    while (candidateNode.right) {
      candidateParentNode = candidateNode;
      candidateNode = candidateNode.right;
    }
    // 如果候选节点没有右子树, 则当前节点就是最终替补节点
    if (candidateNode == candidateParentNode) {
      candidateNode.right = currentNode.right;
      if (isLeftChild) {
        parentNode.left = candidateNode;
      } else {
        parentNode.right = candidateNode;
      }
    }
    // 如果候选节点有右子树
    else {
      // 再判断是否有左子树 (隔代)
      if (candidateNode.left) {
        candidateParentNode.right = candidateNode.left;
      } else {
        candidateParentNode.right = null;
        candidateNode.left = currentNode.left;
        candidateNode.right = currentNode.right;
        if (isLeftChild) {
          parentNode.left = candidateNode;
        } else {
          parentNode.right = candidateNode;
        }
      }
    }
  }
  return true;
};
```

# 测试

```js
/*
 * 测试
 *
 * */

let binarySearchTree = new BinarySearchTree();
binarySearchTree.insert({ key: 11, value: "I'm 11 !" });
binarySearchTree.insert({ key: 7, value: "I'm 7 !" });
binarySearchTree.insert({ key: 15, value: "I'm 15 !" });
binarySearchTree.insert({ key: 5, value: "I'm 5 !" });
binarySearchTree.insert({ key: 3, value: "I'm 3 !" });
binarySearchTree.insert({ key: 9, value: "I'm 9 !" });
binarySearchTree.insert({ key: 8, value: "I'm 8 !" });
binarySearchTree.insert({ key: 10, value: "I'm 10 !" });
binarySearchTree.insert({ key: 13, value: "I'm 13 !" });
binarySearchTree.insert({ key: 12, value: "I'm 12 !" });
binarySearchTree.insert({ key: 14, value: "I'm 14 !" });
binarySearchTree.insert({ key: 20, value: "I'm 20 !" });
binarySearchTree.insert({ key: 18, value: "I'm 18 !" });
binarySearchTree.insert({ key: 25, value: "I'm 25 !" });
binarySearchTree.insert({ key: 19, value: "I'm 19 !" });
//
//                            11
//                  7                     15
//            5         9             13      20
//        3           8  10         12 14   18   25
//                                           19
//

// 先序
// binarySearchTree.preorderTraversal(function (value) {
//   console.log(value);
// });
// 中序
// binarySearchTree.inOrderTraversal(function (value) {
//   console.log(value);
// });
// 后序
// binarySearchTree.postorderTraversal(function (value) {
//   console.log(value);
// });
// 层序
// console.log(binarySearchTree.levelTraversal());
// 最大值
// console.log(binarySearchTree.max());
// 最小值
// console.log(binarySearchTree.min());
// 搜索 key
// console.log(binarySearchTree.search(11));
// console.log(binarySearchTree.search(7));
// console.log(binarySearchTree.search(15));
// console.log(binarySearchTree.search(5));
// console.log(binarySearchTree.search(3));
// console.log(binarySearchTree.search(9));
// console.log(binarySearchTree.search(8));
// console.log(binarySearchTree.search(10));
// console.log(binarySearchTree.search(6));
// console.log(binarySearchTree.search(13));
// console.log(binarySearchTree.search(12));
// console.log(binarySearchTree.search(14));
// console.log(binarySearchTree.search(20));
// console.log(binarySearchTree.search(18));
// console.log(binarySearchTree.search(25));
console.log(binarySearchTree.levelTraversal());
console.log(binarySearchTree.remove(11));
console.log(binarySearchTree.levelTraversal());
```
