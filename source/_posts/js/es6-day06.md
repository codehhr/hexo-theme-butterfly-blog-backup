---
title: ES6 新增用法 ( 六 )
date: 2021-06-25 19:17:42
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/sunrise.jpg
cover:
tags:
  - js
  - javascript
  - ES6
  - class
  - export
  - import
  - module
  - extends
categories:
  - js
  - ES6
comments:
---

# 类基本用法

## 类的属性和方法

声明一个类的写法 :

```js
// 定义一个叫  Animal 的类
class Animal {
  // constructor 构造函数
  constructor(color) {
    this.color = color;
  }
}
```

可以看到类里面 ( 花括号 `{}` 里面 ) 有一个叫 `constructor` 方法 , 它就是构造方法 , 构造方法里面的 `this` , 指向的是该类实例化后的对象 , 这就是实现了一个类的声明 , 如果你没有编写 `constructor` 方法 , 执行的时候也会被加上一个默认的空的 `constructor` 方法 , constructor 方法是必须的 , 也是唯一的 , 一个类体不能含有多个 constructor 构造方法

## 类的实例化对象

给类添加属性和方法 , 把类名后面的括号 `{}` 里面的内容称之为类体 , 我们会在类体内来编写类的属性和方法

```js
class Animal {
  // 构造方法
  constructor(name) {
    // 属性
    this.name = name;
  }
  // 自定义方法 getName()
  getName() {
    return this.name;
  }
}
```

## 类的自定义方法

```js
class Animal {
  // 构造方法
  constructor(name) {
    // 属性
    this.name = name;
  }
  // 自定义方法 getName()
  getName() {
    return `我想念 ${this.name}`;
  }
}

// 创建一个 Animal 实例对象 dog
let dog = new Animal("村口消失的大黄");
console.log(dog.name); // 村口消失的大黄
console.log(dog.getName()); // 我想念 村口消失的大黄
```

## 类的静态方法

如果在一个方法前 , 加上 `static` 关键字 , 就表示该方法**不会被实例继承** , 而是直接通过类来调用 , 这就称为 "静态方法" , 类的静态方法可以被类直接调用

```js
class Father {
  static hello() {
    return "hello";
  }
}
console.log(Father.hello());
```

## 类的继承

`ES6` 使用 `extends` 关键字来实现子类继承父类
`super` , 它相当于是父类中的 `this`

```js
// 父类 Animal
class Animal {}

// 子类 Dog
class Dog extends Animal {
  // 构造方法
  constructor(name, color) {
    super(name);
    this.color = color;
  }
}
```

**可以用 `super` 来引用父类 , 访问父类的方法**

```js
class Animal {
  // 构造方法
  constructor(name) {
    // 属性
    this.name = name;
  }

  // 父类自定义方法
  hello() {
    return "Hello ~";
  }
}

// 子类 Dog
class Dog extends Animal {
  // 构造方法
  constructor(name, color) {
    super(name);
    this.color = color;
  }

  // 子类的实例方法
  getSomething() {
    return super.hello();
  }
}
// 创建 dog 实例对象
let dog = new Dog("dog", "orange");
// 调用子类方法
console.log(dog.getSomething());
```

在父类中 , 我们定义了 `say` 方法 , 想要在子类中调用父类的 `say` 方法的话 , 我们使用 `super.say()` 即可实现

**使用 `super` 有几个要注意的事项 :**

1. 子类必须在 `constructor` 方法中调用 `super` 方法
2. 调用 `super()` , 才可以使用 `this` , 否则报错

# Module 模块

## 模块化的初衷

高内聚,低耦合

目前还没有浏览器支持 `ES6` 的 `module` 模块
但是可以解决 :

1. vscode 安装 live sever
2. `<script type="module">` 将 `script` 标签中的 `type` 的类型换成 `module` , 告诉浏览器我们要使用 `es6` 的模块化了

## 导出 Export

导出 `Export` : 作为一个模块 , 它可以选择性地给其他模块暴露 ( 提供 ) 自己的属性和方法 , 供其他模块使用

## 导入 Import

导入 `Import` : 作为一个模块 , 可以根据需要 , 引入其他模块的提供的属性或者方法 , 供自己模块使用

## 实现 导入 Import 和 导出 Export

假设 `moduleB` 模块代码 :

```js
// moduleB.js
// 导出变量 name
let name = "前端君";
export { name };
```

假设 `moduleA` 模块代码 :

```js
// moduleA.js
// 导入 moduleB 的属性 name
import { name } from "./moduleB.js";
console.log(name); // 前端君
```

## 批量 导入 和 导出

模块 B 批量导出

```js
// moduleB.js
let name = "前端君";
let age = 20;
function hello() {
  console.log("Hello ~ 前端君");
}
export { name, age, hello };
```

模块 A 批量导入

```js
// moduleA.js
import { name, age, hello } from "./moduleB.js";
console.log(name); // 前端君
console.log(age); // 20
hello(); // Hello ~ 前端君
```

## 重命名导出的变量

想给导入的变量换一个名字的话 , 可以这样做 :
使用关键字 `as` , 可以实现给变量重命名

```js
// moduleA.js
import { name as newName } from "./moduleB.js";
console.log(newName); // 前端君
```

## 整体导入

可以使用星号 `*` 实现整体导入 :
使用星号符 `*` 将模块 `B` 提供的所有属性和方法整体导入赋值给变量 `obj` , 我们可以用点运算符 `.` 来获取它的属性和方法

```js
// moduleB.js
let name = "前端君";
let age = 20;
function hello() {
  console.log("Hello ~ 前端君");
}
export { name, age, hello };
```

```js
// moduleA.js
import * as obj from "./moduleB.js";
console.log(obj.name); // 前端君
console.log(obj.age); // 20
obj.hello(); // Hello ~ 前端君
```

## 默认导出

默认导出 , 每个模块支持导出一个没有名字的变量 , 使用关键语句 `export default` 来实现 :

```js
// moduleB.js
export default function () {
  console.log("I'm a default function.");
}
```

导入这个模块的时候 , 可以为这个匿名函数取任意的名字 , 我们试一下导入上面那个匿名函数

```js
// moduleA.js
import defaultFunction from "./moduleB.js";
defaultFunction(); // I'm a default function.
```

## 注意事项

### 声明的变量 , 对外都是只读的

```js
// moduleB.js
let name = "前端君";
export { name };
```

```js
// moduleA.js
import { name } from "./moduleB.js";
name = "tom"; // 报错: name is read-only
```

但是 , 如果模块 `B` 导出的是对象类型的值 , 就可修改 , 实质上是地址不可修改 , 可修改的是地址指向的内容

```js
// moduleB.js
let person = {
  name: "张三",
  age: 40,
};
export { person };
```

```js
// moduleA.js
import { person } from "./moduleB.js";
person.name = "李四";
console.log(person.name); // 李四
```

### 导入不存在的变量会报错

```js
// moduleB.js
let name = "前端君";
export { name };
```

```js
// moduleA.js
import { height } from "./moduleB.js";
console.log(height); // 报错: does not provide an export named 'height'
```
