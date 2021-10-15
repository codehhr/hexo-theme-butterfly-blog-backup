---
title: 用 Object.create 实现类式继承
date: 2021-10-15 12:42:19
updated:
tags:
  - javascript
  - js
  - 继承
categories:
  - js
keywords: Object.create
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

<!-- {% note info flat %}
`Object.create()` 方法创建一个新对象 , 使用现有的对象来提供新创建的对象的 `__proto__`
{% endnote %} -->

# 下面的例子演示了如何使用 Object.create() 来实现类式继承

```js
// Animal ( 父类 )
function Animal(color) {
  this.color = color;
}

// 二哈 ( 子类 )
function ErHa(color) {
  // 拿到父类属性 ( call super constructor )
  Animal.call(this, color);
}

// 子类续承父类
ErHa.prototype = Object.create(Animal.prototype);
ErHa.prototype.constructor = ErHa;

// 新建子类实例
let erha = new ErHa("black");

// 验证
console.log(erha instanceof ErHa); // true
console.log(erha instanceof Animal); // true
```
