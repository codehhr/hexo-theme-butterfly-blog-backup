---
title: ES6 新增用法 ( 四 )
date: 2021-06-24 21:06:25
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/sunrise.jpg
cover:
tags:
  - js
  - javascript
  - ES6
  - 数组去重
categories:
  - js
  - ES6
comments:
---

# Iterator 遍历器

## for...of 为什么不遍历 object 对象

要想能够被 `for...of` 正常遍历的 , 都需要实现一个遍历器 `Iterator` , 而数组 , `Set` 和 `Map` 结构 , 早就内置好了遍历器 `Iterator` ( 又叫迭代器 ) , 它们的原型中都有一个 `Symbol.iterator` 方法 : 而 `Object` 对象并没有实现这个接口 , 使得它无法被 `for...of` 遍历

验证一下 , 它们的原型中到底是不是有个叫 `Symbol.iterator` 的方法:

```js
//数组
console.log(Array.prototype[Symbol.iterator]); //结果 : function values(){...}
//字符串
console.log(String.prototype[Symbol.iterator]); //结果 : function [Symbol.iterator](){...}
//Set结构
console.log(Set.prototype[Symbol.iterator]); //结果 : function values(){...}
//Map结构
console.log(Map.prototype[Symbol.iterator]); //结果 : function entries(){...}
//Object对象
console.log(Object.prototype[Symbol.iterator]); // undefined
```

唯独 `Object` 对象的原型上没有 `Symbol.iterator` , 返回了 : `undefined` , 其他的数据类型的原型上都含有一个名字叫 `Symbol.iterator` 的方法

**注意** : `Symbol.iterator` 是 `Symbol` 对象的 `iterator` 属性 , 是一个特殊的 `Symbol` 值 , 因此 , 当它作为 `prototype` 对象属性名的时候 , 获取它的时候需要使用 `[]` 的形式: `prototype[Symbol.iterator]` , 不能使用点形式获取 : prototype.Symbol.iterator
也就说 , 只要一个数据结构拥有一个叫 `[Symbol.iterator]()` 方法的数据结构 , 就可以被 `for...of` 遍历

## Iterator 原理

当可遍历对象被 `for...of` 遍历的时候 , `[Symbol.iterator]()` 就会被调用 , 返回一个 `iterator` 对象 , `iterator` 对象里有一个很重要的方法 : `next()`

```js
let arr = ["a", "b", "c"];
let iterator = arr[Symbol.iterator]();
console.log(iterator); // Array Iterator {}
console.log(iterator.next()); // {value: "a", done: false}
console.log(iterator.next()); // {value: "b", done: false}
console.log(iterator.next()); // {value: "c", done: false}
console.log(iterator.next()); // {value: undefined, done: true}
```

第 1 次调用 `next()` 方法 : 返回数组的第 1 个元素 : "a" , 以及 `done` 的值为 `fasle` , 表示循环没有结束 , 继续遍历
第 2 次调用 `next()` 方法 : 返回数组的第 2 个元素 : "b" , 以及 `done` 的值还是为 `fasle` , 表示循环没有结束 , 继续遍历
第 3 次调用 `next()` 方法 : 返回数组的第 3 个元素 : "c" , 以及 `done` 的值依然为 `fasle` , 表示循环没有结束 , 继续遍历
第 4 次调用 `next()` 方法 : 返回的 value 值为 undefined , 以及 `done` 的值变成了 `true` , 表示遍历结束

`for...of` 的原理就是 : 先调用可遍历对象的 `[Symbol.iterator]()` 方法 , 得到一个 `iterator` 遍历器对象 , 然后就在遍历器上不断调用 `next()` 方法 , 直到 `done` 的值为 `true` 的时候 , 就表示遍历完成结束了

## 自定义 Iterator 遍历器

给一个 `Object` 对象加一个 `[Symbol.iterator]()` 方法 , 看看它是不是就能被 `for...of` 遍历了

```js
let obj = {
  name: "张三",
  age: 20,
};

// 自定义 [Symbol.iterator] 迭代器
obj[Symbol.iterator] = function () {
  // 获取到对象的每个 key 值返回一个数组
  let keys = Object.keys(obj);
  // 获取到 key 值 ( 对象 ) 的长度
  let length = keys.length;
  // 定义循环变量
  let index = 0;
  // 返回对象:每次迭代会自动调用返回对象里面的 next() 方法
  return {
    next() {
      // 返回值有 value 和 done
      // value 能自定义
      // done为 true 时跳出循环
      return index < length
        ? {
            value: { k: keys[index], v: obj[keys[index++]] },
            done: false,
          }
        : {
            done: true,
          };
    },
  };
};
```

**现在用 for...of 试一下能不能遍历此对象**

```js
for (let { k, v } of obj) {
  console.log(k, v);
}
// 打印结果:
//  name 张三
//  age 20
```

我们定义了一个 `Object` 对象 , 同时给它添加了 `[Symbol.iterator]()` 方法 , 并在 `[Symbol.iterator]()` 方法返回的对象里实现了 `next()`方法 , `next()` 方法返回的对象包含了 `value` 属性和 `done` 属性

也就是说可以通过添加 `[Symbol.iterator]()` 方法 , 把一个不可遍历的 `Object` 对象 , 变成可遍历的对象

# Generator 函数

## 声明 Generator 函数

`Generator` 函数 , 又称生成器函数 , 是 `ES6` 的一个重要的新特性

```js
// 声明一个 hello 的 Generator 函数
function* hello(name) {
  yield `hello ${name}`;
  yield `bye`;
}
```

## 调用 Generator 函数

```js
// 声明一个 hello 的 Generator 函数
function* hello(name) {
  yield `hello ${name}`;
  yield `bye`;
}

// 调用 hello 函数
let ite = hello("前端君");
console.log(ite.next()); // {value: "hello 前端君", done: false}
console.log(ite.next()); // {value: "bye", done: false}
console.log(ite.next()); // {value: undefined, done: true}
```

一开始 , 调用 `hello("前端君")` , 函数执行后 , 返回了一个 : `[object Genrator]` 生成器对象 , 这里生成器的 `next()` 方法的和遍历器 `iterator` 的 `next()` 方法的返回结果很像
可以把 `Generator` 函数被调用后得到的生成器理解成一个遍历器 `iterator` , 用于遍历函数内部的状态

## Generator 函数的行为

`Generator` 函数被调用后并不会一直执行到最后 , 它是先回返回一个生成器对象 , 然后暂停 , 等到生成器对象的 `next()` 方法被调用后 , 函数才会继续执行 , 直到遇到关键字 `yield` 后 , 又会停止执行 , 并返回一个 `Object` 对象 , 然后继续等待 , 直到 `next()` 再一次被调用的时候 , 才会继续接着往下执行 , 直到 `done` 的值为 `true`

## yield 语句的使用

`yield` 有点像传统函数的 `return` 的作用 , 但不同的是普通函数只能 `return` 一次 , 但是 `Generator` 函数可以有很多个 `yield` , 而 `return` 代表的是终止执行 , `yield` 代表的是暂停执行 , 后续通过调用生成器的 `next()` 方法 , 可以恢复执行

## next 方法接收参数

`next()` 方法还可以接受一个参数 , 它的参数会作为上一个 `yield` 的返回值

**案例**

```js
function* gen() {
  let params = yield 2; // params =  3
  let params1 = yield 3; // params1= 1
  let params2 = yield params1 + 6; // params2 = 7
  let params3 = yield 7; // params3 = 4
  return params2 * params + params3;
}
let lt = gen();
console.log(lt.next()); // { value: 2, done: false }
console.log(lt.next(3)); // { value: 3, done: false }
console.log(lt.next(lt.next(1).value)); // { value: 7, done: false }
console.log(lt.next(4)); // { value: 25, done: true }
```

## 关键字 yield\*

在一个 `Generator` 函数里面 , 如果我们想调用另一个 `Generator` 函数 , 就需要用到的关键字是 : yield\*

**案例**

```js
// 声明 Generator 函数 : gen1
function* gen1() {
  yield "gen1 start";
  yield "gen1 end";
}
// 声明 Generator 函数 : gen2
function* gen2() {
  yield "gen2 start";
  yield "gen2 end";
}

// 声明 Generator 函数 : start
function* start() {
  yield "start";
  yield* gen1();
  yield* gen2();
  yield "end";
}

// 调用 start 函数
var ite = start(); // 创建一个生成器
ite.next(); // {value: "start", done: false}
ite.next(); // {value: "gen1 start", done: false}
ite.next(); // {value: "gen1 end", done: false}
ite.next(); // {value: "gen2 start", done: false}
ite.next(); // {value: "gen2 end", done: false}
ite.next(); // {value: "end", done: false}
ite.next(); // {value: undefined, done: true}
```

## Generator 函数的用途

是 `ES6` 的一个很重要的新特性 , 它可以控制函数的内部状态 , 依次遍历每个状态 ; 可以根据需要 , 轻松地让函数暂停执行或者继续执行 , 根据这个特点 , 我们可以利用 `Generator` 函数来实现异步操作的效果

# Set 和 WeakSet 用法

## 什么是 Set

`Set` 是 `ES6` 给开发者带来的一种新的数据结构 , 你可以理解为值的集合 , 我们平时见到的数组 `Array` 也是一种数据结构 , 但是 `Set` 跟其他数据结构不同的地方就在于 : 它的值不会有重复项

## Set 的基本用法

```js
let set1 = new Set();
console.log(set1); // Set(0) {}

let set2 = new Set([1, 2, 3]);
console.log(set2); // Set(3) {1, 2, 3}

let set3 = new Set();
set3.add(4);
set3.add(5);
set3.add(6);
console.log(set3); // Set(3) {4, 5, 6}
```

## Set 成员值唯一

```js
let set = new Set();
set.add(1);
set.add(1);
set.add(2);
set.add(2);
console.log(set); // Set(2) {1, 2}
```

## size 属性

`size` 属性 : 获取成员的个数

```js
let set = new Set([1, 2, 3, 4, 5]);
console.log(set); // 5
```

## delete( )

`delete()` 方法 : 用户删除 `Set` 结构中的指定值 , 删除成功返回 : `true` , 删除失败返回 : `fasle`

```js
let set = new Set([5, 6, 7, 8]);
console.log(set); // Set(4) {5, 6, 7, 8}
console.log(set.delete(8)); // true
console.log(set.delete(8)); // false
console.log(set); // Set(3) {5, 6, 7}
```

## clear( )

`clear()` 方法 : 清除所有成员 , 一个不留

```js
let set = new Set([5, 6, 7, 8]);
console.log(set); // Set(4) {5, 6, 7, 8}
set.clear();
console.log(set); // Set(0) {}
```

## has( )

`has()` 方法 : 判断 `set` 结构中是否含有指定的值 , 如果有 , 返回 `true` , 如果没有 , 返回 `fasle`

```js
let set = new Set([1, 2, 3]);
console.log(set.has(1)); // true
console.log(set.has(6)); // false
```

## entries( )

`entries()` 方法 : 返回一个键值对的遍历器

```js
var set = new Set(["a", "b", "c"]);
console.log(set.entries()); // SetIterator {"a" => "a", "b" => "b", "c" => "c"}
```

注意得到的结果 , 成员值 `a` 对应的键值对是 `["a","a"]` , 也就是说 : `Set` 结构是键名和键值是同一个值

## keys( ) 和 values( )

`keys()` 方法 : 返回键名的遍历器
`values()` 方法 : 返回键值的遍历器

## forEach( )

使用方式跟数组的 `forEach` 一样 , 当然 , 得到的 `value` 是 `key` 的值是一样的

```js
var set = new Set(["a", "b", "c"]);
// 使用回调函数遍历每个成员
set.forEach(function (value, key) {
  console.log(value, key);
});
// 打印结果
// a a
// b b
// c c
```

## set 用途之一

**数组去重** , 顺便我们把它封装成一个函数

```js
let arr = [1, 1, 1, 2, 2, 2, 3, 3, 4, 4, 4, 4];

// 数组去重
function deduplication(arr) {
  return Array.from(new Set(arr));
}

console.log(deduplication(arr));
```

## Weakset 结构

`WeakSet` 结构同样不会存储重复的值 , 不同的是 , 它的成员必须是对象类型的值 , 否则就会报错

```js
let ws = new WeakSet([{ age: 18 }]);
```

```js
// 错误示范
let ws = new WeakSet([1, 2]);
```

实际上 , 任何可遍历的对象 , 都可以作为 `WeakSet` 的初始化参数 , 比如 : **数组**

```js
let arr1 = [1];
let arr2 = [2];
// 初始化一个 WeakSet 对象,参数是 数组 类型
let ws = new WeakSet([arr1, arr2]); //结果 : WeakSet {Object {age: 18}}
```

同样 , `WeakSet` 结构也提供了 `add()` 方法 , `delete()` 方法 , `has()` 方法给开发者使用 , 作用与用法跟 `Set` 结构完全一致

另一个不同点是 : `WeakSet` 结构不可遍历 , 因为它的成员都是对象的弱引用 , 随时被回收机制回收 , 成员消失 , 所以 WeakSet 结构不会有 `keys()` , `values()` , `entries()` , `forEach()` 等方法和 `size` 属性

# Map 和 WeakMap

## 什么是 Map

`ES6` 提供了 `Map` 结构给我们使用 , 它跟 `Object` 对象很像 , 但是不同的是 , 它的 `key` 键名的类型不再局限于字符串类型了 , 它可以是各种类型的值 ; 可以说 , 它比 `Object` 对象更加灵活了 , 当然 , 也更加复杂了。

## Map 的基本用法

跟 `Set` 类似

```js
let map1 = new Map();
console.log(map1); // Map(0) {}

let map2 = new Map([
  ["name", "前端君"],
  ["gender", 1],
]);
console.log(map2); // Map(2) {"name" => "前端君", "gender" => 1}
```

`Map()` 方法里面的参数 , 首先它是一个数组 , 而里面的内容也是由多个数组组成 , `"name"` : `"前端君"` 作为一个键值对 , 将它们装在一个数组里面 , `["name","前端君"]` , 另外一组键值对也一样 : `["gender",1]` 这就是初始化一个 `Map` 结构实例的基本写法

## set( )

`set()` 方法作用 : 给实例设置一对键值对 , 返回 `map` 实例

```js
let map = new Map();
// 添加一个 string 类型的键名
map.set("name", "前端君");
// 添加一个数字类型的键名
map.set(1, 2);
console.log(map); // Map(2) {"name" => "前端君", 1 => 2}
```

`Map` 结构可以存储非字符串类型的键名 , 当然还可以设置更多其它类型的键名 , 比如更过分点的 :

```js
// 数组类型的键名
map.set([1], 2);
// 对象类型的键名
map.set({ name: "Zhangsan" }, 2);
// 布尔类型的键名
map.set(true, 2);
// Symbol 类型的键名
map.set(Symbol("name"), 2);
// null 为键名
map.set(null, 2);
// undefined 为键名
map.set(undefined, 2);
```

使用 `set` 方法的时候有一点需要注意 , 如果你设置一个已经存在的键名 , 那么后面的键值会覆盖前面的键值

```js
let map = new Map();
map.set("name", "前端君");
console.log(map); // 结果 : Map(1) {"name" => "前端君"}
// 再次设置 name 的值
map.set("name", "隔壁老王");
console.log(map); // 结果 : Map(1) {"name" => "隔壁老王"}
```

## get( )

`get()` 方法作用 : 获取指定键名的键值 , 返回键值

```js
let map = new Map([
  ["name", "前端君"],
  ["age", 20],
]);
console.log(map.get("name")); // 前端君
console.log(map.get("age")); // 20
console.log(map.get("gender")); // undefined
```

## delete( )

`delete()` 方法作用 : 删除指定的键值对 , 删除成功返回 : `true` , 否则返回 : `false`

```js
let map = new Map();
map.set("name", "前端君");
console.log(map); // Map(1) {"name" => "前端君"}
console.log(map.delete("name")); // true
console.log(map.delete("name")); // false
```

## clear( )

跟 `Set` 结构一样 , `Map` 结构也提供了 `clear()` 方法 , 让你一次性删除所有键值对

```js
let map = new Map();
map.set("name", "前端君");
map.set("gender", 1);
map.clear();
console.log(map); // Map(0) {}
```

## has( )

`has()` 方法作用 : 判断 `Map` 实例内是否含有指定的键值对 , 有就返回 : `true` , 否则返回 : `false`

```js
let map = new Map();
map.set("name", "前端君");
console.log(map.has("name")); // 结果 : true
console.log(map.has("age")); // 结果 : false
```

## entries()

`entries()` 方法作用 : 返回实例的键值对遍历器

```js
let map = new Map([
  ["name", "前端君"],
  ["age", 25],
]);
for (let [key, value] of map.entries()) {
  console.log(key + "  " + value);
}
// 打印结果
//  name  前端君
//  age  25
```

## keys( ) 和 values( )

`keys()` 方法 : 返回实例所有键名的遍历器
`values()` 方法 : 返回实例所有键值的遍历器

## forEach( )

```js
let map = new Map([
  ["name", "前端君"],
  ["age", 25],
]);
map.forEach(function (value, key) {
  console.log(key + " " + value);
});
// 打印结果
//  name 前端君
//  age 25
```

## size 属性

获取实例的成员数

```js
let map = new Map();
map.set(1, 3);
map.set("1", "3");
console.log(map.size); // 结果: 2
```

## 什么是 WeakMap

`WeakMap` 结构和 `Map` 结构很类似 , 不同点在于 `WeakMap` 结构的键名只支持引用类型的数据 , 比如 : 数组 , 对象 , 函数

## WeakMap 的基本用法

`WeakMap` 结构的使用方式和 `Map` 结构一样

```js
let wm = new WeakMap();
```

两者都是使用 `new` 来创建实例 , 如果添加键值对的话 , 我们同样是使用 `set` 方法 , 不过键名的类型必须要求是引用类型的值

```js
let wm = new WeakMap();
// 数组类型的键名
wm.set([1], 2);
// 对象类型的键名
wm.set({ name: "Zhangsan" }, 2);
// 函数类型的键名
function fn() {}
wm.set(fn, 2);
console.log(wm); // WeakMap {ƒ => 2, {…} => 2, Array(1) => 2}
```

从打印结果可以看出 , 以上类型的键名都可以成功添加到 `WeakMap` 实例中

## WeakMap 与 Map 的区别

如果是普通的值类型则不允许 , 比如 : `String` , `Number` , `null` , `undefined` , `boolean` , 而 `Map` 结构是允许的 , 这就是两者的不同之处 , 谨记

跟 `Map` 一样 , `WeakMap` 也拥有 `get` , `has` , `delete` 方法 , 用法和用途都一样 , 不同地方在于 , `WeakMap` 不支持 `clear` 方法 , 不支持遍历 , 也就没有了 `keys` , `values` , `entries` , `forEach` 这 4 个方法 , 也没有属性 `size`

理由跟 `WeakSet` 结构一样 : 键名中的引用类型是弱引用 , 你永远不知道这个引用对象什么时候会被垃圾回收机制回收了 , 如果这个引用类型的值被垃圾机制回收了 , `WeakMap` 实例中的对应键值对也会消失。
