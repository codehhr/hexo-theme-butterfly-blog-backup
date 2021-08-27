---
title: Vue 基础
date: 2021-07-19 21:39:18
tags:
  - Vue
categories:
  - Vue
  - Vue基础
keywords:
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

# Vue.js

![vue.js](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/vuebasic/vueall.png)

# 什么是 `vue.js`

- `Vue.js` 是一套`构建用户界面`的`渐进式` `框架` , 与其他重量级框架不同的是 , `Vue` 采用自底向上增量开发的设计 , `Vue` 的核心库只关注视图层 , 不仅易于上手 , 还便于与第三方库或既有项目整合 ,
- `Vue.js` 是前端的主流框架之一 , 和 `Angular.js`、`React.js` 一起 , 并成为前端三大主流框架！

## 为什么学习流行框架

- 企业为了提高开发效率 : 在企业 `4E2D` , 时间就是效率 , 效率就是金钱 ;
- 企业中 , 使用框架 , 能够提高开发的效率 ;
- 提高开发效率的发展历程 : 原生 `JS` -> `Jquery` 之类的类库 -> 前端模板引擎 -> `Angular.js` / `Vue.js`
- 能够帮助我们减少不必要的 DOM 操作 ;提高渲染效率 ;双向数据绑定的概念【通过框架提供的指令 , 我们前端程序员只需要关心数据的业务逻辑 , 不再关心 `DOM` 是如何渲染的了】
- 在 `Vue` 中 , 一个核心的概念 , 就是让用户不再操作 `DOM` 元素 , 解放了用户的双手 , 让程序员可以更多的时间去关注业务逻辑 ;

## 框架和库的区别

- 框架 : 是一套完整的解决方案 , 对项目的侵入性较大 , 项目如果需要更换框架 , 则需要重新架构整个项目
  - 例如 : `node` 中的 `express`
- 库 ( 插件 ) : 提供某一个小功能 , 对项目的侵入性较小 , 如果某个库无法完成某些需求 , 可以很容易切换到其它库实现需求
  - 例如 : 从 `Jquery` 切换到 `Zepto`
  - 例如 : 从 `EJS` 切换到 `art-template`

## MVC 与 MVVM 的区别

- `MVC` 是后端的分层开发概念 ;
- `MVVM` 是前端视图层的概念 , 主要关注于视图层分离 , 也就是说 : `MVVM` 把前端的视图层 , 分为了三部分 `Model`、`View`、`VM ViewModel` ;

![vue.js](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/vuebasic/MVVM.png)

# 开始写 Vue.js 代码

## 引入 vue.js

```html
<script src="https://cdn.bootcdn.net/ajax/libs/vue/2.6.14/vue.js"></script>
```

## 写视图层 , 要展示的内容

`Vue.js` 的核心是一个允许采用简洁的模板语法来声明式地将数据渲染进 `DOM` 的系统 :

**示例**

```html
<div id="app">
  <!-- 插值表达式 , 可以读取变量 -->
  {{ message }}
</div>
```

## 实例化 Vue()

{% hideToggle 实例化 Vue() %}

```html
<!-- 引入 vue.js , 引入 js 之后他为我们提供了 Vue 类 -->
<script>
  // 调度层
  let vm = new Vue({
    // vue 控制的区域
    el: "#app",
    // data 参数存放我们的数据 , 这一层就是 mvvm 里的 model 层
    data: {
      message: "Hello Vue!",
    },
    methods: {},
  });
</script>
```

{% endhideToggle %}

页面展示内容:

{% note simple %}
Hello Vue!
{% endnote %}

**注意 : 都是通过 `this` 对象去拿的 , 通过 `this` 也可以调用方法 , 写方法的时候我们需要注意 `this` 的指向问题**

# 插值表达式 , v-cloak , v-text , v-html

- 如何获取变量值呢?
  - 插值表达式 : `{{ }}` , 可以在前后插一些内容;
  - `v-text` : 会替换掉元素里的内容;
  - `v-html` : 可以渲染 `html` 界面;

{% hideToggle 插值表达式&sbquo;v-cloak&sbquo;v-text&sbquo;v-html %}

```html
<!-- 引入vue的js , 引入js之后他为我们提供了Vue类 -->
<script src="https://cdn.bootcdn.net/ajax/libs/vue/2.6.14/vue.js"></script>

<!-- 视图层 start -->
<div id="app">
  <!-- 在 vue 加载之前 v-cloak 存在 , vue 加载结束之后 v-cloak就隐藏了 , 利用这个特性可以实现 : 界面防止闪烁
  如果网速够快的话也就看不出来了 -->
  <p v-cloak>{{ message }}</p>
  <!-- 使用 v-text 给界面元素赋值 -->
  <!-- 如果我们想在变量之前或者后面加一些内容的话使用 插值表达式 -->
  <!-- 如果我们想直接覆盖元素内容的话使用 v-text 指令 -->
  <p v-text="message"></p>
  <p v-text="html"></p>
  <!-- 通过 v-html 指令把字符串解析成 html 的内容 -->
  <p v-html="html">1111</p>
</div>
<!-- 视图层 end -->

<script>
  // 调度层 start
  var vm = new Vue({
    // vue 控制的区域
    el: "#app",
    // data 参数存放我们的数据 , 这一层就是 mvvm 里的 model 层
    data: {
      message: "Hello Vue!",
      html: "<h1>这是一个很大的标题</h1>",
    },
  });
  // 调度层 end
</script>
```

{% endhideToggle %}

# v-bind

- 界面元素属性值的绑定
  - 括号里不加引号的都是 `data` 里的数据读取
  - 如果想使用字符串需要再加上引号 ( `{{"hello World"}}` )
  - 里面可以写表达式
  - 里面也可以调用定义好的方法 , 拿到的是方法的返回值

**示例**

{% hideToggle v-bind %}

```html
<!-- 引入 vue 的js , 引入 js 之后他为我们提供了 Vue 类 -->
<script src="https://cdn.bootcdn.net/ajax/libs/vue/2.6.14/vue.js"></script>

<!-- 视图层 start -->
<div id="app">
  <!-- 插值表达式 , 可以读取变量 -->
  {{ message }}
  <!-- <button v-bind:title="nihao">按钮</button> -->
  <button :title="hello">按钮</button>
  <input type="text" v-bind:value="message" />
</div>
<!-- 视图层 end -->

<script>
  // 调度层 start
  var vm = new Vue({
    // vue 控制的区域
    el: "#app",
    // data 参数存放我们的数据 , 这一层就是 mvvm 里的 model 层
    data: {
      message: "Hello Vue!",
      flag: false,
      hello: "你好世界",
    },
  });
  // 调度层 end
</script>
```

{% endhideToggle %}

# v-on

- 进行事件的绑定 , 我们用的最多的是 `click` 事件绑定
- 简写为 `@`
- 实现跑马灯的效果

**示例**

{% hideToggle v-on %}

```html
<!-- 引入 vue 的js , 引入 js 之后他为我们提供了 Vue 类 -->
<script src="https://cdn.bootcdn.net/ajax/libs/vue/2.6.14/vue.js"></script>

<div id="app">
  <!-- 跑马灯 start -->
  <button @click="start" :disabled="disabled">开始</button>
  <button @click="stop" :disabled="!disabled">暂停</button>
  <h2>{{msg}}</h2>
  <!-- 跑马灯 end -->
</div>

<script>
  let vm = new Vue({
    el: "#app",
    data: {
      msg: "猥琐发育,别浪~",
      disabled: false,
      lampTimer: null,
    },
    methods: {
      start() {
        console.log("start");
        this.disabled = !this.disabled;
        clearInterval(this.lampTimer);
        let msgList;
        this.lampTimer = setInterval(() => {
          msgList = this.msg.split("");
          msgList.push(msgList.shift());
          this.msg = msgList.join("");
        }, 200);
      },
      stop() {
        console.log("stop");
        this.disabled = !this.disabled;
        clearInterval(this.lampTimer);
      },
    },
  });
</script>
```

{% endhideToggle %}

# 事件修饰符

- `.stop` 阻止冒泡
- `.prevent` 阻止默认事件
- `.capture` 添加事件侦听器时使用事件捕获模式
- `.self` 只当事件在该元素本身 ( 比如不是子元素 ) 触发时触发回调
- `.once` 事件只触发一次

**示例**

{% hideToggle 事件修饰符 %}

```html
<!-- 引入 vue 的js , 引入 js 之后他为我们提供了 Vue 类 -->
<script src="https://cdn.bootcdn.net/ajax/libs/vue/2.6.14/vue.js"></script>

<div id="app">
  <div class="outer" @click.capture="outer">
    <div class="inner" @click.stop="inner">
      <div class="self" @click.self="self">
        <button @click.once="button">button</button>
        <a href="https://codehhr.cn" @click.prevent="clickA">a-link-tag</a>
      </div>
    </div>
  </div>
</div>

<script>
  let vm = new Vue({
    el: "#app",
    data: {},
    methods: {
      outer() {
        console.log("outer");
      },
      inner() {
        console.log("inner");
      },
      self() {
        console.log("self");
      },
      button() {
        console.log("button");
      },
      clickA() {
        console.log("a-link-tag");
      },
    },
  });
</script>
```

{% endhideToggle %}

# v-model 数据双向绑定

- 作用 : 数据双向绑定
- 注意 : 绑定的是表单控件

**示例**

{% hideToggle v-model 数据双向绑定 %}

```html
<!-- vue.js start -->
<script src="https://cdn.bootcdn.net/ajax/libs/vue/2.6.14/vue.js"></script>
<!-- vue.js end -->

<div id="app">
  <input type="text" name="" id="" v-model:value="msg" />
  <h1>{{msg}}</h1>
</div>
<script>
  let vm = new Vue({
    el: "#app",
    data: {
      msg: "",
    },
    methods: {},
  });
</script>
```

{% endhideToggle %}

# Vue 中样式的使用

## 使用 class 样式 :

{% tabs class %}

<!-- tab 数组 -->

使用 `vue` 设置多个样式的时候可以使用数组

```html
<div :class="[font20,blue]">Text</div>
```

```json
data: {
  font20: "font20",
  blue: "blue"
}
```

<!-- endtab -->

<!-- tab 三木表达式 -->

```html
<div :class="flag?'class1':'class2'">Text</div>
```

```json
data: {
  flag: true,
  class1: "red",
  class1: "blue"
}
```

<!-- endtab -->

<!-- tab 数组内置对象 -->

当我们根据某个条件显示某个样式的时候可以使用对象的方式 , 对象里的键就是我们显示的样式 , 值是个 `bool` 类型

```html
<div :class="[class1,{'class2':flag}]">Text</div>
```

```json
data: {
  flag: true,
  class1: "red",
  class1: "blue"
}
```

<!-- endtab -->

<!-- tab 直接通过对象 -->

直接使用对象 , 对象里的键就是我们显示的样式 , 值是个 `bool` 类型

```html
<div :class="{'class1':false,'class2':true}">Text</div>
```

或者

```html
<div :class="classObj">Text</div>
```

```json
data: {
  classObj: {
    class1: true,
    class2: true
  }
}
```

<!-- endtab -->

{% endtabs %}

## 使用行内样式

{% tabs style %}

<!-- tab :style 的形式 -->

直接在元素上通过 `:style` 的形式 , 书写样式对象

```html
<div :style="{'color':color}">Text</div>
```

```json
data: {
  color: "red",
}
```

<!-- endtab -->

<!-- tab 在data中定义样式对象 -->

- 在 `data` 上定义样式
- 在元素中 , 通过属性绑定的形式 , 将样式对象应用到元素中

```html
<div :style="textStyle">Text</div>
```

```json
data: {
  textStyle: {
    color: "red",
    "font-size": "50px"
  }
}
```

<!-- endtab -->

<!-- tab 数组引用多个样式对象 -->

在 `:style` 中通过数组 , 引用多个 `data` 上的样式对象

- 在 `data` 上定义样式
- 在元素中 , 通过属性绑定的形式 , 将样式对象应用到元素中

```html
<div :style="[textStyle1,textStyle2]">Text</div>
```

```json
data: {
  textStyle1: {
    color: "red",
    "font-size": "50px"
  },
   textStyle2: {
    "font-weight": "600"
  }
}
```

<!-- endtab -->

<!-- tab 通过调用方法返回对象 -->

```js
methods: {
  getStyle(num) {
    let obj = {
      color: "red",
      "font-size": "50px",
    };
    if (num == 1) {
      obj.color = "red";
    } else {
      obj.color = "green";
    }
    return obj;
  },
}
```

<!-- endtab -->

{% endtabs %}

# V-for 和 key 属性

- 遍历数组 , 参数 `(item,index) in list`
- 遍历对象 , 参数 `(value,key,index) in list`
- 遍历数字 , `num in 10 (1~10)`
- `key` 在使用 `v-for` 的时候都需要去设置 `key`
  - 让界面元素和数组里的每个记录进行绑定
  - `key` 只能是字符串或者数字
  - `key` 必须是唯一的

**示例**

{% hideToggle V-for和key %}

```html
<!-- 引入 vue 的js , 引入 js 之后他为我们提供了 Vue 类 -->
<script src="https://cdn.bootcdn.net/ajax/libs/vue/2.6.14/vue.js"></script>

<div id="app">
  <div v-for="(value,key,index) in zhangsan" :key="index">
    <h1>{{index}} - {{key}} : {{value}}</h1>
    <br />
  </div>

  <div v-for="(item,index) in list" :key="index">
    <h1>{{index}} : {{item}}</h1>
  </div>

  <div v-for="item in 6">
    <h1>🦌</h1>
  </div>
</div>

<script>
  let vm = new Vue({
    el: "#app",
    data: {
      list: ["github", "gitee", "coding", "gitlab"],
      zhangsan: {
        name: "张三",
        age: 35,
        nickName: "法外狂徒",
      },
    },
    methods: {},
  });
</script>
```

{% endhideToggle %}

**注意:**
`2.2.0+` 的版本里 , 当在组件中使用 `v-for` 时 , `key` 现在是必须的;
当 `Vue.js` 用 `v-for` 正在更新已渲染过的元素列表时 , 它默认用 "就地复用" 策略 , 如果数据项的顺序被改变 , `Vue` 将不是移动 `DOM` 元素来匹配数据项的顺序 , 而是简单复用此处每个元素 , 并且确保它在特定索引下显示已被渲染过的每个元素
为了给 `Vue` 一个提示 , 以便它能跟踪每个节点的身份 , 从而重用和重新排序现有元素 , 你需要为每项提供一个唯一 `key` 属性。

# v-if 与 v-show 区别

- 区别：
  - `v-if` 删除 `dom` 元素
  - `v-show` 设置 `display:none`
- 应用场景：
  - `v-if` 只修改一次的时候可以使用 `v-if`
  - `v-show` 频繁切换的时候可以使用 `v-show`

**示例**

{% hideToggle v-if与v-show 区别 %}

```html
<!-- 引入 vue 的js , 引入 js 之后他为我们提供了 Vue 类 -->
<script src="https://cdn.bootcdn.net/ajax/libs/vue/2.6.14/vue.js"></script>

<div id="app">
  <div v-if="flag"><h1>张三</h1></div>
  <div v-if="age>18?flag:!flag"><h1>{{age}}</h1></div>
  <div v-else><h1>未成年</h1></div>
  <!--  -->
  <div v-show="flag"><h1>show</h1></div>
  <div v-show="!flag"><h1>show</h1></div>
</div>

<script>
  let vm = new Vue({
    el: "#app",
    data: {
      flag: true,
      age: 20,
    },
    methods: {},
  });
</script>
```

{% endhideToggle %}
