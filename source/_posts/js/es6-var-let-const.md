---
title: var 与 ES6 中的 let const 的区别
date: 2021-06-29 14:22:44
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/sunrise.jpg
cover:
tags:
  - js
  - jsvascript
  - ES6
  - var
  - let
  - const
categories:
  - js
  - ES6
comments:
---

# let const var 定义变量的区别是什么

- `let`

  - 块作用域
  - 没有变量提升
  - 不能重复声明

- `const`

  - 声明常量，不能修改
  - 必须初始化
  - 块作用域
  - 没有变量提升
  - 不能重复声明

- `var`
  - 没有块的概念
  - 可以跨块访问，但是不能跨函数访问
  - 会进行变量提升
