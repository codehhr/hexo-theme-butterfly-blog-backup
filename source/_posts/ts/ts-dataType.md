---
title: Ts 基础静态类型和复杂静态类型
date: 2021-11-08 22:57:57
updated:
tags:
categories:
keywords:
description:
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/sunrise.jpg
cover: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/ts/ts.jpeg
comments:
copyright:
copyright_author:
copyright_author_href:
copyright_url:
copyright_info:
---

# 基础静态类型

```js
let num: Number = 123;
let code: String = "TypeScript";
let flag: Boolean = true;
// 以及 Undefinde, Null, Void, Symbol
```

# 复杂静态类型

## 对象

{% note warning no-icon %}
**有很多形式**
{% endnote %}

### 直接声明

```ts
let person: {
  name: String;
  age: Number;
} = {
  name: "ts",
  age: 123,
};
```

### interface

```ts
interface Animal {
  color: String;
}
let dag: Animal = {
  color: "brown",
};
```

### 类或者构造函数

```ts
class Person {
  constructor(parameters) {
    // ...
  }
}
let man: Person = new Person();
```

### 声明函数返回值类型

下面用箭头函数演示

```ts
let fun: () => String = () => {
  return "string";
};
```

## 数组

```ts
let arr: String[] = ["js", "ts", "py", "c"];
```
