---
title: ES6 新增用法 ( 三 )
date: 2021-06-23 21:57:46
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/sunrise.jpg
cover:
tags:
  - js
  - javascript
  - ES6
categories:
  - js
  - ES6
comments:
---

# ES6 中数值的用法

## isNaN( )

`isNaN` 函数 : 用于判断传入的是否是非数值  
**注意** : 是判断非数值 , 而不是判断数值 , `isNaN` 的全称是： is not a number

**传统写法**

```js
console.log(isNaN(2.5)); // false
console.log(isNaN("2.5")); // false,会隐式类型转化为 Number 类型
console.log(isNaN("abc")); // true,转换为 Number 后是一个非数值 (NaN)
console.log(isNaN(NaN)); // true
```

`isNaN` 是全局函数 , 本身就是属于 `window` 对象下的一个方法 , 在 `ES6` 的标准中 , `isNaN` 方法被移植到了 `Number` 对象上 , 也就是原本属于全局对象 `window` 下的函数 , 现在属于 `Number` 对象上了

**ES6 用法**

```js
console.log(Number.isNaN(2.5)); // false
console.log(Number.isNaN("abc")); // false,不做类型转换,是字符串,直接返回 false
console.log(Number.isNaN("2.5")); // false,也不会隐式类型转换,即还是字符串,返回 false
console.log(Number.isNaN(NaN)); // true
```

## Number.isFinite( )

`Number.isFinite` 函数 : 用来检查一个数值是否非无穷 ( 有穷的 , 有限的 )

```js
console.log(Number.isFinite(10)); // true
console.log(Number.isFinite("10")); // false,字符串也会返回 false
console.log(Number.isFinite(Infinity)); // false
```

## Number.parseInt( )

`parseInt` 函数 : 解析一个字符串 , 返回一个整数. `parseInt` 函数同样是从 `window` 对象下移植到 `Number` 对象下 , 但是它的作用没有任何变化

```js
console.log(Number.parseInt(2.3)); // 2
console.log(Number.parseInt(2.7)); // 2
```

## Number.isInteger( )

`Number.isInteger` 函数 : 用来判断是否是整数

```js
console.log(Number.isInteger(1)); // true
console.log(Number.isInteger(1.0)); // true
console.log(Number.isInteger(1.1)); // false
console.log(Number.isInteger("1.0")); // false
console.log(Number.isInteger("1.a")); // false
```

## Math.trunc( )

`Math.trunc` 函数 : 用于去除一个数的小数部分 , 返回整数部分。

```js
console.log(Math.trunc(2.1)); // 2
console.log(Math.trunc(2.8)); // 2
```

## Math.sign( )

`Math.sign` 函数 : 用来判断一个数到底是正数 , 负数 , 还是零
参数如果是正数 , 结果返回 `1` ; 如果是负数 , 结果返回 `-1` ; 如果是 0 , 结果返回 `0` ; 如果是一个非数值类型的参数 , 结果返回 `NaN`

```js
console.log(Math.sign(2)); // 1
console.log(Math.sign(0)); // 0
console.log(Math.sign(-20)); // -1
console.log(Math.sign("-20")); // -1
console.log(Math.sign("asd")); // NaN
```

# ES6 中对象的使用

## 对象的写法

**传统写法**

```js
// 传统方式
let name = "张三";
let age = 20;
let person = {
  name: "张三",
  // name: name,
  age: 20,
  // age: age,
  say: function () {
    console.log("Hello");
  },
};
```

**ES6 写法**

```js
// ES6
let name = "李四";
let age = 20;
let person2 = {
  name,
  age,
  say() {
    console.log("Shit bro ~");
  },
};
```

## ES6 中属性名的更新

用字面量定义一个对象的时候 ,可以用表达式作为对象的属性名或者方法名

```js
let h = "hello";
let w = "world";
let f = "first";
let l = "name";
let person3 = {
  [f + l]: "FirstName",
  [h + w]() {
    console.log("Hello World");
  },
};
console.log(person3.firstname); // FirstName
person3.helloworld(); // Hello World
```

## Object.is( )

`Object.is` 函数的作用 : 比较两个值是否严格相等 , 或者说全等 , 即 `===`

```js
// ===
let str = "12";
let num = 12;
console.log(str == num); // true
console.log(str === num); // false

// ES6
console.log(Object.is(str, num)); // false
```

## Object.assign( )

`Object.assign` 函数作用 : 将新对象的属性赋值到原对象上 , 后面的属性值会覆盖前面的属性值

```js
let before = {
  a: 1,
};
let after1 = {
  b: 2,
};
let after2 = {
  c: 3,
};
let after3 = {
  a: 22,
  b: 33,
  c: 44,
};
Object.assign(before, after1, after2, after3);
console.log(before); // {a: 22, b: 33, c: 44}
```

## Object.getPrototypeOf( )

`Object.getPrototypeOf` 函数作用 : 获取一个对象的 `prototype` 属性

```js
// 构造函数
function Person(name) {
  this.name = name;
}
// 在 prototype 上添加方法
Person.prototype.say = function () {
  console.log("Awesome man");
};
// 实例一个新对象
let tom = new Person();
tom.say(); // 成功打印 Awesome man , 添加成功!;
console.log(Object.getPrototypeOf(tom)); // 打印 prototype 里的内容
```

## Object.setPrototypeOf( )

`Object.setPrototypeOf` 函数作用 : 设置一个对象的 `prototype` 属性

```js
Object.setPrototypeOf(tom, {
  hello() {
    console.log("Hello");
  },
});
tom.hello(); // Hello
```

# ES6 中函数的使用

## 参数的默认值

**传统方式**

```js
function person(name, age) {
  name = name || "张三";
  age = age || 20;
}
```

**ES6 写法**

```js
function person(name = "张三", age = 20) {
  //
}
```

如果函数有多个参数 , 但只有部分需要指定默认值 , 另一部分不需要的话 , 那么 , 设定默认值的参数一定要放在最后

```js
// 错误示范
function person(age = 20, name) {
  console.log(name, age);
}
// 正确写法
function person(name, age = 20) {
  console.log(name, age);
}
```

另外 , 只有当传入的参数为 `undefined` , 才会触发默认值赋值。否则 , 哪怕你传的参数值为 `0` , `false` , `null` 都不会触发默认值赋值 , 这就完美的解决了传统实现方式的弊端

```js
function getAge(age = 20) {
  console.log(age);
}
getAge(); // 20
getAge(undefined); // 20
getAge(0); // 0
getAge(null); // null
```

还有一个要注意的地方 , 函数的参数是默认声明的 , 声明过的变量 , 就不能用 `let` 或者 `const` 关键字再次声明 , 否则会报错

```js
function person(age) {
  let age = 20;
  // 错误 :不能再次声明
  // Uncaught SyntaxError: Identifier 'age' has already been declared
}
```

## rest 函数

**案例**

`rest` 参数 , 它代表的意思是 : 在实参中 , 除了第一个参数以外 , 剩余的参数都会被 `...rest` 获取到 , 当然 `...rest` 是形参 , 也可以是别的名字 , 比如 `...value`

```js
let result = 0;
function sum(result, ...rest) {
  rest.forEach(function (value) {
    result += value;
  });
  return result;
}
console.log(sum(result, 1, 2, 3));
```

**`...rest` 必须放到参数最后**

```js
// 错误示范
// Uncaught SyntaxError: Rest parameter must be last formal parameter
function sum(...rest,a,b,c){
    //
}
```

## 扩展运算符

扩展运算符 `...` 的作用 : 它可以将一个数组转成一个对应的参数数列表

```js
let arr = [1, 2, 3];
function sum(a, b, c) {
  return a + b + c;
}
console.log(sum(...arr));
```

## 箭头函数

```js
// 传统写法
function sumA(a, b) {
  return a + b;
}

// ES6
// 如果函数题单是返回一个东西 , return 也可以省略
let sumB = (a, b) => a + b;

let sumC = (a, b) => {
  let c = a + b;
  return c;
};
```

```js
// 传统写法
let sum = 0;
[1, 2, 3].forEach(function (v) {
  sum += v;
});
console.log(sum);

// ES6
let sum = 0;
[1, 2, 3].forEach((v) => {
  sum += v;
});
```

# ES6 新增数据类型 symbol 数据类型

**回顾**
`JavaScript` 有 6 种数据类型 , 分别是 :
`String` 字符串类型;
`Number` 数字类型;
`Object` 对象类型;
`Boolean` 布尔值类型;
`Undefined`
`Null`

而 `ES6` 给我们带来一种全新的数据类型 : `Symbol` 每一种全新的事物的诞生都是为了解决某种问题 , `Symbol` 的初衷 : 解决对象的属性名冲突 , `Symbol()` , **它代表着一个独一无二的值** , 虽然我们看不到它长什么样子 , 但基本上 , 它有点类似字符串

```js
let sm = Symbol();
console.log(sm); // Symbol()
console.log(typeof sm); // symbol

let sm1 = Symbol();
let sm2 = Symbol();
console.log(sm1); // Symbol()
console.log(sm2); // Symbol()
console.log(sm1 == sm2); // false
console.log(sm1 === sm2); // false

let sm3 = Symbol("sm3");
let sm4 = Symbol("sm4");
console.log(sm3); // Symbol(sm3)
console.log(sm4); // Symbol(sm4)
```

`Symbo()` 函数接受参数 , 用于对实例值的描述
`symbol` 永远都是独一无二的值 , 谨记

```js
let sm5 = Symbol("sm");
let sm6 = Symbol("sm");
console.log(sm5 == sm6); // false
console.log(sm5 === sm6); // false
```

下面 , 我们用两种方式获取 `name` 的值  
第一种用中括号的形式 `[name]` 能正确获取到  
第二种用点运算符的形式 , 获取失败
原因是 : 当 `symbol` 值作为对象的属性名的时候 , 不能用点运算符获取对应的值

```js
let name = Symbol();
let person = {
  [name]: "张三",
};
console.log(person[name]); // 张三
console.log(person.name); // undefined
```

因为用点运算符的话 , 会导致 `javascript` 把后面的属性名为理解为一个字符串类型 , 而不是 `symbol` 类型

```js
let name = Symbol();
let person = {};
person.name = "张三";
console.log(person.name); // 张三
console.log(person["name"]); // 张三
console.log(person[name]); // undefined
```

## 属性名的遍历

当 `symbol` 类型的值作为属性名的时候 , 该属性是不会出现在 `for...in` 和 `for...of` 中的  
也不会被 `Object.keys()` 获取到

```js
// 属性名的遍历
let name = Symbol();
let person = {
  [name]: "张三", // Symbol 类型
  age: 20, // String 类型
};

Object.keys(person); // ["age"]

for (let key in person) {
  console.log(key);
}
// 结果: [age];
```

## Object.getOwnPropertySymbols( )

`Object.getOwnPropertySymbols()` 方法 , 它会找到 `symbol` 类型的属性并且返回一个数组 , 数组的成员就是 `symbol` 类型的属性值

```js
let name = Symbol("name");
let age = Symbol("age");
let person = {
  [name]: "张三",
  [age]: 22,
  sex: "man",
};
Object.getOwnPropertySymbols(person);
// 结果: [Symbol(name),Symbol[age]]
```

## Reflect.ownKeys( )

由于获取字符串类型的属性和获取 `symbol` 类型的属性要分开两种不同的方式来获取 , 难免有有时候会很不方便  
我们可以用 `Reflect.ownKeys()` 方法一次性获取所有类型的属性 , 不管它是字符串类型还是 `symbol` 类型

```js
console.log(Reflect.ownKeys(person));
```

## Symbol.for( )

`Symbol.for()` 函数作用 : 根据参数名 , 去**全局环境**中搜索是否有以该 `symbol.for()` 参数为名的 `symbol` 值  
有就返回它 , 没有就以该参数名来创建一个新的 `symbol` 值

```js
let n1 = Symbol.for("name");
let n2 = Symbol.for("name");
console.log(n1 === n2); // true
```

## Symbol.keyFor( )

`Symbol.keyFor()` 函数作用 : 返回一个以被登记在全局环境中的 `symbol` 值的 `key` , 没有就返回 `undefined`
注意这句话的一个关键词 : **"被登记在全局环境中"**  
也就是说这个 `symbol` 值是被 `Symbol.for()` 创建的 , 不是被 `Symbol()` 创建的

```js
let n1 = Symbol("name"); // 此时 n1 是创建在 Symbol 类型下的变量,并非全局
let n2 = Symbol.for("name");
console.log(n1 === n2); // false
```

```js
let n1 = Symbol.for("name");
console.log(Symbol.keyFor(n1)); // name
```

# Proxy 的实现

## proxy 的实现

```js
// proxy
let personB = {
  name: "张三",
  age: 20,
};
let pro = new Proxy(personB, {
  get(target, property) {
    return target;
  },
  set(target, property, value) {
    target[property] = value;
  },
  ownKeys(target) {
    return ["name"];
  },
  has(target, property) {
    if (target[property] == undefined) {
      return false;
    } else {
      return true;
    }
  },
});
console.log(pro.target); // {name: "张三", age: 20}
pro.name = "王五";
console.log(pro.target); // {name: "王五", age: 20}
console.log(Object.keys(personB)); // ["name", "age"]
console.log(Object.keys(pro)); // ["name"]
console.log("name" in pro); // true
console.log("cname" in pro); // false
```

## apply( )

除了对象类型的变量可以被代理 , 函数也可以被代理  
如果被代理的变量是一个函数 , 那么还会支持一个拦截程序 : `apply` 调用

```js
function func(value) {
  console.log("func");
}
let proxy = new Proxy(func, {
  apply(target, property, value) {
    return `today is ${value}`;
  },
});
console.log(proxy("Saturday"));
```

## proxy.revocable( )

如果创建了代理之后又想取消代理的话 , 我们可以用 `Proxy.revocable()`( 可废止的 , 可撤回的 ) 函数来实现  
它会返回一个对象 , 对象中含有一个 `proxy` 属性 , 它就是 `Proxy` 的代理实例对象
还有一个 `revoke` 属性 , 它是一个方法 , 用于取消代理。

```js
let personC = { name: "张三" };
let handle = {
  get(target, property) {
    return "李四";
  },
};
let obj = Proxy.revocable(proxy, handle);
console.log(obj.proxy.name); // 李四
obj.revoke();
console.log(obj.proxy.name); // Uncaught TypeError: Cannot perform 'get' on a proxy that has been revoked
```

# for...of 使用

**for...of 的优势** :

1. 写法比 `for` 循环简洁很多
2. 可以用 `break` 来终止整个循环 , 或者 `continute` 来跳出当前循环 , 继续后面的循环  
   结合 `keys()` 获取到循环的索引 , 并且是数字类型 , 而不是字符串类型

```js
let arrA = [1, 2, 3];
for (let value of arrA) {
  console.log(value);
}

for (let value of arrA) {
  if (value > 1) {
    console.log(value);
    break;
  }
}
for (let value of arrA) {
  if (value > 1) {
    console.log(value);
    continue;
  }
}
```

# The_End
