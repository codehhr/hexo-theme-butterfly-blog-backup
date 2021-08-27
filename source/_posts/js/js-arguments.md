---
title: Js 函数内置对象 arguments
date: 2021-06-18 08:53:59
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/sunrise.jpg
cover:
tags:
  - js
  - javascript
  - arguments
categories:
  - js
comments:
---

# js 函数中有个内置的对象 arguments

任何一个函数都有内置对象 `arguments` , `arguments` 前几个元素都是实参。
`length` : 实参的个数
`callee.length` : 形参的个数
`callee.name` : 函数名
`函数名.caller` : 函数的调用者

**案例 :**

```js
// 既然是伪数组,就可以遍历,利用这一点
function num() {
  let sum = 0;
  for (let i = 0; i < arguments.length; i++) {
    sum += arguments[i];
  }
  return sum;
}
console.log(num(1, 2, 3, 4));
```

# The_End
