---
title: Ts 学习总结
date: 2021-11-08 22:57:57
updated:
tags:
  - TypeScript
categories:
  - TypeScript
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

# 基本数据类型

## boolean 类型

使用`boolean` 声明布尔值

```ts
let finished: boolean = false;
```

如果用构造函数 `Boolean()` 创造的对象不是布尔值，而是一个 `Boolean` 对象，会报错

```ts
let finished: boolean = new Boolean(false);

// 报错：'boolean' is a primitive, but 'Boolean' is a wrapper object
```

## number 类型

使用 `number` 来声明数字类型

```ts
let num: number = 12; // ES6中十进制表示法
let xnum: number = 0xf; // ES6中16进制表示法
let bnum: number = 0b1010; // ES6中二进制表示法
let onum: number = 0o744; // ES6中8进制表示法
let notANumber: number = NaN;
let infinityNumber: number = Infinity;
```

编译结果：

```ts
let num: number = 12; // ES6中十进制表示法
let xnum: number = 0xf; // ES6中16进制表示法
let bnum: number = 10; // ES6中二进制表示法
let onum: number = 484; // ES6中8进制表示法
let notANumber: number = NaN;
let infinityNumber: number = Infinity;
```

**其中二进制和八进制会被编译为十进制**

## string 类型

使用 `string` 来声明字符串类型

```ts
let name: string = "TypeScript";
```

## void 类型

这个 `void` 在 `js` 里没有，在 `ts` 里表示没有任何返回值的函数:

```ts
function hello(): void {
	alert("hello");
}
```

**实则发现声明一个 `void` 类型的变量我感觉没啥用，只能赋值为 `undefined`：**

```ts
let nothing: void = undefined;
```

## null 和 undefined

声明方式

```ts
let u: undefined = undefined;
let n: null = null;
```

这俩貌似也没啥用，和 `void` 的区别就是 `undefined` 和 `null` 都是所有类型的子类型，也就是 `undefined` 的类型的变量可以赋值给比如 `number` 类型

```ts
let u: undefined = undefined;

// 下面这两种方式都不会报错
let num: number = u;
let unum: number = undefined;
```

`void` 类型试了不行

```ts
let u: void;
let num: number = u;

// 报错：Type 'void' is not assignable to type 'number'.
```

# 任意值 Any

如果是一个基本数据类型，在赋值过程中改变类型是不被允许

```ts
let str: string = "seven";
str = 7;

// 报错：Type 'number' is not assignable to type 'string'.
```

如果是 `any` 类型是允许被赋值任意类型的

```ts
let str: any = "seven";
str = 7;
```

如果在声明变量的时候，未指定其类型，那么它会被识别为任意值类型

# 类型推断

也就是如果没有明确的声明变量的类型，那么 `ts` 就会推断出一个类型

```ts
let code = "js";
code = 2;

// 报错：Type 'number' is not assignable to type 'string'
```

如果定义的时候没有赋值，不管之后有没有赋值，都会被推断成 `any` 类型，也就是不会被类型检查：

```ts
// 这样没问题
let number;
number = "seven";
number = 7;
```

# 联合类型 Union Types

取值可以为多种类型中的一种

```ts
let code: string | number;
code = "ts";
code = 123;
```

如果赋值的类型不是声明的那几种类型，就报错了

```ts
let code: string | number;
code = true;

// 报错 Type 'boolean' is not assignable to type 'string | number'
```

如果访问联合类型的属性的时候，因为 `ts` 也不确定变量类型，所以是能访问共有的属性或方法

```ts
// 因为length不是string和number的共有属性，所以下边这个例子就报错了
function getLength(something: string | number): number {
	return something.length;
}
```

换成共有的属性或方法就可以了，比如 `.toString()`

```ts
function getLength(something: string | number): string {
	return something.toString();
}
```

在给联合类型赋值的时候 `ts` 会推断出一个类型

```ts
let tom: string | number;
tom = "brother";
console.log(tom.length); // 7

tom = 123;
console.log(tom.length); // 报错：Property 'length' does not exist on type 'number'
```

第一次赋值 "tom" 被推断成了 `string` 类型，访问 `length` 属性是没问题的
第二次赋值 "tom" 被推断成了 `snumber` 类型，`number` 类型没有 `length` 属性，所以就报错了

# 对象类型

用接口 `interface` 来定义对象类型

```ts
interface Persion {
	name: string;
	age: number;
}

let tom: Persion = {
	name: "Tom",
	age: 20,
};
```

接口一般首字母大写，我印象中有的编程语言中会建议接口的名称加上 `I` 前缀

定义的变量比接口少一些属性是不允许的

```ts
interface Person {
	name: string;
	age: number;
}

let tom: Person = {
	name: "Tom",
};

// 报错：Property 'age' is missing in type '{ name: string; }' but required in type 'Persion'
```

多一些属性也是不允许的

```ts
interface Person {
	name: string;
	age: number;
}

let tom: Person = {
	name: "Tom",
	age: 25,
	gender: "male",
};

// 报错：Type '{ name: string; age: number; gender: string; }' is not assignable to type 'Person'.
  Object literal may only specify known properties, and 'gender' does not exist in type 'Person'
```

## 可选属性

如果不希望完全匹配，可以设置可选属性，属性后面加个问号，这时仍然不允许添加未定义的属性

```ts
interface Person {
	name: string;
	age?: number;
}

let tom: Person = {
	name: "Tom",
};
```

## 任意属性

有时候希望一个接口允许有任意的属性，可以使用如下方式
使用 `[propName: string]` 定义了任意属性取 string 类型的值

```ts
interface Person {
	name: string;
	age?: number;
	[propName: string]: any;
}

let tom: Person = {
	name: "Tom",
	gender: "male",
};
```

而且一旦定义了任意属性，那么确定属性和可选属性的类型都必须是它的类型的子集：

```ts
interface Person {
	name: string;
	age?: number;
	[propName: string]: string | number;
}

let tom: Person = {
	name: "Tom",
	age: 25,
	gender: "male",
};
```

## 只读属性

如果希望对象中的一些字段只能在创建的时候被赋值，那么可以用 `readonly` 定义只读属性：

```ts
interface Person {
	readonly id: number;
	name: string;
	age?: number;
	[propName: string]: any;
}

let tom: Person = {
	id: 89757,
	name: "Tom",
	gender: "male",
};

tom.id = 9527;

// Cannot assign to 'id' because it is a read-only property
```

**只读的约束存在于第一次给对象赋值的时候，而不是第一次给只读属性赋值的时候，举个例子：**

```ts
interface Person {
	readonly id: number;
	name: string;
	age?: number;
	[propName: string]: any;
}

let tom: Person = {
	name: "Tom",
	gender: "male",
};

tom.id = 89757;

// 这里就有两个错了，第一次给对象赋值的时候缺少了id属性，第二次赋值的时候赋给了只读属性
```

# 数组类型

最简单的数组表示方式是：

```ts
let arr: number[] = [1, 2, 3, 4, 5];
```

数组中的项不允许出现其他类型：

```ts
let arr: number[] = [1, 2, "3", 4, 5];

// Type 'string' is not assignable to type 'number'
```

很容易理解这样在数组定义的时候就限制了一些方法的参数：

```ts
let arr: number[] = [1, 2, 3, 4, 5];
arr.push("6");

// Argument of type 'string' is not assignable to parameter of type 'number'
```

## 数组泛型

用数组泛型 `Array<elemType>` 来表示数组：

```ts
let arr: Array<number> = [1, 2, 3, 4, 5];
```

接口也可以用来描述数组，我感觉描述很清晰，就是略显复杂：

```ts
interface numberArray {
	[index: number]: number;
}
let arr: numberArray = [1, 2, 3, 4, 5];
```

## 类数组

类数组就是伪数组，比如 `arguments`

```ts
function sum() {
	let args: number[] = arguments;
}
// Type 'IArguments' is missing the following properties from type 'number[]': pop, push, concat, join, and 24 more
```

`arguments` 实际上是一个伪数组，不能用普通的数组的方式来描述，而应该用接口

```ts
function sum() {
	let args: {
		[index: number]: any;
		length: number;
		callee: Function;
	} = arguments;
}
```

常用的类数组都有自己的接口定义，如 `IArguments`, `NodeList`, `HTMLCollection` 等：

```ts
function sum() {
	let args: IArguments = arguments;
}
```

其中 `IArguments` 是 `TypeScript` 中定义好了的类型，实际上就是：

```ts
interface IArguments {
	[index: number]: any;
	length: number;
	callee: Function;
}
```

## any 在数组里的应用

用 `any` 表示数组中允许出现任意类型

```ts
let list: any[] = ["codehhr", "web", 22, { blog: "codehhr.cn" }];
```

# 函数类型

`js` 中可以声明函数或者用表达式的形式，`ts` 要考虑输入输出个数：

```ts
function sum(x: number, y: number): number {
	return x + y;
}
```

如果我执行的时候输入了多余或者少参数，也不行

```ts
sum(1, 2, 3); // Expected 2 arguments, but got 3
sum(1); // Expected 2 arguments, but got 1
```

我感觉这就挺好，增强了程序的健壮性，即使报错也可以很快定位

## 函数表达式

开始我以为 `ts` 里函数表达式是这样的：

```ts
let sum: number = function (x: number, x: number): number {
	return x + y;
};

// 或者箭头函数的形式：

let sum: number = (x: number, x: number): number => {
	return x + y;
};
```

实际上发现在 `ES6` 里 `=>` 表示箭头函数，在 `ts` 里左边是输入类型，得用小括号括起来，右边是输出类型：

```ts
let sum: (x: number, y: number) => number = function (x: number, y: number): number {
	return x + y;
};
```

感觉虽然比 `js` 麻烦太多了，但是由牺牲的自由换来了稳定

## 用 interface 来描述函数

```ts
interface fun {
	(str1: string, str2: string): boolean;
}

let hadFinished: fun = function (str1: string, str2: string) {
	return str1 == str2;
};
```

## 可选参数

之前在对象里用 `?` 来指定可选参数，我寻思这函数里的参数是不是也这样，果然就是这样

```ts
function getName(firstName: string, lastName?: string): string {
	if (lastName) {
		return `${firstName} ${lastName}`;
	} else {
		return firstName;
	}
}

getName("H"); // H
getName("H", "HR"); // H HR
```

但是有一点限制，可选参数后面不能出现必须参数了，也就是可选参数不能放到前面，例子就不敲了，容易误导自己 🤣

## 参数默认值

`ts` 会将有默认值的参数识别为可选参数，这就很合理

```ts
function getName(lastName: string = "HR", firstName: string = "H"): string {
	return `${firstName} ${lastName}`;
}
```

## 拓展运算符

因为推展运算符的应用类型是数组，所以用数组来标注数据类型

```ts
function pushArr(array: any[], ...items: any[]) {
	items.forEach(function (item) {
		array.push(item);
	});
}

let a = [];
pushArr(a, 1, 2, 3);
```

## 重载

重载允许一个函数接受不同数量或类型的参数时，作出不同的处理
比如，我们需要实现一个函数 `reverse`，输入数字 `123` 的时候，输出反转的数字 `321`，输入字符串 `'hello'` 的时候，输出反转的字符串 `'olleh'`。

利用联合类型，可以这么实现：

```ts
function reverseSth(x: number | string): number | string | void {
	if (typeof x === "number") {
		return Number(x.toString().split("").reverse().join(""));
	} else if (typeof x === "string") {
		return x.split("").reverse().join("");
	}
}
```

但是这样就太麻烦了，而且类型都写死了，不够通用
可以用重载来定义多个 `reverseSth` 函数类型

```ts
function reverseSth(x: number): number;
function reverseSth(x: string): string;
function reverseSth(x: number | string): number | string | void {
	if (typeof x === "number") {
		return Number(x.toString().split("").reverse().join(""));
	} else if (typeof x === "string") {
		return x.split("").reverse().join("");
	}
}
```

实则这样看起来更麻烦了 😂
这次重复定义了多次函数 `reverseSth`，前几次都是函数定义，最后一次是函数实现，在 `vscode` 中会提示 `+1 overload`

而且 `TypeScript` 会优先从最前面的函数定义开始匹配，所以多个函数定义如果有包含关系，需要优先把精确的定义写在前面

# 类型断言

```ts
值 as 类型;

// 或者

<类型>值;
```

# 未完待续 ...
