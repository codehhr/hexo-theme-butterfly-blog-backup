---
title: Js 递归
date: 2021-06-19 09:00:22
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/sunrise.jpg
cover:
tags:
  - javascript
  - js
  - recursive
  - 递归
categories:
  - js
comments:
---

# 简单来说递归就是函数直接或间接调用自己

# 案例

## 1. 递归实现 1 + ... + n

```js
function sum(n) {
  if (n == 1) {
    return 1;
  }
  return n + sum(n - 1);
}
console.log(sum(3));
console.log(sum(4));
console.log(sum(100));
```

## 2. 递归实现 1 \* . . . \* n

```js
function sum2(n) {
  if (n == 1 || n == 0) {
    return 1;
  }
  return n * sum2(n - 1);
}
console.log(sum2(3));
console.log(sum2(4));
console.log(sum2(5));
console.log(sum2(6));
```

## 3. 递归实现斐波那契数列

```js
// 1,1,2,3,5,8 . . .
function feiBoNaQi(n) {
  if (n == 1 || n == 2) {
    return 1;
  }
  return feiBoNaQi(n - 1) + feiBoNaQi(n - 2);
}
console.log(feiBoNaQi(1));
console.log(feiBoNaQi(2));
console.log(feiBoNaQi(3));
console.log(feiBoNaQi(4));
console.log(feiBoNaQi(5));
console.log(feiBoNaQi(6));
```

## 4. 一共 10 级楼梯，每次可以走一步或两步，求一共多少种走法?

```js
// 1阶 => 1种
// 2阶 => 2种
// 3阶 => 3种
// 4阶 => 5种
// 假设有 5 阶,去掉一阶就是 4 阶,相当于假设最后走一步,然后加上 4 阶的走法

function feiBoNaQi(n) {
  if (n == 1) {
    return 1;
  }
  if (n == 2) {
    return 2;
  }
  return feiBoNaQi(n - 1) + feiBoNaQi(n - 2);
}
console.log(feiBoNaQi(5));
```

## 5. 假设一个细胞一小时后分裂成两个 , 生命周期为三个小时 , 若开始有一个细胞 , n 小时后有多少个细胞?

**黑色代表那个细胞生命结束**

![cell-division](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/js/celldivision.png)
**方法 1**

```js
// 白
// 绿，白
// 黄，白，绿，白
// 白，绿，白，黄，白，绿，白
// 绿，白，黄，白，绿，白，白，绿，白，黄，白，绿，白
// 黄，白，绿，白，白，绿，白，黄，白，绿，白，绿，白，黄，白，绿，白，白，绿，白，黄，白，绿，白

// 白 (1,1,2,4,7,13,24)
// 绿 (0,1,1,2,4,7,13)
// 黄 (0,0,1,1,2,4,7)
// 总 (1,2,4,7,13,24)

// 找规律发现从第四项开始后者是前三项的和
function A(h) {
  switch (h) {
    case 1:
      return 2;
    case 2:
      return 4;
    case 3:
      return 7;
  }
  return A(h - 1) + A(h - 2) + A(h - 3);
}
console.log(A(7));
```

**方法 2**

```js
// 绿色细胞数量
function green(n) {
  if (n == 0) {
    return 0;
  }
  return white(n - 1);
}
// 黄色细胞数量
function yellow(n) {
  if (n == 0 || n == 1) {
    return 0;
  }
  return green(n - 1);
}
// 白色细胞数量
function white(n) {
  if (n == 0) {
    return 1;
  }
  return green(n - 1) + yellow(n - 1) + white(n - 1);
}
// 细胞数量总和
function total(n) {
  return green(n) + yellow(n) + white(n);
}
console.log(total(0)); // 1
console.log(total(1)); // 2
console.log(total(2)); // 4
console.log(total(3)); // 7
console.log(total(4)); // 13
console.log(total(5)); // 24
```

# The_End
