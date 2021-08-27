---
title: Vue 组件
date: 2021-07-22 22:12:28
updated:
tags:
  - Vue
  - Vue 组件
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

# vue 组件

- 组件化和模块化的不同 :
  - 模块化 : 是从代码逻辑的角度进行划分的 ; 方便代码分层开发 , 保证每个功能模块的职能单一
  - 组件化 : 是从 UI 界面的角度进行划分的 ; 前端的组件化 , 方便 UI 组件的重用

{% btn 'https://codehhr.github.io/vue-daily/component.html',在线预览,far fa-hand-point-right,green larger %}

## 全局组件定义的四种方式

**注意 : 组件中的 `DOM` 结构 , 有且只能有唯一的根元素 `( Root Element )` 来进行包裹 !**

{% tabs component %}

<!-- tab 第一种 -->

### 使用 `Vue.extend` 配合 `Vue.component` 方法 :

```js
// 第一种方法
let myTitle = Vue.extend({
  template: "<h1> 我是第一种方法</h1>",
});
Vue.component("my-title", myTitle);
```

引用

```html
<my-title></my-title>
```

<!-- endtab -->

<!-- tab 第二种 -->

### 直接使用 `Vue.component` 方法 :

```js
// 第二种方法
Vue.component("my-header", {
  template: "<h1>我是第二种方法</h1>",
});
```

引用

```html
<my-header></my-header>
```

<!-- endtab -->

<!-- tab 第三种 -->

### 将模板字符串定义到 `script` 标签中 , 设置`type="x-template"` , 同时需要使用 `Vue.component` 来定义组件 :

```js
<script type="x-template" id="my-component">
  <div>
    <a href="//codehhr.cn" target="_blank">
      <h1>第三种方法</h1>
    </a>
  </div>
</script>
```

```js
// 第三种方法
Vue.component("my-component", {
  template: "#my-component",
});
```

引用

```html
<my-component></my-component>
```

<!-- endtab -->

<!-- tab 第四种 -->

### 用 `template` 标签

```html
<template id="global-component">
  <div>
    <h1>我是全局组件</h1>
    <span>{{num}}</span>
    <button @click="globalComponent">全局组件按钮</button>
  </div>
</template>
```

```js
Vue.component("global-component", {
  template: "#global-component",
});
```

引用

```html
<global-component></global-component>
```

<!-- endtab -->

{% endtabs %}

## 组件中展示数据和响应事件

在组件中 , `data` 需要被定义为一个方法

```js
Vue.component("global-component", {
  template: "#global-component",
  data() {
    return {};
  },
  methods: {},
});
```

在子组件中 , 如果将模板字符串 , 定义到了 `script` 标签中 , 那么 , 要访问子组件身上的 `data` 属性中的值 , 需要使用 `this` 来访问

## 为什么组件中的 `data` 属性必须定义为一个方法并返回一个对象

如果不用 `return` , 每个组件的 `data` 的内存都是同一个地址 , 那么一个数据改变其他数据也改变了 , 这当然就不是我们想要的 , 用 `return` 其实就相当于申明了新的变量 , 相互独立 , 自然就不会有这样的问题

## 实例

定义组件

```html
<template id="global-component">
  <div>
    <h1>我是全局组件</h1>
    <span>{{num}}</span>
    <button @click="globalComponent">全局组件按钮</button>
  </div>
</template>
```

```js
Vue.component("global-component", {
  template: "#global-component",
  data() {
    return {
      num: 1,
    };
  },
  methods: {
    globalComponent() {
      this.num++;
    },
  },
});
```

引用

```html
<global-component class="global-component"></global-component>
<global-component class="global-component"></global-component>
<global-component class="global-component"></global-component>
```

**这样各个组件的数据不会相互干扰**

## 使用 components 属性定义局部子组件

在 `Vue` 实例里用 `components` 定义局部组件

```js
let vm = new Vue({
  el: "#app",
  data: {},
  methods: {},
  // 局部组件
  components: {
    // 局部组件名
    "part-component": {
      template: "#part-component",
      data() {
        return {};
      },
      methods: {},
    },
  },
});
```

引用

```html
<part-component></part-component>
```

## 使用 flag 标识符结合 v-if 和 v-else 切换组件

定义组件

```html
<template id="part-component">
  <div>
    <!-- 使用 flag 标识符结合 v-if 和 v-else 切换组件 -->
    <h1 v-if="flag">{{partComponentMsg1}}</h1>
    <h1 v-else>{{partComponentMsg2}}</h1>
    <button @click="partComponentClick">局部组件按钮</button>
  </div>
</template>
```

```js
let vm = new Vue({
  el: "#app",
  data: {
    componentName: "part-component",
  },
  methods: {},
  // 局部组件
  components: {
    "part-component": {
      template: "#part-component",
      data() {
        return {
          flag: true,
          partComponentMsg1: "我是局部组件的数据 1",
          partComponentMsg2: "我是局部组件的数据 2",
        };
      },
      methods: {
        partComponentClick() {
          this.flag = !this.flag;
        },
      },
    },
  },
});
```

引用

```html
<part-component></part-component>
```

## 使用 `:is` 属性来切换不同的子组件

定义组件

```html
<template id="part-component">
  <div>
    <h1>>组件</h1>
    <button>组件按钮</button>
  </div>
</template>
```

在 `data` 里定义属性值

```js
let vm = new Vue({
  el: "#app",
  data: {
    componentName: "part-component",
  },
});
```

引用

```html
<!-- 使用 component 标签 , 来引用组件 , 并通过 :is 属性来指定要加载的组件 -->
<component :is="componentName"></component>  
```

## 添加切换动画

{% btn 'https://codehhr.github.io/vue-daily/component-switching.html',在线预览,far fa-hand-point-right,green larger %}

### 定义组件示例

```html
<template id="login">
  <h1>登录</h1>
</template>
<template id="register">
  <h1>注册</h1>
</template>
```

```js
Vue.component("login", {
  template: "#login",
});
Vue.component("register", {
  template: "#register",
});
```

### 使用 component 标签 , 来引用组件 , 并通过`:is` 属性来指定要加载的组件

```html
<div id="app">
  <button @click="comName='login'">登录</button>
  <button @click="comName='register'">个人中心</button>
  <transition mode="out-in">
    <component :is="comName"></component>
  </transition>
</div>
```

默认显示 `login`

```js
const vm = new Vue({
  el: "#app",
  data: {
    comName: "login",
  },
  methods: {},
});
```

### 添加切换样式

```css
.v-enter {
  opacity: 0;
  transform: translateX(-40px);
}
.v-leave-to {
  opacity: 0;
  transform: translateX(40px);
}
.v-enter-active,
.v-leave-active {
  transition: all 0.5s;
}
```
