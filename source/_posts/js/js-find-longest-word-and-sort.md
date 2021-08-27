---
title: 用 Js 找出最长的单词并排序
date: 2021-06-15 11:15:48
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/sunrise.jpg
cover:
tags:
  - js
  - javascript
categories:
  - js
aside:
comments:
---

```js
// 找出最长的单词并输出每个单词的长度
var str = "My name is Tom , I love jerry !";
var maxLength = 0;
var maxLengthWord = [];
var strList = str.split(" ");

for (let i = 0; i < strList.length; i++) {
  if (i + 1 <= strList.length - 1) {
    // 如果后者长度大于前者长度 且 后者长度大于或等于已知的最大长度，就存于 maxLengthWord 数组
    if (
      strList[i].length < strList[i + 1].length &&
      strList[i + 1].length >= maxLength
    ) {
      // 避免重复
      // 如果不存在就 push
      if (maxLengthWord.indexOf(strList[i + 1]) == -1) {
        maxLengthWord.push(strList[i + 1]);
        maxLength = strList[i + 1].length;
      }
    }
    // 如果后者长度等于前者长度 且 长度大于或等于已知的最大长度，就将两者都存于 maxLengthWord 数组
    else if (
      strList.length == strList[i + 1].length &&
      strList[i].length >= maxLength
    ) {
      // 避免重复
      // 如果不存在就 push
      if (maxLengthWord.indexOf(strList[i]) == -1) {
        maxLengthWord.push(strList[i]);
      }
      // 避免重复
      // 如果不存在就 push
      if (maxLengthWord.indexOf(strList[i + 1]) == -1) {
        maxLengthWord.push(strList[i + 1]);
      }
      maxLength = strList[i].length;
    }
    // 后者长度小于前者长度 且 前者长度大于已知的最大长度，就存于 maxLengthWord 数组
    else if (
      strList[i].length > strList[i + 1].length &&
      strList[i].length >= maxLength
    ) {
      // 避免重复
      // 如果不存在就 push
      if (maxLengthWord.indexOf(strList[i]) == -1) {
        maxLengthWord.push(strList[i]);
        maxLength = strList[i].length;
      }
    }
  }
}

console.log('" ' + str + ' "');

maxLengthWord.forEach(function (value) {
  console.log("最长单词为: " + value + " ,单词长度为" + value.length);
});
```
