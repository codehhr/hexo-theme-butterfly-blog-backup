---
title: Js 正则表达式
date: 2021-06-19 15:06:18
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/sunrise.jpg
cover:
tags:
  - js
  - javascript
  - RegExp
  - 正则
  - test
  - match
  - replace
categories:
  - js
comments:
---

# 1. 正则表达式的作用

给定的字符串是否符合正则表达式的过滤逻辑 ( 匹配 )
可以通过正则表达式，从字符串中获取我们想要的特定部分 ( 提取 )
强大的字符串替换能力 ( 替换 )

# 2. 正则的组成

## (1) 特殊字符

普通数字 , 字母 , 中文 , 符号 , 特殊字符 . . .

## (2) 常用元字符

| 元字符 | 说明                                  |
| :----: | :------------------------------------ |
|   \d   | 匹配至少一个数字                      |
|   \D   | 匹配至少一个除数字外的任意字符        |
|   \w   | 匹配至少一个字母或数字或下划线 ( \_ ) |
|   \W   | 匹配至少一个非字母或数字或下划线      |
|   \s   | 匹配至少一个空白字符                  |
|   \S   | 匹配至少一个非空白任意字符            |
|   .    | 匹配除换行符以外的任意单个字符        |
|   ^    | 匹配行首的文本 ( 以谁开始 )           |
|   $    | 匹配行尾的文本 ( 以谁结束 )           |

## (3) 限定符

| 限定符 | 说明             |
| :----: | :--------------- |
|   \*   | 重复零次或更多次 |
|   +    | 重复一次或多次   |
|   ?    | 重复零次或一次   |
|  {n}   | 重复 n 次        |
|  {n,}  | 至少重复 n 次    |
| {n,m}  | 重复 n 到 m 次   |

## (4) 其他符号

|    其他符号     | 说明                                                                               |
| :-------------: | :--------------------------------------------------------------------------------- |
|       []        | 字符串用中括号括起来，表示匹配其中的任一字符 , 相当于或的意思, 比如 0 到 9 : [0-9] |
|       [^]       | 匹配除中括号以内的内容 , 比如 [^0-9] , 就是除了 0 到 9 之外的内容                  |
|       \\        | 转义符： \ 的用法主要是用法是在正则表达式中的特殊符号转换为它本身的意思            |
|       \|        | 或者，选择两者中的一个。注意将左右两边分为两部分，而不管左右两边有多长多乱         |
|       ( )       | 从两个直接量中选择一个                                                             |
| [\u4e00-\u9fa5] | 匹配汉字                                                                           |

# 3. 创建正则对象

## (1) 字面量创建

```js
var reg = /\d/;
```

## (2) 构造函数创建

```js
var regObj = new RegExp(/\d/);
```

# 4. 正则匹配

在 `RegExp` 的原型上有个 `test` 方法,用类测试是否匹配成功

`RegExp.prototype.test()`

**语法** :`reg.test(str)`
**参数** : `str` 与正则表达式匹配的字符串
**返回值** : 如果正则表达式与指定的字符串匹配 , 返回 `true` ; 否则 `false`

**案例 :**

**html**

```html
<input type="email" name="" id="" /> <button>提交</button>
```

**js**

```js
// 验证输入邮箱
var reg = /^([a-zA-Z]|[0-9])(\w|\-)+@[a-zA-Z0-9]+\.([a-zA-Z]{2,4})$/;
document.querySelector("button").addEventListener("click", function () {
  var value = document.querySelector("input").value;
  console.log(reg.test(value));
});
```

# 5. 正则提取

`String.prototype.match()`

**语法** : `str.match(reg)`
**参数** : `reg`
**返回值 :** 如果使用 `g` 标志，则将返回与完整正则表达式匹配的所有结果 ( `Array` ), 但不会返回捕获组 , 或者未匹配返回 ` null`
如果未使用 `g` 标志，则仅返回第一个完整匹配及其相关的捕获组( `Array` ) 或者未匹配返回 ` null`

**案例 :**

**html**

```html
<input type="text" name="" id="" /> <button>提取</button>
```

**js**

```js
// 提取非数字
var reg = /[^\d]/g;
document.querySelector("button").addEventListener("click", function () {
  var value = document.querySelector("input").value;
  console.log(value.match(reg));
});
```

# 6. 正则替换

`String.prototype.replace()`

**原字符串不会改变**

**语法** : `str.replace(regexp|substr, newSubStr|function)`

**返回值 :** 替代后的新的字符串。

**案例 :**
全局匹配,将 " l " 替换为 " L "

```js
var str = "Hello World!";
console.log(str.replace(/l/g, "L"));
```

# The_End
