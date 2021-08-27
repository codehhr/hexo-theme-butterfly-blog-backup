---
title: Vue 中的动画
date: 2021-07-22 21:24:20
updated:
tags:
  - Vue
  - Vue 过渡动画
categories:
  - Vue
  - Vue基础
keywords:
description:
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/sunrise.jpg
cover: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/vue/animate-cover.jpg
comments:
copyright:
copyright_author:
copyright_author_href:
copyright_url:
copyright_info:
---

# 推荐使用第三方 css 动画库

{% tabs animate %}

<!-- tab 使用过渡类名 -->

## 使用过渡类名

{% btn 'https://codehhr.github.io/vue-daily/vue-transition-class.html',在线预览,far fa-hand-point-right,green larger %}

![transition](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/vue/transition.png)

```html
<script src="https://cdn.bootcdn.net/ajax/libs/vue/2.6.13/vue.min.js"></script>

<div id="app">
  <button @click="myAnimate">按钮</button>
  <transition name="fade">
    <div class="div" v-show="isShow">动画</div>
  </transition>
</div>

<script>
  let vm = new Vue({
    el: "#app",
    data: {
      isShow: false,
    },
    methods: {
      myAnimate() {
        this.isShow = !this.isShow;
      },
    },
  });
</script>
```

**定义两组类样式**

```css
#app {
  margin: 100px auto;
  width: 600px;
}
button {
  padding: 10px 20px;
  outline: none;
}
.div {
  margin: 20px 0;
  padding: 20px;
  width: 200px;
  text-align: center;
  color: #ffffff;
  background-color: #494f5c;
  font-size: 24px;
}
/* 入场动画开始和出场动画结束 */
.fade-enter {
  opacity: 0;
  transform: translateX(-200px);
}
/* 整个入场动画和出场动画过程 */
.fade-enter-active,
.fade-leave-active {
  transition: all 0.6s;
}
```

<!-- endtab -->

<!-- tab 第三方css动画库 -->

## 使用第三方 css 动画库

{% btn 'https://codehhr.github.io/vue-daily/vue-animate.css.html',在线预览,far fa-hand-point-right,green larger %}

Vue 官网推荐的是 `Animate.css`

{% btn 'https://animate.style/',Animate 官网,far fa-hand-point-right,orange larger %}

![animate.style](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/vue/animate.style.png)

### 引入动画类库

```html
<link
  rel="stylesheet"
  href="https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css"
/>
```

### 给标签加入 animate 类名

```html
<h1 class="animate__animated animate__bounce">Animate</h1>
```

<!-- endtab -->

<!-- tab 使用动画钩子函数 -->

## 使用动画钩子函数

{% btn 'https://codehhr.github.io/vue-daily/vue-animation-hook-function.html',在线预览,far fa-hand-point-right,green larger %}

### 定义 transition 组件以及三个钩子函数

```html
<div id="app">
  <button @click="isShow = !isShow">点我</button>  
  <transition
    @before-enter="beforeEnter"
    @enter="enter"
    @after-enter="afterEnter"
  >
    <div v-if="isShow" class="show">OK</div>
  </transition>
</div>
```

### 定义三个 methods 钩子方法

**注意 : `enter` 函数里的 `el.offsetHeight` 和 `el.offsetWidth` 至少要有一个**

```js
let vm = new Vue({
  el: "#app",
  data: {
    isShow: false,
  },
  methods: {
    beforeEnter(el) {
      // 动画进入之前的回调函数
      el.style.transform = "translateX(500px)";
    },
    enter(el, done) {
      // 动画进入完成时候的回调函数
      el.offsetWidth;
      // el.offsetHeight;
      el.style.transform = "translateX(0px)";
      done();
    },
    afterEnter(el) {
      // 动画进入完成之后的回调函数
      this.isShow = !this.isShow;
      // el.style.opacity = 0;
    },
  },
});
```

<!-- endtab -->

<!-- tab v-for的列表过渡 -->

## v-for 的列表过渡

{% btn 'https://codehhr.github.io/vue-daily/v-for-list-transition-animation.html',在线预览,far fa-hand-point-right,green larger %}

### 定义过渡样式

```css
.list-enter,
.list-leave-to {
  opacity: 0;
  transform: translateY(10px);
}
.list-enter-active,
.list-leave-active {
  transition: all 0.6s;
}
```

### 使用 transition-group 组件把 v-for 循环的列表包裹起来

```html
<div id="app">
    <input type="text" v-model="text" @keyup.enter="add" />  
  <transition-group tag="ul" name="list">
    <li v-for="(item, index) in list" :key="index">{{item}}</li>
  </transition-group>
</div>
```

### 创建 Vue 实例

```js
let vm = new Vue({
  el: "#app",
  data: {
    text: "",
    list: [1, 2, 3, 4],
  },
  methods: {
    add() {
      this.list.push(this.text);
      this.text = "";
    },
  },
});
```

<!-- endtab -->

{% endtabs %}
