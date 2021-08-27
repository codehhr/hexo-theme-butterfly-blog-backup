---
title: Js 基础总结及案例
date: 2021-05-13 15:03:46
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/sunrise.jpg
cover: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/js/js.jpeg
aside:
tags:
  - js
  - javascript
  - 基础总结
categories:
  - js
---

# 一. JavaScript 介绍

## (1) 、JavaScript 是什么

### 1. JavaScript 的历史

Netscape（网景）在最初将其脚本语言命名为 LiveScript，是布兰登.艾克发明的。后来 Netscape 在与 Sun 合作之后将其改名为 JavaScript。JavaScript 最初受 Java 启发而开始设计的，目的之一就是“看上去像 Java”，因此语法上有类似之处，一些名称和命名规范也借自 Java。JavaScript 与 Java 名称上的近似，是当时 Netscape 为了营销考虑与 Sun 微系统达成协议的结果。

### 2. JavaScript 是什么语言

可以说：Java 服务器端的编程语言，JavaScript 运行在客户端(浏览器)的编程语言
JavaScript(简称 JS)是一种运行在客户端的脚本语言，JavaScript 的解释器被称为 JavaScript 引擎，为浏览器的一部分，广泛用于客户端的脚本语言，最早是在 HTML（标准通用标记语言下的一个应用）网页上使用，用来给 HTML 网页增加动态功能。
也可以说，是一门脚本语言、是一门解释性语言、是一门动态类型的语言、是一门基于
对象的语言。（不是面向对象）、是一门弱性语言

### 3. JavaScript 的发展和意义

最初的目的是为了处理表单的验证操作。JavaScript 发展到现在几乎无所不能，例如：做网页特效、与交互（表单的提交），比如：轮播图、tab 切换、返回顶部。。。
例如：网页特效、服务端开发(Node.js)、命令行工具(Node.js)、桌面程序(Electron)、App(Cordova)、控制硬件-物联网(Ruff)、游戏开发(cocos2d-js)

### 4. JavaScript 和 HTML、CSS 的区别

`HTML` - 提供网页的结构，提供网页中的内容
`CSS` - 用来美化网页
`JavaScript` - 可以用来控制网页内容，给网页增加动态的效果

### 5. JavaScript 的组成

![js](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/js/jscontent.png)

#### （1）ECMAScript - JavaScript 的核心

ECMA 欧洲计算机制造联合会。JavaScript 的核心，描述了语言的基本语法和数据类型，ECMAScript 是一套标准，定义了一种语言的标准与具体实现无关。

#### （2）BOM - 浏览器对象模型

一套操作浏览器功能的 API。通过 BOM 可以操作浏览器窗口，比如：弹出框、控制浏览器跳转、获取分辨率等。Borswer object model

#### （3）DOM - 文档对象模型

一套操作页面元素的 API。DOM 可以把 HTML 看做是文档树，通过 DOM 提供的 API 可以对树上的节点进行操作。Document object model

## (2) JavaScript 代码写法

CSS 代码写法分为行内样式、嵌入样式（内部）、外部样式、控制台书写。那么，js 的代码可以分四个地方写：  
1.在 html 的文件中,script 的标签中写 js 代码  
2.js 代码可以在 html 的标签中写  
3.在 js 文件中可以写 js 代码,但是需要在 html 页面中引入 script 的标签中的 src="js 的路径"  
4.还可以在控制台直接书写 js 代码

### (3) JavaScript 问题总结

1. 在一对 script 的标签中有错误的 js 代码,那么该错误的代码后面的 js 代码不会执行
2. 如果第一对的 script 标签中有错误,不会影响后面的 script 标签中的 js 代码执行
3. script 的标签中可以写 type="text/javascript"标准写法或者写 language="JavaScript"都可以。但是，目前在我们的 html 页面中，type 和 language 都可以省略，原因：html 是遵循 h5 的标准。
4. 有可能会出现这种情况：script 标签中可能同时出现 type 和 language 的写法。
5. script 标签在页面中可以出现多对。
6. script 标签一般是放在 body 的标签的最后的，有的时候会在 head 标签中，目前讲课的时候都在 body 标签的后面(body 中的最后)。
7. 如果 script 标签是引入外部 js 文件的作用，那么这对标签中不要写任何的 js 代码，如果要写，重新写一对 script 标签，里面写代码。

### (4) 注释

单行注释

```js
// var a;
```

多行注释

```js
/*
var a = 1
var b = 1
*/
```

# 二. JavaScript 变量

## (1) 变量引入

**什么是变量**
变量是计算机内存中存储数据的标识符，根据变量名称可以获取到内存中存储的数据
**为什么要使用变量**
使用变量可以方便的获取或者修改内存中的数据

## (2) 变量声明和初始化

`var` 声明变量

```js
var age;
```

变量的赋值

```js
var age;
age = 18;
```

同时声明多个变量

```js
var age, name, sex;
age = 10;
name = "zs";
```

同时声明多个变量并赋值

```js
var age = 10,
  name = "zs";
```

变量在内存中的存储

```js
var age = 18;
```

## (3) 变量的命名规则和规范

**规则 - 必须遵守的，不遵守会报错**
1、由字母、数字、下划线、$符号组成，不能以数字开头
2、不能是关键字和保留字，例如：for、while。
3、区分大小写
**规范 - 建议遵守的，不遵守不会报错**
1、变量名必须有意义
2、遵守驼峰命名法。首字母小写，后面单词的首字母需要大写。

## (4) 字面量

在源代码中一个固定值的表示法，也叫字面量。
数值字面量：8, 9, 10
字符串字面量：`'程序员'`, `"大前端"`
布尔字面量：`true`，`false`

# 三. JavaScript 数据类型

## (1) 基本数据类型

`Number`、`String`、`Boolean`、`Undefined`、`Null`

### 1. Number 类型

```js
// 十进制
var num = 9;
//进行算数计算时，八进制和十六进制表示的数值最终都被转换成十进制数值。

// 十六进制
var num = 0xA;//数字序列范围：0~9 以及 A~F

// 八进制
var num1 = 07;  // 对应十进制的 7
var num2 = 011; // 对应十进制的 9
var num3 = 021; // 对应十进制的 17 //数字序列范围：0~7
// 如果字面值中的数值超出了范围，那么前导零将被忽略，后面的数值将被当作十进制数值解析

// 浮点数
var n = 5e-5;   // 科学计数法 5 乘以 10 的-5 次方  

// 浮点数值的最高精度是 17 位小数，但在进行算术计算时其精确度远远不如整数
var result = 0.1 + 0.2; // 结果不是 0.3，而是：0.30000000000000004
console.log(0.07 * 100);

// 注意：不要判断两个浮点数是否相等
// 就是说由于 0.1 转换成二进制时是无限循环的，所以在计算机中 0.1 只能存储成一个近似值

// 最小值：
// 这个值为： 5e-324
Number.MIN_VALUE

// 最大值：
// 这个值为： 1.7976931348623157e+308
Number.MAX_VALUE

无穷大：Infinity
无穷小：-Infinity
```

### 数值判断

```js
//可以通过 Number()方法判断
NaN：not a number
NaN 与任何值都不相等，包括他本身
isNaN(): is not a number
// 如果 x 是特殊的非数字值 NaN (或者能被转换为这样的值 )，返回的值就是 true。如果 x 是其他值,则返回 false
```

### 2、String 类型

字符串可以使用单引号,也可以使用双引号，例如：`'abc'`、`"abc"`
字符串字面量：`'I am Happy'`、`"Hello World"`

#### 转义符

![striingtranslate](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/js/striingtranslate.png)

#### 字符串长度

```js
// length属性用来获取字符串的长度;
var str = "Hello World";
console.log(str.length);
```

#### 字符串拼接

```js
// 字符串拼接使用 + 连接;
console.log(11 + 11);
console.log("hello" + " world");
console.log("100" + "100");
console.log("11" + 11);
console.log("male:" + true);
// 两边只要有一个是字符串，那么+就是字符串拼接功能
// 两边如果都是数字，那么就是算术功能。
```

语言具有隐式转换 ( 隐式类型转换就是指，数据的类型在不用人工干预的情况下进行转换的行为，原因：`js` 是一门弱类型（动态类型）的语言，他在声明变量的时候不需要指定类型，对变量赋值也没有类型的检测，所以 `js` 是非常的灵活的，)

### 3. Boolean 类型

`Boolean` 字面量： `true` 和 `false`，区分大小写
计算机内部存储：`true` 为 `1`，`false` 为 `0`

### 4. Undefined 和 Null

`undefined` 表示一个声明了没有赋值的变量，变量只声明的时候值默认是 `undefined`
`null` 表示一个空，变量的值如果想为 `null`，必须手动设置

## (2) 复杂数据类型

`Object`

## (3) 数据类型转换

### `typeof` 关键字

获取变量的类型

```js
var age = 18;
console.log(typeof age); // number
```

```js
console.log(typeof null); // Object
```

**一个 bug，`null` 为什么是引用类型（复杂类型）？**

在 JS 的最初版本中使用的是 32 位系统，为了性能考虑使用低位存储变量的类型信息，000 开头的是对象，`null` 是全 0，所以将 `null` 误判为 `Object` 了，虽然现在的内部类型判断代码已经改变了，但 bug 永久的遗留下来了

### toString()

转换成字符串类型

```js
var num = 5;
console.log(num.toString()); // String("5")
```

### String()

`String()` 函数存在的意义：有些值没有 `toString()`, 这个时候可以使用 `String()`.比如：`undefined` 和 `null`

### 拼接字符串方式

`num + ""`，当 + 两边一个操作符是字符串类型，一个操作符是其它类型的时候，会先把其它类型转换成字符串再进行字符串拼接，返回字符串

### 转换成数值类型

`Number()` 可以把任意值转换成数值，如果要转换的字符串中有一个不是数值的字符，返回 `NaN`
#### Number()转化规则
a. 如果字符串中只包含数字时，将其转换为十进制数值，忽略前导 0
b. 如果字符串中包含有效浮点格式，如“1.1”，将其转换为对应的浮点数字，忽略前导 0
c. 如果字符串中包含有效的十六进制格式，如“0xf”，将其转换为相同大小的十进制数值
d. 如果字符串为空，或者是空内容，将其转换为 0
e. 如果字符串中包含除上述格式之外的字符，则将其转换为 NaN

#### parseInt()

```js
// 返回 12，如果第一个字符是数字会解析知道遇到第一个小数点结束
var num1 = parseInt("12.3abc");
// 返回 NaN，如果第一个字符不是数字或者符号就返回 NaN
var num2 = parseInt("abc123");
```

#### parseFloat()

`parseFloat()` 把字符串转换成浮点数，`parseFloat()` 和 `parseInt()` 非常相似，不同之处在与
`parseFloat()` 会解析第一个`.` 遇到第二个 `.` 或者非数字结束
如果解析的内容里只有整数，解析成整数

#### 正负运算

```js
var str = "500";
console.log(+str); // 取正
console.log(-str); // 取负
```

### 转换成布尔类型

**`Boolean()`**
`0`, `''`, `null`, `undefined`, `NaN`, 会转换成 `false`,其它都会转换成 `true`

# 四. JavaScript 运算

## (1) 算术运算符

`+ - * / %`

## (2) 一元运算符

一元运算符：只有一个操作数的运算符
`5 + 6` 两个操作数的运算符是二元运算符
`++` 自身加 1, `--` 自身减 1

**前置 `++` 先将自身的值自增 1，再将自增后的值赋值给变量**

```js
var num1 = 5;
++num1;
console.log(num1); // 6
```

**后置 `++` 先将自身的值赋值给变量，然后再自增 1**

```js
var num2 = 5;
console.log(num2++); // 5
console.log(num2); // 6
```

**总结：**
前置 `++`： 先加后输出
后置 `++`： 先输出后加

## (3) 逻辑运算符 (布尔运算符)

`&&` (与) 两个操作数同时为 `true`，结果为 `true`，否则都是 `false`
`||` (或) 两个操作数有一个为 `true`，结果为 `true`，否则为 `false`
`!` (非) 取反

## (4) 关系运算符(比较运算符)

`< > >= <= == != === !==`
`==` 与 `===` 的区别：`==` 只进行值得比较，`===` 类型和值同时相等，则相等

```js
var result = "55" == 55; // true
var result = "55" === 55; // false 值相等，类型不相等
var result = 55 === 55; // true 值和类型都相等
```

## (5) 赋值运算符

`= += -= *= /= %=`

```js
num += 5; //相当于 num = num + 5;
num *= 5; //相当于 num = num * 5;
```

## (6) 运算符的优先级

**优先级从高到底如下：**

括号>点运算符>一元运算符> 算数运算符 >关系运算符>逻辑运算符 >赋值运算符

**注意：同级运算符先后顺序如下：**
一元运算符 `++` `--` `!`
算数运算符 先 `*` `/` `%` 后 `+` `-`
关系运算符 `>` `>=` `<` `<=` `==` `!=` `===` `!==`
逻辑运算符 先 `&&` 后 `||`

## 运算优先级练习

**优先级： 括号>点运算符>一元运算符> 算数运算符 >关系运算符>逻辑运算符 >赋值运算符**
(1)

```js
4 >= 6 || ("人" != "阿凡达" && !(12 * 2 == 144) && true);
// 第一轮 4 >= 6 || ("人" != "阿凡达" && !(false) && true)
// 第二轮 4 >= 6 || ("人" != "阿凡达" && true && true)
// 第三轮 false || (true && true && true)
// 第四轮 false || true
// 结果为 true
```

(2)

```js
100.2 >= 52 || ("蛇" != "眼镜蛇" && !(25 * 4 == 120)) || true;
// 结果为 true
// 第一轮 : 100.2 >= 52 || ("蛇" != "眼镜蛇" && !false) || true
// 第二轮 : 100.2 >= 52 || ("蛇" != "眼镜蛇" && true) || true
// 第三轮 : true || (true && true) || true
// 第四轮 : true
```

# 五. 流程控制

程序的三种基本结构
顺序结构：从上到下执行的代码就是顺序结构(程序默认就是由上到下顺序执行的)
分支结构：根据不同的情况，执行对应代码
循环结构：重复做一件事情

## 1. 分支结构

### (1) if 语句

`if` 语句  - 只有当指定条件为 true 时，使用该语句来执行代码
`if...else` 语句  - 当条件为 true 时执行代码，当条件为 false 时执行其他代码
`if...else if....else` 语句- 使用该语句来选择多个代码块之一来执行

**if 案例判断一个人的年龄是否满 18 岁(是否成年)**

```js
if // 判断
if // (条件) {执行语句}
var age = 19;
if (age >= 18) {
  console.log("成年了");
}

if (age < 18) {
  console.log("未成年");
}

// 弹出输入框
prompt("参数会展示在页面上") // 点击确认会返回输入内容，点击取消会返回 null

var a = prompt();
console.log(a);

var age = prompt();
if (age >= 18) {
  console.log("成年了");
}
if (age < 18) {
  console.log("未成年");
}
```

**if 案例百分制转换成等级制**

```js
var grade = prompt("请输入成绩");
if (grade > 0 && grade < 60) {
  console.log("不及格");
} else if (grade < 70) {
  console.log("及格");
} else if (grade < 80) {
  console.log("良");
} else if (grade < 90) {
  console.log("良好");
} else if (grade <= 100) {
  console.log("优秀");
} else {
  console.log("请输入0-100");
}
```

### (2) 三元运算符

`表达式 1` ? `表达式 2` : `表达式 3`
是对 `if ... else` 语句的一种简化写法

```js
age >= 18 ? console.log("成年") : console.log("未成年");
```

### (3) switch 语句

`switch` 语句
`break` 可以省略，如果省略，代码会继续执行下一个 `case`
`default` 关键词来规定匹配不存在时做的事情。
`switch case` 使用严格比较（===），值必须与要匹配的类型相同

```js
var day = prompt("请输入数字");
// prompt 返回类型为字符串
switch (Number(day)) {
  case 1:
    console.log("周一");
    break;
  case 2:
    console.log("周二");
    break;
  case 3:
    console.log("周三");
    break;
  case 4:
    console.log("周四");
    break;
  case 5:
    console.log("周五");
    break;
  case 6:
    console.log("周六");
    break;
  case 7:
    console.log("周日");
    break;
  default:
    console.log("666");
}
```

**百分制转换成等级制**

```js
var grade = prompt();
var g = parseInt(grade / 10);
console.log(g);
switch (g) {
  case 10:
    console.log("NB");
    break;
  case 9:
    console.log("优秀");
    break;
  case 8:
    console.log("良好");
    break;
  case 7:
    console.log("良");
    break;
  case 6:
    console.log("及格");
    break;
  default:
    console.log("不及格");
}
```

能用 `switch` 语句实现的就一定可以使用 `if` 实现，但是反之不一定，如果是区间范围就采用 `if` .如果是等值判断使用 `switch`

```js
// If 语句会把后面的值隐式转换成布尔类型
// 转换为 true ： 非空字符串 非 0 数字 true 任何对象
// 转换成 false ： 空字符串, 0, false, null, undefined
if (undefined) {
  console.log("OK");
} else {
  console.log("NO");
}
```

## 2. 循环结构

在 `javascript` 中，循环语句有三种，`while`、`do..while`、`for` 循环。

### (1) while 语句

while 循环会在指定条件为真时循环执行代码块

```js
//   死循环
// while (true) {
//   console.log();
// }

// 打印 1-100
var a = 1;
while (a <= 100) {
  console.log(a);
  a++;
  console.log(a++);
}

// 打印 1-100 的和
var sum = 0;
var b = 1;
while (b <= 100) {
  sum += b;
  b++;
}

// 打印 100 以内 7 的倍数
var c = 1;
while (c <= 100) {
  if (c % 7 == 0) {
    console.log(c);
  }
  c++;
  // ++c;
}

// 100 以内偶数及和
var d = 1;
var sum2 = 0;
while (d <= 100) {
  if (d % 2 == 0) {
    console.log(d + "是偶数");
    sum2 += d;
  }
  d++;
}
console.log(sum2);

// 100 以内奇数及和
var e = 1;
var sum3 = 0;
while (e <= 100) {
  if (e % 2 != 0) {
    console.log(e + "是奇数");
    sum3 += e;
  }
  e++;
}
console.log(sum3);
```

### (2) do...while 语句

`do..while` 循环和 `while` 循环非常像，二者经常可以相互替代，但是 `do..while` 的特点是不管条件成不成立，都会执行一次。

```js
// do ... while
// 打印 1-100 之间所有数的和
var f = 1;
var sum4 = 0;
do {
  console.log(f);
  sum4 += f;
  f++;
} while (f <= 100);

// 打印 100 以内 7的倍数
var g = 1;
do {
  if (g % 7 == 0) {
    console.log(g);
  }
  g++;
} while (g <= 100);

// 打印 100 以内所有偶数
var i = 1;
var sum = 0;
do {
  if (i % 2 == 0) {
    console.log(i + "是偶数");
    sum += i;
  }
  i++;
} while (i <= 100);
console.log(sum);
```

### (3) for 语句

`while` 和 `do...while` 一般用来解决无法确认次数的循环。`for` 循环一般在循环次数确定的时候比较方便

```js
// for 循环
// 1-100 和
var sum = 0;
for (var j = 1; j < 101; j++) {
  console.log(j);
  sum += j;
}
console.log(sum);

// 1-100 偶数和
var sum = 0;
for (var i = 1; i <= 100; i++) {
  if (i % 2 == 0) {
    sum += i;
  }
}
console.log(sum);

// 双层 for 循环
// 正方形
for (var i = 0; i < 10; i++) {
  for (var j = 0; j < 10; j++) {
    document.write("*");
  }
  document.write("<br />");
}

// 三角形
for (var i = 0; i < 10; i++) {
  for (var j = 0; j < i; j++) {
    document.write("#");
  }
  document.write("<br />");
}
```

### (4) continue 和 break

`break` :立即跳出整个循环，即循环结束，开始执行循环后面的内容（直接跳到大括号）
`continue` :立即跳出当前循环，继续下一次循环（跳到 `i++` 的地方）

```js
// break
// continue
var sum = 0;
for (var i = 1; i <= 100; i++) {
  if (i % 10 == 3) {
    break;
    // continue;
  }
}
sum += i;
console.log(sum);
```

### (5) 循环语句区别

#### 1. 循环结构的表达式不同

`do-while` 循环结构表达式为：`do`{循环体;}
`for` 循环的结构表达式为：`for`（单次表达式;条件表达式;末尾循环体）{中间循环体；}。
`while` 循环的结构表达式为：`while`（表达式）{循环体}

#### 2. 执行时判断方式不同

`do-while` 循环将先运行一次，因为经过第一次 `do` 循环后，当检查条件表达式的值时，其值为   不成立时而会退出循环。保证了至少执行 `do`{ }内的语句一次。
`for` 循环执行的中间循环体可以为一个语句，也可以为多个语句，当中间循环体只有一个语句时，其大括号{}可以省略，执行完中间循环体后接着执行末尾循环体。
`while` 循环执行时当满足条件时进入循环，进入循环后，当条件不满足时，执行完循环体内全部语句后再跳出（而不是立即跳出循环）。

#### 3. 执行次数不同

`do-while` 循环是先执行后判断，执行次数至少为一次。
`for` 循环是先判断后执行，可以不执行中间循环体。
`while` 循环先判断后执行，可以不执行中间循环体。

#### 4. 执行末尾循环体的顺序不同

`do-while` 循环是在中间循环体中加入末尾循环体，并在执行中间循环体时执行末尾循环体。
`for` 循环的中间循环体在条件判断语句里，执行末尾循环体后自动执行中间循环体。
`while` 循环的末尾循环体也是在中间循环体里，并在中间循环体中执行。

## 作业

```js
// 作业 1
// 求 1-100 所有数的乘积
var sum1 = 1;
for (var a = 1; a <= 100; a++) {
  sum1 *= a;
}
console.log(sum1);
// ---------------------------------------------
// 作业 2
// 求 1-100 之间所有奇数的和
var sum2 = 0;
for (var b = 1; b <= 100; b++) {
  if (b % 2 == 1) {
    sum2 += b;
  }
}
console.log(sum2);

// ---------------------------------------------
// 作业 3
// 计算 1-100 之间能被 3 整除的数的和
var sum3 = 0;
for (var c = 1; c <= 100; c++) {
  if (c % 3 == 0) {
    sum3 += c;
  }
}
console.log(sum3);

// ---------------------------------------------
// 作业 4
// 计算 1-100 之间不能被7整除的数的和
var sum4 = 0;
for (var d = 1; d <= 100; d++) {
  if (d % 7 == 0) {
  } else {
    sum4 += d;
  }
}
console.log(sum4);

// ---------------------------------------------
// 作业 5
// 本金10000元存入银行，年利率是千分之三，每过1年，将本金和利息相加作为新的本金。计算5年后，获得的本金是多少？
var money = 10000,
  rate = 0.003,
  years = 5,
  sum5 = 0;
sum5 += money;
for (var year = 1; year <= years; year++) {
  sum5 *= 1 + rate;
}
console.log(sum5);

// ---------------------------------------------
// 作业 6
// 有个人想知道，一年之内一对兔子能繁殖多少对？
// 于是就筑了一道围墙把一对兔子关在里面。已知一对兔子每个月可以生一对小兔子，而一对兔子从出生后第3个月起每月生一对小兔子。假如一年内没有发生死亡现象，那么，一对兔子一年内（12个月）能繁殖成多少对？
// (兔子的规律为数列，1，1，2，3，5，8，13，21)
var sum6,
  r1 = 1,
  r2 = 1;
for (var month = 1; month <= 12; month++) {
  sum6 = r1 + r2;
  r1 = r2;
  r2 = sum6;
  console.log("第" + month + "个月 : " + sum6 + " 只");
}
// ---------------------------------------------
// 作业 7
// 求 1-100 之间不能被 7 整除的整数的和（用continue）
var sum7 = 0;
for (var e = 1; e <= 100; e++) {
  if (e % 7 == 0) {
    continue;
  } else {
    sum7 += e;
  }
}
console.log(sum7);

// ---------------------------------------------
// 作业 8
// 求 200-300 之间所有的奇数的和（用continue）
var sum8 = 0;
for (var i = 200; i <= 300; i++) {
  if (i % 2 == 0) {
    continue;
  } else {
    sum8 += i;
  }
}
console.log(sum8);
// ---------------------------------------------
// 作业 9
// 求 200-300之间第一个能被7整数的数（break）
for (var j = 200; j <= 300; j++) {
  if (j % 7 == 0) {
    console.log(j);
    break;
  }
}
```

## 2. 调试

### (1) alert()

### (2) console.log()

### (3) debugger 关键字

debugger  关键字用于停止执行 JavaScript，并调用调试函数。这个关键字与在调试工具中设置断点的效果是一样的

### (4) 断点调试

# 六. 数组

## (1) 为什么要学习数组

之前学习的数据类型，只能存储一个值,比如：`Number`,`String`

## (2) 数组的定义

所谓数组，就是将多个元素（通常是同一类型）按一定顺序排列放到一个集合中，那么这个集合我们就称之为数组。
数组是一个有序的列表，可以在数组中存放任意的数据，并且数组的长度可以动态的调整

## (3) 通过数组字面量创建数组

```js
// 创建一个空数组
var arr1 = [];
// 创建一个包含3个数值的数组，多个数组项以逗号隔开
var arr2 = [1, 3, 4];
// 创建一个包含2个字符串的数组
var arr3 = ["a", "c"];
// 可以通过数组的length属性获取数组的长度
console.log(arr3.length);
// 可以设置length属性改变数组中元素的个数
arr3.length = 0;
```

## (4) 获取数组元素

```js
// 获取数组元素
// 按下标取值,从0开始
// 取值未定义的下标，值为 undefined
console.log(arr2[0]);
console.log(arr2[10]); // undefined
```

## (5) 遍历数组

遍历：遍及所有，对数组的每一个元素都访问一次就叫遍历。

```js
for (var i = 0; i < arr.length; i++) {
  console.log(arr[i]);
}
```

## (6) 数组中新增元素

```js
// 数组中新增元素
// 赋值
arr2[arr2.length] = 100;
console.log(arr2);

// push()
// 在数组末尾添加，返回数组长度
arr2.push(101);
console.log(arr2);

// unshift()
// 在数组开始添加任意元素,返回数组长度
arr2.unshift(0);
console.log(arr2);

// shift()
// 从数组中删除第一个元元素，并返回该元素的值.此方法会更改数组的长度
var r = arr2.shift();
console.log(r);
console.log(arr2);
```

## 数组练习案例

```js
// 求数组所有数平均值
var sum = 0;
var arr1 = [2, 3, 4];
for (var i = 0; i < arr1.length; i++) {
  sum += arr1[i];
}
console.log(sum);
console.log(sum / arr1.length);

// 数组最大值，最小值 (第一种)
var arr2 = [0, 1, , 32, 0, 2, 3, 4, 5, 6];
var min = arr2[0], // 假设第一个元素是最小值
  max = arr2[0]; // 假设第一个元素是最大值
for (var i = 0; i < arr2.length; i++) {
  if (arr2[i] > max) {
    max = arr2[i];
  }
  if (arr2[i] < min) {
    min = arr2[i];
  }
}
console.log(max);
console.log(min);
// 数组最大值，最小值 (第二种)
for (var i = 0; i < arr2.length; i++) {
  if (arr2[i] > arr2[i + 1]) {
    var temp = arr2[i + 1];
    arr2[i + 1] = arr2[i];
    arr2[i] = temp;
  }
}
max = arr2[arr2.length - 1];
console.log(max);

// indexOf()
// 返回在数组中可以找到一个给定元素的第一个索引，如果不存在，则返回 -1
// 数组去重
// 第一种
var arr3 = [1, 1, 22, 22, 55, 55, 9, 9];
var newArr = [];
for (var i = 0; i < arr3.length; i++) {
  if (arr3.indexOf(arr3[i]) == i) {
    newArr.push(arr3[i]);
  }
}
console.log(newArr);

// 第二种
// 遍历新数组,indexOf 返回判断 -1, 即不存在就 push()
for (var i = 0; i < arr3.length; i++) {
  if (newArr.indexOf(arr3[i]) == -1) {
    newArr.push(arr3[i]);
  }
}
console.log(newArr);
```

# 七. 函数

## (1) 为什么要有函数

如果要在多个地方求 1-100 之间所有数的和，应该怎么做？

## (2) 什么是函数

把一段相对独立的具有特定功能的代码块封装起来，形成一个独立实体，就是函数。
起个名字（函数名），在后续开发中可以反复调用。
函数的作用就是封装一段代码，将来可以重复使用。

## (3) 函数的定义

```js
// 1.具名函数
function name() {
  console.log("name");
}

// 2.匿名函数
var fun = function () {
  console.log("fun");
};
```

## (4) 函数的调用

```js
// 函数调用，加 (),即函数名();
// 特点：函数体只有在调用的时候才会执行，调用需要()进行调用。可以调用多次(重复使用)
name();
fun();
```

**示例**

```js
// 声明函数
function sayHi() {
  console.log("吃了没？");
}
// 调用函数
sayHi();
​
// 求1-100之间所有数的和
function getSum() {
  var sum = 0;
  for (var  i = 0; i < 100; i++) {
    sum += i;
  }
  console.log(sum);
}
// 调用
getSum();
```

## (5) 函数的参数

**形参和实参**

1. 形式参数：在声明一个函数的时候，为了函数的功能更加灵活，有些值是固定不了的，对于这些固定不了的值。我们可以给函数设置参数。这个参数没有具体的值，仅仅起到一个占位置的作用，我们通常称之为形式参数，也叫形参
2. 实际参数：如果函数在声明时，设置了形参，那么在函数调用的时候就需要传入对应的参数，我们把传入的参数叫做实际参数，也叫实参。

```js
var x = 5,
  y = 6;
fn(x, y);
function fn(a, b) {
  console.log(a + b);
}
//x,y实参，有具体的值。函数执行的时候会把x,y复制一份给函数内部的a和b，函数内部的值是复制的新值，无法修改外部的x,y
// 不传值为 undefined;
```

## (6) 函数的返回值

```js
// 函数通过return返回一个返回值
function re(e) {
  return e;
}
console.log(re(1));

// 返回值总结
// 1.如果函数没有使用 return语句 ，那么函数有默认的返回值：undefined
// 2.如果函数使用 return语句，那么跟再 return 后面的值，就成了函数的返回值
// 3.如果函数使用 return语句，但是return后面没有任何值，那么函数的返回值也是：undefined
// 4.函数使用 return 语句后，这个函数会在执行完 return 语句之后停止并立即退出，也就是说 return 后面的所有其他代码都不会再执行
// 推荐的做法是要么让函数始终都返回一个值，要么永远都不要返回值

// 求阶乘
function jieCh(n) {
  var j = 1;
  if (n == 0) {
    return 1;
  } else {
    for (i = 1; i <= n; i++) {
      j *= i;
    }
    return j;
  }
}
console.log(jieCh(4));
```

## 函数案例

```js
// 求 1-n 之间所有的和
function sumN(n) {
  sum = 0;
  for (var i = 1; i <= n; i++) {
    sum += i;
  }
  console.log(sum);
}
sumN(3);

// 圆的面积
// toFixed : 四舍五入,指定小数位数
function circle(r) {
  console.log((Math.PI * r * r).toFixed(2));
}
circle(1);

// 求俩数中的最大值
function getMaxNum(numA, numB) {
  if (numA > numB) {
    console.log("最大值 : " + numA);
  } else if (numA < numB) {
    console.log("最大值 : " + numB);
  } else {
    console.log(numA + "=" + numB);
  }
}
getMaxNum(2, 3);
getMaxNum(2, 2);

// 求三个数的最大值
function getMaxNumInThreeNum(numX, numY, numZ) {
  if (numX == numY) {
    if (numX == numZ) {
      console.log("三者相等");
    } else if (numX > numZ) {
      console.log("最大值 ：" + numX);
      // 或者: console.log("最大值 ：" + numY);
    } else {
      console.log("最大值 : " + numZ);
    }
  } else if (numX > numY) {
    if (numX > numZ) {
      console.log("最大值 : " + numX);
    } else {
      console.log("最大值 : " + numZ);
    }
  } else {
    if (numY > numZ) {
      console.log("最大值 ：" + numY);
    } else {
      console.log("最大值 ：" + numZ);
    }
  }
}
getMaxNumInThreeNum(2, 2, 1);

// 判断一个数是否为素数
function isPrime(n) {
  if (n == 0 || n == 1) {
    console.log(n + " 是素数");
  } else if (n == 2) {
    console.log(n + " 不是素数");
  } else {
    for (var i = 2; i < n; i++) {
      if (n % i != 0) {
        console.log(n + " 是素数");
        break;
      } else {
        console.log(n + " 不是素数");
        break;
      }
    }
  }
}
isPrime(4);
```

## 作业

```js
// 作业1：
// 数组去重，返回一个新数组
var arr1 = [2, 4, 4, 5, 5, 7, 8, 9];
function duplicateRemoval(arr) {
  var newArr = [];
  for (var i = 0; i < arr.length; i++) {
    if (newArr.indexOf(arr[i]) == -1) {
      newArr.push(arr[i]);
    }
  }
  return newArr;
}

console.log(duplicateRemoval(arr1));

// 作业2：
// 将数组[10,1,35,61,89,36,55]冒泡排序，从小到大
var arr2 = [10, 1, 35, 61, 89, 36, 55];
for (var i = 0; i < arr2.length - 1; i++) {
  for (var j = 0; j < arr2.length - 1 - i; j++) {
    if (arr2[j] > arr2[j + 1]) {
      var temp = arr2[j];
      arr2[j] = arr2[j + 1];
      arr2[j + 1] = temp;
    }
  }
}
console.log(arr2);

// 作业3：
// 求1!+2!+3!+....+n!
function sumJieCh(n) {
  var sumJie = 0;
  // n 轮
  for (var i = 1; i <= n; i++) {
    // 每轮从 1 开始累乘
    jie = 1;
    for (var j = 1; j <= i; j++) {
      jie *= j;
    }
    sumJie += jie;
  }
  return sumJie;
}
console.log(sumJieCh(1), sumJieCh(2), sumJieCh(3), sumJieCh(4));

// 作业4：
// 输入一个年份，判断是否是闰年[闰年：能被4整数并且不能被100整数，或者能被400整数]
function isLeapYear() {
  var year = prompt("请输入年份");
  if (year % 4 == 0 && year % 100 != 0) {
    console.log(year + " 是闰年");
  } else if (year % 400 == 0) {
    console.log(year + " 是世纪闰年");
  } else {
    console.log(year + " 不是闰年");
  }
}
isLeapYear();

// 作业5：
// 输入某年某月某日，判断这一天是这一年的第几天？（不用做）
// 😁

// 作业6：
// 利用函数的返回值，求1+2+3+4+………+n
function sum(n) {
  var result = 0;
  for (var i = 1; i <= n; i++) {
    result += i;
  }
  return result;
}
console.log(sum(3));

// 作业7：
// 斐波那契数列函数
function fibonacci(n) {
  var f = [1, 1];
  for (var i = 0; i < n - 2; i++) {
    f.push(f[i] + f[i + 1]);
  }
  return f;
}
console.log(fibonacci(5));
```

## 冒泡排序

```js
// 冒泡排序
// 从小到大
var arr1 = [2, 1, 6, 0, 3, 8, 4, 5, 9, 7];
// 第一层 for 循环是比较多少轮
for (var i = 0; i < arr1.length - 1; i++) {
  // 第二层 for 循环是每轮比较多少次,递减
  for (var j = 0; j < arr1.length - 1 - i; j++) {
    if (arr1[j] > arr1[j + 1]) {
      var temp = arr1[j + 1];
      arr1[j + 1] = arr1[j];
      arr1[j] = temp;
    }
  }
}
console.log(arr1);

// 从大到小
// 俩数判断后交换顺序改一下就行
var arr2 = [2, 1, 6, 0, 3, 8, 4, 5, 9, 7];
for (var i = 0; i < arr2.length - 1; i++) {
  for (var j = 0; j < arr2.length - 1 - i; j++) {
    if (arr2[j] < arr2[j + 1]) {
      var temp = arr2[j + 1];
      arr2[j + 1] = arr2[j];
      arr2[j] = temp;
    }
  }
}
console.log(arr2);
```

<!-- -------------------------------- -->

# 八. 预解析

`JavaScript` 引擎在对 `JavaScript` 代码进行解释执行之前，会对 `JavaScript` 代码进行预解析，在预解析阶段，会将以关键字 `var` 和 `function` 开头的语句块提前进行处理。
当变量和函数的声明处在作用域比较靠后的位置的时候，变量和函数的声明会被提升到作用域的开头。

## (1) 函数提升

```js
func();
function func() {
  alert("fun");
}
// 由于 JavaScript 的预解析机制，上面的代码就等效于：
function func() {
  alert("fun");
}
func();
```

## (2) 变量提升

```js
// 变量声明被提升,赋值并没有提升
console.log(e); // undefined
var e = 1;
// 相当于
var e;
console.log(e);
e = 1;
```

## (3) 函数同名

```js
func1();
function func1() {
  console.log("func1");
}
func1();
function func1() {
  console.log("func2");
}
// 由于预解析机制，func1的声明会被提升，提升之后的代码为
function func1() {
  console.log("func2");
}
func1();
func1();
// 同名的函数，后面的会覆盖前面的，所以两次输出结果都是 func2
```

## (4) 变量和函数同名

```js
console.log(f);
var f = 1;
function f() {}
// 当出现变量声明和函数同名的时候，只会对函数声明进行提升，变量会被忽略。所以上面的代码的输出结果为
// ƒ f() {}
```

```js
var num = 1;
function num() {
  alert(num);
}
num(); // num is not a function

// 当变量和函数同名时,只会对函数声明进行提升，变量会被忽略。

// 同名的变量和函数，变量会覆盖函数，导致函数无法调用

// 通俗来讲就是只要出现同名的函数和变量，优先对函数进行提升。但没用，变量会覆盖函数，最终只有变量声明语句生效

// 按照常规的书写顺序，同名的函数与变量，变量会覆盖函数
```

## 练习

```js
// 先提升
// 再看顺序
// 1
function test(a, b) {
  console.log(a);
  var a = 3;
  console.log(b);
  var b = 2;
  function b() {}
  console.log(b);
}
test(1);
// 变量提升后的顺序:
function test(a, b) {
  var a;
  function b() {}
  var b;
  console.log(a);
  a = 3;
  console.log(b);
  b = 2;
  console.log(b);
}
test(1);
// 所以结果为
// 1
// ƒ b() {}
// 2

// 2
function test() {
  console.log(a);
  console.log(b);
  var b = 234;
  console.log(b);
  a = 123;
  console.log(a);
  function a() {}
  var a;
  b = 234;
  var b = function () {};
  console.log(a);
  console.log(b);
}
test();
// 变量提升后的顺序:
function test() {
  var b;
  function a() {}
  var a;
  console.log(a);
  console.log(b);
  b = 234;
  console.log(b);
  a = 123;
  console.log(a);
  b = 234;
  var b = function () {};
  console.log(a);
  console.log(b);
}
test();
// 所以结果为:
// ƒ a() {}
// undefined
// 234
// 123
// 123
// ƒ () {}
```

## (5) 预解析是分作用域的

```js
function m() {
  var m = "m";
}
console.log(m); // m 未定义
// 解析后的代码:
function m() {
  var m;
  m = "m";
}
console.log(m); // m 未定义
```

## (6) 函数表达式不会提升

```js
fun1();
var fun1 = function () {
  console.log("666");
};
// 结果是 : func1 is not a function，原因就是函数表达式，并不会被提升。只是简单地当做变量声明进行了处理，如下
var fun1;
fun1();
fun1 = function () {
  console.log("666");
};
```

## (7)作用域

### (1) 全局作用域

直接编写在 `script` 标签之中的 `JS` 代码，都是全局作用域；或者是一个单独的 `JS` 文件中的。
全局作用域在页面打开时创建，页面关闭时销毁；
在全局作用域中有一个全局对象 `window`（代表的是一个浏览器的窗口，由浏览器创建），可以直接使用。
所有创建的变量都会作为 `window` 对象的属性保存。

### (2) 局部作用域 ( 函数作用域 )

在函数内部就是局部作用域，这个代码的名字只在函数的内部起作用

### (3) 隐式全局变量

声明变量使用`var`, 如果不使用 `var` 声明的变量就是全局变量( 禁用 )
因为在任何代码结构中都可以使用该语法. 那么再代码维护的时候会有问题. 所以除非特殊原因不要这么用.

```js
fun2();
console.log(a);
console.log(b);
console.log(c);
function fun2() {
  var a = 1;
  b = 1;
  c = 1;
  console.log(a);
  console.log(b);
  console.log(c);
}
fun2 执行后获得隐式全局变量 `b` 和 `c`
```

# 九. 对象

## (1) 为什么要有对象

```js
function printPerson(name, age, sex....) {}
// 函数的参数如果特别多的话，可以使用对象简化
function printPerson(person) {  
   console.log(person.name);  
}
```

## (2) 什么是对象

现实生活中：万物皆对象，对象是一个具体的事物，一个具体的事物就会有行为和特征。
举例： 一辆车、一部手机、一台电脑、一张桌子
车是一类事物，门口停的那辆车才是对象。特征：红色、四个轮子，行为：驾驶、刹车

## (3) JavaScript 中的对象

JavaScript 的对象是无序属性的集合。
其属性可以包含基本值、对象或函数。对象就是一组没有顺序的值。我们可以把 JavaScript 中的对象想象成键值对，其中值可以是数据和函数。
`Key` = `value`
对象的行为和特征
特征---属性
行为---方法
Tips：
事物的特征在对象中用属性来表示。
事物的行为在对象中用方法来表示。

## (4) 对象创建方式

### 1. 对象字面量

```js
var obj = {
  name: "zs",
  age: 18,
  sex: true
  fun=function(){
    console.log("fun")
  }
};
```

### 2. new Object()创建对象

```js
var person = new Object();
person.name = "lisi";
person.age = 35;
person.job = "codeman";
person.say = function () {
  console.log("Hello");
};
```

### 3. 工厂函数创建对象

```js
function createPerson(name, age, job) {
  var person = new Object();
  person.name = name;
  person.age = age;
  person.job = job;
  person.say = function () {
    console.log("Hello");
  };
  return person;
}
var p1 = createPerson("张三", 22, "actor");
```

### 4. 自定义构造函数

```js
function Person(name, age, job) {
  this.name = name;
  this.age = age;
  this.job = job;
  this.say = function () {
    console.log("Hello");
  };
}
var p1 = new Person("张三", 22, "actor");
```

## (5) 属性和方法

1. 如果一个变量属于一个对象所有，那么该变量就可以称之为该对象的一个属性

2. 如果一个函数属于一个对象所有，那么该函数就可以称之为该对象的一个方法

## (6) new 关键字

构造函数，是一种特殊的函数。主要用来在创建对象时初始化对象，即为对象成员变量赋初始值，总与 new 运算符一起使用在创建对象的语句中。

1. 构造函数用于创建一类对象，首字母要大写。

2. 构造函数要和 `new` 一起使用才有意义。

**`new` 在执行时会做四件事情：**

1、new 会在内存中创建一个新的空对象
2、new 会让 this 指向这个新的对象
3、new 会返回这个新对象

## (7) this

函数内部的 `this` 几个特点：

1. 函数在定义的时候 `this` 是不确定的，只有在调用的时候才可以确定
2. 一般函数直接执行，内部 `this` 指向全局 window
3. 函数作为一个对象的方法，被该对象所调用，那么 `this` 指向的是该对象
4. 构造函数中的 `this` 其实是一个隐式对象，类似一个初始化的模型，所有方法和属性都挂载到了这个隐式对象身上，后续通过 new 关键字来调用，从而实现实例化

## (8) 对象的使用

遍历对象的属性
通过 for..in 语法可以遍历一个对象
删除对象的属性

```js
// 通过 for ... in 遍历对象的属性
var obj1 = {
  name: "man",
  age: 20,
};
for (var key in obj1) {
  console.log(key);
}
// 遍历对象的属性值
for (var key in obj1) {
  console.log(obj1[key]);
}
// 删除对象的属性
delete obj1.name;
```

# 十. JavaScript  错误

## (1) JavaScript `try` 和 `catch`

`try`  语句允许我们定义在执行时进行错误测试的代码块。
`catch`  语句允许我们定义当 `try` 代码块发生错误时，所执行的代码块。
`JavaScript` 语句  `try`  和  `catch`  是成对出现的。

```js
function t() {
  try {
    alertt("666");
  } catch (error) {
    console.log(error.message); // alertt is not defined
  }
}
t();
// catch 块会捕捉到 try 块中的错误，会执行 catch 里的部分
```

## (2) finally 语句

`finally` 语句不论之前的 `try` 和 `catch` 中是否产生异常都会执行该代码块

```js
function t() {
  try {
    alertt("666");
  } catch (error) {
    console.log(error.message); // alertt is not defined
  } finally {
    console.log("finally");
  }
}
t();
```

## (3) Throw 语句

`throw` 语句允许我们创建自定义错误。
正确的技术术语是：创建或抛出异常（exception）。

```js
// 检测输入变量的值。如果值是错误的，会抛出一个异常（错误）。catch 会捕捉到这个错误，并显示一段自定义的错误消息
function myFunction() {
  var x = prompt();
  try {
    if (x == "") throw "值为空";
    if (isNaN(x)) throw "请输入数字";
    x = Number(x);
    if (x < 5) throw "太小";
    if (x > 10) throw "太大";
    else {
      console.log("good");
    }
  } catch (err) {
    console.log(err);
  }
}
myFunction();
```

## 作业

```js
// 作业1;
// 创建一个电脑对象,有颜色,有重量,有品牌,有型号,可以看电影,可以听音乐,可以打游戏,可以敲代码;
var computer = {
  color: "#494f5c",
  weight: "120",
  brand: "Brand",
  model: "model",
  seeMovies: function () {
    console.log("看电影");
  },
  listenMusics: function () {
    console.log("听音乐");
  },
  gaming: function () {
    console.log("打游戏");
  },
  coding: function () {
    console.log("coding");
  },
};
console.log(computer);
computer.gaming();
computer.coding();

// 作业2;
// 创建一个按钮对象, 宽, 高, 背景颜色, 点击行为, 按钮有鼠标进入的行为;
var button = new Object();
button.width = "120px";
button.height = "40px";
button.backgroundColor = "#494f5c";
button.click = function () {
  console.log("click");
};
button.hover = function () {
  console.log("hover");
};
console.log(button);
button.click();
button.hover();

// 作业3;
// 创建一个车的对象, 有重量, 颜色, 牌子, 可以载人, 拉货;
function createCar(weight, color, brand, canBeManned, pickUpTheGoods) {
  var car = new Object();
  car.weight = weight;
  car.color = color;
  car.brand = brand;
  car.canBeManned = function () {
    console.log("可以载人");
  };
  car.pickUpTheGoods = function () {
    console.log("可拉货");
  };
  return car;
}
var car1 = createCar("2000kg", "#494f5c", "brand");
console.log(car1);
car1.canBeManned();

// 作业4;
// 利用对象属性不能重复的特性给数组去重;
var arr = [1, 2, 2, 3, 3, 5, 5, 6, 8, 8, 9, 9];
function duplicateRemoval(arr) {
  var obj = {};
  var newArr = [];
  for (var i = 0; i < arr.length; i++) {
    if (!obj[arr[i]]) {
      newArr.push(arr[i]);
      obj[arr[i]] = true;
    }
  }
  return newArr;
}
console.log(duplicateRemoval(arr));
```

# 十一. js 内置对象

## 1.内置对象

`JavaScript` 中的对象分为 4 种：内置对象、浏览器对象、自定义对象、DOM 对象。
`JavaScript` 提供多个内置对象：Math/Array/Number/String/Boolean ...
对象只是带有属性和方法的特殊数据类型。学习一个内置对象的使用，只要学会其常用的成员的使用(通过查文档学习)。内置对象的方法很多，我们只需要知道内置对象提供的常用方法，使用的时候查询文档。

## 2. Math 对象

`Math` 对象不是构造函数，它具有数学常数和函数的属性和方法，都以静态成员的方式提供。
跟数学相关的运算来找 `Math` 中的成员(求绝对值，取整)。

### (1) 常用属性

```js
Math.PI; // 圆周率
```

### (2) 常用方法

```js
Math.random(); // 生成随机数
Math.floor(); // 向下取整
Math.ceil(); // 向上取整
Math.round(); // 取整，四舍五入
Math.abs(); // 绝对值
Math.max(); // 最大值
Math.min(); // 最小值
Math.sin(); // 正弦
Math.cos(); // 余弦
Math.pow(); // 求指数次幂
Math.sqrt(); // 求平方根
```

## 3. Date 对象

创建 `Date` 实例用来处理日期和时间。`Date` 对象基于 1970 年 1 月 1 日（世界标准时间）起的毫秒数。

### (1) 创建日期对象

`Date()` 是构造函数

```js
var date = new Date(); // 获取到的是 1970 年 1 月 1 日至今的毫秒数
```

### (2) 日期原始值

getTime()：获取 1970 年 1 月 1 日至今的毫秒数
valueOf();原始值，获取 1970 年 1 月 1 日至今的毫秒数

### (3) 获取日期指定部分

```js
getMilliseconds();
getSeconds(); // 返回 0-59
getMinutes(); // 返回 0-59
getHours(); // 返回 0-23
getDay(); // 返回星期几 0 周日   6 周 6
getDate(); // 返回当前月的第几天
getMonth(); // 返回月份，从 0 开始
getFullYear(); //返回 4 位的年份 如 2016
```

## 4. Array 对象

### (1) 创建数组对象的两种方式

1、字面量方式
2、new Array()

### (2) 检测一个对象是否是数组

`instanceof` 如果返回 `true` 就是数组，`false` 是非数组 ( 这玩意儿很少用 )
`Array.isArray()` 如果返回 `true` 就是数组，`false` 是非数组 ( 常用 )
`valueOf()` 返回数组对象本身

### (3) 栈操作 (先进后出)

```js
push(); // 添加元素
pop(); // 删除元素
```

![stack](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/js/stack.png)

### (4) 队列操作 (先进先出)

```js
shift(); // 删除元素
unshift(); // 添加元素
```

### (5) 排序方法

```js
reverse(); // 翻转数组
sort(); // 只看第一位数来排序
```

```js
//   var arr = [1, 2, 3, 4, 9, 8, 7, 6, 5];
var arr1 = [100, 200, 3, 4, 9, 8, 7, 6, 5];
console.log(arr1.sort()); // 然而排序后的结果不是咱想要的
```

**可以这样**

```js
arr1.sort(function (a, b) {
  return a - b; // 从小到大排序
  return b - a; // 从大到小排序
});
```

### (6) 操作方法

#### `concat()` 把参数拼接到当前数组、  或者用于连接两个或多个数组

#### `slice(start,end)`

1、从 `start` 开始截取元素，到 `end` 结束，包括 `start`,不包括 `end`,返回新数组，`start`,`end` 是索引,
2、不会改变原始数组

#### `splice()`

`splice(start,length)`
1、从 `start` 开始截取元素，截取 `length` 个，,`返回新数组，start` 是索引,`length` 是个数, **如果不写`length`参数,会从`start`一直删到最后**
2、会改变元素的数组

### (7) 位置方法

`indexOf()` 寻找元素位置,返回第一次出现的位置的索引值,没有找到返回 -1，
`lastIndexOf()`   从后往前找
上述方法只是查找顺序不一样 结果都是索引值

### (8) 数组迭代方法

1、`forEach()` 方法用于调用数组的每个元素，并将元素传递给回调函数

可以拿到每个数组中的值，没有返回值

```js
array.forEach(function(value, index))
// value 必需,当前元素
// Index 可选,当前元素索引值
```

2、`every()`, `some()` 方法用于检测数组所有元素是否都符合指定条件（通过函数提供）
`some()`,`every()` 方法的参数是一个回调函数，回调函数中的第一个参数是数组的元素，第二个参数是数组的索引
`some()`,`every()` 方法都会返回新的数组

```js
var flag1 = arr3.every(function (value, index) {
  return value > 55;
});
console.log(flag1);
var flag2 = arr3.some(function (value, index) {
  return value >= 88;
});
console.log(flag2);
```

`every()` :判断回调函数中的表达式是否全部满足，如果满足，返回值就是 `true`,只要有一个不满足就是 `false`

`some` 判断回调函数中的表达式是否有一个满足，如果至少一个满足，返回值就是 `true`

### (9) 清空数组

#### 方式 1 推荐

```js
arr = [];
```

#### 方式 2

```js
arr.length = 0;
```

#### 方式 3

```js
arr.splice(0, arr.length);
// 或者,不写 length ,会一直删到最后
arr.splice(0);
```

### (10) 数组转化字符串

`join()` 将数组转化为字符串，以参数分割

```js
var str = "31423412";
console.log(str.split("").join()); // 3,1,4,2,3,4,1,2
console.log(str.split("").join("")); // 31423412
console.log(str.split("").join("-")); // 3-1-4-2-3-4-1-2
```

## 5. 基本包装类型

为了方便操作基本数据类型，`JavaScript` 还提供了三个特殊的引用类型：`String`,`Number`,`Boolean`

```js
// s1是基本类型，基本类型是没有方法来操作的
var s1 = 'zhangsan';
var s2 = s1.substring(5);
​
// 当调用 s1.substring(5) 的时候，先把 s1 包装成 String 类型的临时对象，再调用 substring 方法，最后销毁临时对象, 相当于：
var s1 = new String('zhangsan');
var s2 = s1.substring(5);
s1 = null;
```

```js
// 创建基本包装类型的对象
var num = 18; //数值，基本类型
var num = Number("18"); //类型转换
var num = new Number(18); //基本包装类型，对象
// Number 和 Boolean 基本包装类型基本不用，使用的话可能会引起歧义。例如：
var b1 = new Boolean(false);
var b2 = b1 && true; // 结果是 true, 因为 object && true = true
```

## 6. String 对象

### (1) 字符串的不可变

```js
var str = "abc";
str = "hello";
// 当重新给 str 赋值的时候，常量 'abc'不会被修改，依然在内存中
// 重新给字符串赋值，会重新在内存中开辟空间，这个特点就是字符串的不可变
// 由于字符串的不可变，在大量拼接字符串的时候会有效率问题
```

### (2) 创建字符串对象

```js
var str = new String("Hello World");
// 获取字符串中字符的个数
console.log(str.length);
```

### (3) 字符串对象的常用方法

字符串所有的方法，都不会修改字符串本身(字符串是不可变的)，操作完成会返回一个新的字符串

#### 1. 字符方法

```js
charAt(); //获取指定位置处字符
charCodeAt(); //获取指定位置处字符的 ASCII 码
str[0]; //HTML5，IE8+支持 和 charAt()等效
```

#### 2. 字符串操作方法

```js
concat()   //拼接字符串，等效于+，+更常用
slice(start,end)   //从 start 位置开始，截取到 end 位置，end 取不到
substring(start,end) //从 start 位置开始，截取到 end 位置，end 取不到
substr(start,length)   //// 从 start 位置开始，截取 length 个字符
indexOf()   //返回指定内容在元字符串中的位置,,如果没有，返回-1；(从前往后，检索到第一个就结束)
lastIndexOf() //返回指定内容在元字符串中的位置,,如果没有，返回-1；(从后往前，检索到第一个就结束)
trim() //只能去除字符串前后的空白

// 大小写转换方法
toUpperCase() //转换大写
toLowerCase() //转换小写
search()//方法用于检索字符串中指定的子字符串，返回子字符串的起始位置
replace(old,new) //替换字符串替换字符串 new 替换 old
split() //分割字符串 返回的是一个数组。。数组的元素就是以参数的分割的
```

**演示**

```js
var str = "uy weiu ryqi w-u-q-wey82374192739    ";

console.log(str.charAt(0)); // //获取指定位置处字符

console.log(str.charCodeAt(0)); //获取指定位置处字符的ASCII码

console.log(str[0]); //HTML5，IE8+支持 和charAt()等效

var str2 = "";
str2 = str.concat(str); //拼接字符串，等效于+，+更常用
console.log(str2);

console.log(str.slice(0, 1)); //从start位置开始，截取到end位置，end取不到

console.log(str.slice(2, 4));

console.log(str.substring(2, 4)); //从start位置开始，截取到end位置，end取不到

console.log(str.substr(2, 4)); // 从start位置开始，截取 length 个字符

console.log(str.indexOf("u")); //返回指定内容在元字符串中的位置,,如果没有，返回-1；(从前往后，检索到第一个就结束)

console.log(str.lastIndexOf("u")); //返回指定内容在元字符串中的位置,,如果没有，返回-1；(从后往前，检索到第一个就结束)

console.log(str.trim()); //只能去除字符串前后的空白

// 大小写转换方法
console.log(str.charAt(0).toUpperCase()); //转换大写

console.log(str.charAt(0).toLowerCase()); //转换小写

console.log(str.search("u")); //方法用于检索字符串中指定的子字符串，返回子字符串的起始位置

console.log(str.replace("u", "new")); //替换字符串替换字符串 new替换old

console.log(str.split()); //分割字符串 返回的是一个数组。。数组的元素就是以参数的分割的

console.log(str.split(""));
console.log(str.split(" "));
console.log(str.split("-"));
```

**作业**

```js
//   -------------------------
// Wechat收购 Baidu，电话号码相同的人当作是同一个人，合并后salary相加，其他属性保留Wechat的数据，新的Baidu的员工重新生成id,salary涨幅20%
// 统计收购后的员工平均工资，最高工资，最低工资，male的平均工资，female的平均工资
// 找出收购后工资高于8000的员工姓名和电话号码，按薪水从高到低排序
// 找出收购前后工资涨幅最高的员工姓名和电话号码，以及涨幅的百分比
// 找出收购后重名最多的三个姓名，统一出他们的平均年龄
var BaiduUsers = [],
  WechatUsers = [];
var User = function (id, name, phone, gender, age, salary) {
  this.id = id;
  this.name = name;
  this.phone = phone;
  this.gender = gender;
  this.age = age;
  this.salary = salary;
};
User.create = function (id, name, phone, gender, age, salary) {
  return new User(id, name, phone, gender, age, salary);
};
BaiduUsers.push(User.create(1, "tommy", "1111", "male", 18, 10000));
BaiduUsers.push(User.create(2, "jerry", "2222", "male", 28, 10000));
BaiduUsers.push(User.create(3, "raobin", "3333", "female", 14, 1200));
BaiduUsers.push(User.create(4, "binbin", "4444", "male", 23, 9800));
BaiduUsers.push(User.create(5, "arthur", "5555", "female", 22, 10000));
//
WechatUsers.push(User.create(1, "tommy", "1111", "male", 20, 40000));
WechatUsers.push(User.create(2, "allen", "6666", "male", 34, 15800));
WechatUsers.push(User.create(3, "raobin", "3333", "female", 16, 2300));
WechatUsers.push(User.create(4, "harvey", "7777", "male", 30, 29800));
WechatUsers.push(User.create(5, "yuyu", "8888", "female", 27, 7000));

// 电话号码相同的人当作是同一个人，合并后salary相加，其他属性保留Wechat的数据
for (var b = 0; b < BaiduUsers.length; b++) {
  for (var w = 0; w < WechatUsers.length; w++) {
    if (BaiduUsers[b].phone == WechatUsers[w].phone) {
      WechatUsers[w].oldsalary = WechatUsers[w].salary;
      WechatUsers[w].salary = WechatUsers[w].oldsalary + BaiduUsers[b].salary;
      BaiduUsers.splice(b, 1);
    }
  }
}

// 新的Baidu的员工重新生成id,salary涨幅20%
for (var i = 0; i < BaiduUsers.length; i++) {
  BaiduUsers[i].oldsalary = BaiduUsers[i].salary;
  BaiduUsers[i].salary = BaiduUsers[i].salary * 1.2;
  BaiduUsers[i].id = WechatUsers.length + 1 + i;
}

// 所有 weChat 员工
newWechatUsers = WechatUsers.concat(BaiduUsers);

// 统计收购后的员工平均工资，最高工资，最低工资，male的平均工资，female的平均工资
var sumSalary = 0, // 所有员工薪资和
  usersSalary = [], // 所有员工薪资
  averageSalary = 0, // 平均薪资
  max = 0, // 最高薪资
  min = 0, // 最低薪资
  maleSalary = [], // 男员工薪资集合
  femaleSalary = [], // 女员工薪资集合
  sumMaleSalary = 0,
  sumFemaleSalary = 0;
newWechatUsers.forEach(function (user, userIndex) {
  // 把所有员工薪资放到一个新数组里
  usersSalary.push(newWechatUsers[userIndex].salary);

  // 把所有男员工薪资放到一个新数组里
  if (user.gender == "male") {
    maleSalary.push(newWechatUsers[userIndex].salary);
  }

  // 把所有女员工薪资放到一个新数组里
  if (user.gender == "female") {
    femaleSalary.push(newWechatUsers[userIndex].salary);
  }
});

// 所有员工的薪资
usersSalary.forEach(function (userSalary) {
  sumSalary += userSalary;
});

// 平均薪资
averageSalary = sumSalary / newWechatUsers.length;
console.log(averageSalary);

// 最高工资，最低工资
max = usersSalary[0];
min = usersSalary[0];
usersSalary.forEach(function (value) {
  if (max < value) {
    max = value;
  }
  if (min > value) {
    min = value;
  }
});
console.log(max, min);

// male的平均工资
for (var i = 0; i < maleSalary.length; i++) {
  sumMaleSalary += maleSalary[i];
}
console.log(sumMaleSalary / maleSalary.length);

// female的平均工资
for (var i = 0; i < femaleSalary.length; i++) {
  sumFemaleSalary += femaleSalary[i];
}
console.log(sumFemaleSalary / femaleSalary.length);

// 找出收购后工资高于8000的员工姓名和电话号码，按薪水从高到低排序

// 先把整体重新排序
newWechatUsers.sort(function (a, b) {
  return b["salary"] - a["salary"];
});

var more8000 = [];

function UserList(name, phone) {
  this.name = name;
  this.phone = phone;
  return { name, phone };
}
for (var i = 0; i < newWechatUsers.length; i++) {
  if (newWechatUsers[i].salary > 8000) {
    more8000.push(UserList(newWechatUsers[i].name, newWechatUsers[i].phone));
  }
}

// 找出收购前后工资涨幅最高的员工姓名和电话号码，以及涨幅的百分比
for (var i = 0; i < newWechatUsers.length; i++) {
  if (newWechatUsers[i].oldsalary != undefined) {
    newWechatUsers[i].riseSalary =
      newWechatUsers[i].salary - newWechatUsers[i].oldsalary;
    newWechatUsers[i].percentRise =
      (newWechatUsers[i].riseSalary / newWechatUsers[i].oldsalary) * 100;
  }
  // 因为有的员工薪资没有合并，也没有涨薪，所以 oldsalary 会是 undefined
  else {
    newWechatUsers.splice(i, 1);
  }
}

newWechatUsers.sort(function (a, b) {
  return b["percentRise"] - a["percentRise"];
});
console.log(
  newWechatUsers[0].name,
  newWechatUsers[0].phone,
  "涨幅百分比 :" + newWechatUsers[0].percentRise + "%"
);

console.log("-------------------------------------");

var str = "abaasdffggghhjjkkgfddsssss3444343";

// 1、 字符串的长度
console.log(str.length);

// 2、 取出指定位置的字符，如：0,3,5,9等
console.log(str.slice(0, 1));
console.log(str.slice(2, 3));
console.log(str.slice(4, 5));
console.log(str.slice(8, 9));

// 3、 查找指定字符是否在以上字符串中存在，如：i，c ，b等
function searchStr(string, element) {
  if (string.search(element) == -1) {
    console.log("没找到");
  } else {
    console.log("存在");
  }
}
searchStr(str, "i");
searchStr(str, "c");
searchStr(str, "b");

// 4、 替换指定的字符，如：g替换为22,ss替换为b等操作方法
var str2 = str;
do {
  str2 = str2.replace("g", 22);
} while (str2.search("g") != -1);
console.log(str2);

var str3 = str;
do {
  str3 = str3.replace("ss", "b");
} while (str3.search("ss") != -1);
console.log(str3);

// 5、 截取指定开始位置到结束位置的字符串，如：取得1-5的字符串
console.log(str.substring(0, 5));

// 6、 找出以上字符串中出现次数最多的字符和出现的次数
var obj = {},
  count = 0,
  s = "";
for (var i = 0; i < str.split("").length; i++) {
  // 如果不存在,记录一次
  if (!obj[str.charAt(i)]) {
    obj[str.charAt(i)] = 1;
  }
  // 如果存在，则 +1
  else {
    obj[str.charAt(i)]++;
  }
}

for (var key in obj) {
  if (obj[key] > count) {
    count = obj[key];
    s = key;
  }
}
console.log("出现次数最多的字符 : " + s + " ; " + "次数 : " + count);

// 7、 遍历字符串，并将遍历出的字符两头添加符号“@”输出至当前的文档页面
str.split("").forEach(function (value, index) {
  document.write("@" + value + "@");
  document.write("<br />");
});
```

# The_End
