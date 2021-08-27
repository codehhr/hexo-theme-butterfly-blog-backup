---
title: Js 数组去重并排序
date: 2021-06-15 11:19:50
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/sunrise.jpg
cover:
tags:
  - js
  - javascript
  - 数组排序
  - sort
  - 数组去重
categories:
  - js
aside:
comments:
---

```js
// 数组去重并从大到小排序

var arr = [7, 8, 8, 1, 6, 10, 1, 2, 2, 3, 9, 2, 4, 1, 5, 7, 7, 2, 2];

function getNewArr(arr) {
  let newArr = [];
  // 去重
  arr.forEach(function (value) {
    if (newArr.indexOf(value) == -1) {
      newArr.push(value);
    }
  });

  // 从大到小排序

  // 遍历 n-1 次
  for (let i = 0; i < newArr.length - 1; i++) {
    // 每次排序次数从 n-1 开始递减 (下标 n-2)
    for (let j = newArr.length - 2; j >= 0; j--) {
      if (j + 1 <= newArr.length - 1) {
        if (newArr[j] < newArr[j + 1]) {
          // 两者交换
          let temp = newArr[j];
          newArr[j] = newArr[j + 1];
          newArr[j + 1] = temp;
        }
      }
    }
  }
  return newArr;
}

console.log(getNewArr(arr));
```

# The_End
