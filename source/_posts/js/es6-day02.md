---
title: ES6 新增用法 ( 二 )
date: 2021-06-20 15:02:37
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/sunrise.jpg
cover:
tags:
  - js
  - javascript
  - ES6
  - 解构赋值
categories:
  - js
  - ES6
comments:
---

# 解构赋值

## 数组

### 解构赋值

```js
let [a, b, c] = [1, 2, 3];
console.log(a); // 1
console.log(b); // 2
console.log(c); // 3
```

### 不完全解构

```js
let [a, b, c] = [1, 2];
console.log(a); // 1
console.log(b); // 2
console.log(c); //undefined
```

### 嵌套

```js
let [a, [b, [c, [d, [e, [f]]]]]] = [1, [2, [3, [4, [5, [6]]]]]];
console.log(a); // 1
console.log(b); // 2
console.log(c); // 3
console.log(d); // 4
console.log(e); // 5
console.log(f); // 6
```

### 可以赋默认值

```js
let [a, b = 3] = [1];
console.log(a); // 1
console.log(b); // 3
```

## 对象

### 解构赋值

```js
let { a, b, c } = { a: 1, c: 2, b: 3 };
console.log(a); // 1
console.log(b); // 3
console.log(c); // 2
```

### 不完全解构

```js
let { a } = { b: 1 };
console.log(a); // undefined
```

### 嵌套

```js
let {
  a: {
    b: { c },
  },
} = { a: { b: { c: 1 } } };
console.log(c);
console.log(a); // a 与 b 只是为了样式一样
console.log(b); // 1
```

### 默认值

```js
let { a, b = 1 } = { a: 1 };
console.log(a); // 1
console.log(b); // 1
```

## 字符串

### 解构赋值

```js
let [a, b, c, d, e, f] = "pretty";
console.log(a); // p
console.log(b); // r
console.log(c); // e
console.log(d); // t
console.log(e); // t
console.log(f); // y
```

# 结构赋值的用途

## 变量交换

```js
let a = 1;
let b = 3;
[a, b] = [b, a];
console.log(a); // 3
console.log(b); // 1
```

## 返回多个值

```js
function demo() {
  return { name: "张三", age: 12 };
}
let { name, age } = demo();
console.log(name); // 张三
console.log(age); // 12
```

## 定义函数参数

```js
function demo1({ a, b, c }) {
  console.log(a); // 李四
  console.log(b); // 22
  console.log(c); // 175
}
demo1({ a: "李四", b: 22, c: 175 });
```

## 函数参数的默认值

```js
function fn1({ name = "张三" }) {
  console.log(name);
}
fn1({ name: "李四" }); // 李四
fn1({}); // 张三
```

# ES6 中字符串的用法

## 模板字符串

**`${}`**

```js
let Person = {
  name: "张三",
  age: 22,
  sex: "男",
  hobby: "钓鱼",
};
let str = `我的名字是${Person.name},今年${Person.age}岁了,性别${Person.sex},爱好${Person.hobby}`;
console.log(str); // 我的名字是张三,今年22岁了,性别男,爱好钓鱼
```

## repeat( )

`repeat()` 函数 : 将目标字符串重复 `N` 次 , 返回一个新的字符串 , 不影响原字符串

```js
let str1 = "嘿";
let str2 = str1.repeat(2);
console.log(str2); // 嘿嘿
```

## includes( )

`includes()` 函数 : 判断字符串中是否含有指定的子字符串 , 返回 `true` 表示含有, `false` 表示未含有。第二个参数选填 , 表示开始搜索的位置 (下标从 `0` 开始)

```js
let str = "codehhr";
console.log(str.includes("c")); // true
console.log(str.includes("code")); // true
console.log(str.includes("h", 5)); // true
console.log(str.includes("h", 6)); // false
```

## startsWith( )

判断指定的子字符串是否出现在目标字符串的开头位置 , 第二个参数选填，表示开始搜索的位置 (从下标 `0` 开始)

```js
let str = "codehhr";
console.log(str.startsWith("c")); // true
console.log(str.startsWith("code")); // true
console.log(str.startsWith("c", 0)); // true
console.log(str.startsWith("c", 1)); // false
```

## endsWith( )

判断子字符串是否出现在目标字符串的尾部位置 , 第二个参数选填 , 表示从头开始截取的长度

```js
let str = "codehhr";
console.log(str.endsWith("r")); // true
console.log(str.endsWith("hr")); // true
console.log(str.endsWith("hr", 6)); // false
console.log(str.endsWith("hr", 7)); // true
```

## String.raw

返回未加工的字符串

```js
// 后面跟模板字符串
console.log(String.raw`hello\nworld`); // hello\nworld
```

# ES6 中数组的用法

## Array.of( )

将一组值 , 转换成数组

```js
let newArr = Array.of(1, 2, 3, 4, 5);
console.log(newArr); // [1,2,3,4,5]
```

## Array.from( )

将类似数组的对象或者可遍历的对象转换成真正的数组

```js
let str = "hello";
console.log(Array.from(str)); // ["h", "e", "l", "l", "o"]
```

## find( )

找出数组中符合条件的第一个元素

```js
let arr = [1, 2, 3, 4, 5, 6, 7, 8];
console.log(
  arr.find(function (value) {
    return value > 7;
  })
); // 8
```

## findIndex( )

返回符合条件的第一个数组成员的位置

```js
let arr = [1, 2, 3, 4, 5, 6, 7, 8];
console.log(
  arr.findIndex(function (value) {
    return value > 7;
  })
); // 7
```

## fill( )

用指定的值 , 填充到数组 , 会更改原数组
多个参数时 , 第一个为要填充的内容 , 第二个为起始位置 (下标从 `0` 开始) , 第三个参数为结束位置 ( 结束位置不填充 )

```js
let arr = [1, 2, 3, 4, 5];
arr.fill(6);
console.log(arr); // [6, 6, 6, 6, 6]
arr.fill(6, 0, 2); // [6, 6, 3, 4, 5]
```

## entries( )

对数组的键值对进行遍历 , 返回一个遍历器

```js
for (let [index, value] of ["html", "css", "js"].entries()) {
  console.log(index, value);
}
// 0 "html"
// 1 "css"
// 2 "js"
```

## keys( )

对数组的索引键进行遍历 , 返回一个遍历器

```js
for (let index of [1, 2].keys()) {
  console.log(index);
}
// 0
// 1
```

## values

对数组的元素进行遍历 , 返回一个遍历器

```js
for (let value of [1, 2].values()) {
  console.log(value);
}
// 1
// 2
```

# The_End
