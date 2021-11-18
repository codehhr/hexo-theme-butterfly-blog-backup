---
title: Vue slot 插槽
date: 2021-07-24 22:10:15
updated:
tags:
  - Vue
  - Vue slot 插槽
categories:
  - Vue
  - Vue 基础
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

# 什么是插槽

{% note blue no-icon flat %}
插槽就是子组件中的提供给父组件使用的一个占位符 , 用`<slot></slot>` 表示 , 父组件可以在这个占位符中填充任何模板代码 , 如 `HTML`、`组件`等 , 填充的内容会替换子组件的`<slot></slot>`标签
{% endnote %}

# 插槽的使用

## 在子组件中放一个占位符

```js
// 定义一个子组件
Vue.component("child", {
  template: "#child",
  data() {
    return {
      childMsg: "我是子组件的内容",
    };
  },
});
```

```html
<template id="child">
  <div>
    <!-- 在子组件中放一个占位符 start -->
    <slot></slot>
    <!-- 在子组件中放一个占位符 end -->
    <h1>{{childMsg}}</h1>
  </div>
</template>
```

## 在父组件中给这个占位符填充内容

```js
let vm = new Vue({
  el: "#app",
  data: {
    msg: "我是父组件的内容",
  },
  methods: {},
});
```

```html
<div id="app">
  <child>
    <!-- 在父组件中给这个占位符填充内容 start -->
    <template>
      <div>{{msg}}</div>
    </template>
    <!-- 在父组件中给这个占位符填充内容 end -->
  </child>
</div>
```

{% btn 'https://codehhr.github.io/vue-daily/slot.html',展示效果,far fa-hand-point-right,green larger %}

## 现在来看看 , 如果子组件中没有放插槽 , 同样的父组件中在子组件中填充内容 , 会是啥样的

### 子组件代码无插槽

```html
<template id="child">
  <div>
    <h1>{{childMsg}}</h1>
  </div>
</template>
```

### 父组件照常填充内容

```html
<div id="app">
  <child>
    <!-- 父组件填充内容 start -->
    <template>
      <div>{{msg}}</div>
    </template>
    <!-- 父组件填充内容 end -->
  </child>
</div>
```

**最后结果是不会渲染上去**

## 总结 : 如果子组件没有使用插槽 , 父组件如果需要往子组件中填充模板或者 `html` 是没法做到的

# 具名插槽 和 默认插槽

{% btn 'https://codehhr.github.io/vue-daily/slot-name.html',展示效果,far fa-hand-point-right,green larger %}

<div style="height:20px"></div>

{% tabs slot %}

<!-- tab 具名插槽 -->

{% note blue no-icon flat %}
描述 : 具名插槽其实就是给插槽取个名字 , 一个子组件可以放多个插槽 , 而且可以放在不同的地方 , 而父组件填充内容时 , 可以根据这个名字把内容填充到对应插槽中
{% endnote %}

## 子组件设置两个插槽 ( header , footer )

```html
<template id="child">
  <div>
    <slot name="header"></slot>
    <h1>我是子组件</h1>
    <slot name="footer"></slot>
  </div>
</template>
```

```js
Vue.component("child", {
  template: "#child",
});
```

## 父组件填充内容

```js
let vm = new Vue({
  el: "#app",
  data: {
    header: "我是父组件的 Header",
    footer: "我是父组件的 Footer",
    msg: "父组件内容,不指定插槽名字,填充到默认插槽",
  },
});
```

**父组件通过 `v-slot:name` 的方式指定到对应的插槽中**

```html
<div id="app">
  <child>
    <template v-slot:header>
      <a href="//h.codehhr.cn"><h1>{{header}}</h1></a>
    </template>
    <template v-slot:footer>
      <a href="//h.codehhr.cn"><h1>{{footer}}</h1></a>
    </template>
  </child>
</div>
```

即使父组件对插槽的填充的顺序打乱 , 只要名字对应上了 , 就可以正确渲染到对应的插槽中 , 即 : 父组件填充内容时 , 是可以根据这个名字把内容填充到对应插槽中的

<!-- endtab -->

<!-- tab 默认插槽 -->

{% note blue no-icon flat %}
描述 : 默认插槽就是指没有名字的插槽 , 子组件未定义的名字的插槽 , 父级将会把未指定插槽的填充的内容填充到默认插槽中
{% endnote %}

## 子组件代码定义了一个默认插槽

```html
<template id="child">
  <div>
    <h1>我是子组件</h1>
    <!-- 默认插槽 start -->
    <slot></slot>
    <!-- 默认插槽 end -->
  </div>
</template>
```

```js
Vue.component("child", {
  template: "#child",
});
```

## 父组件上定义一个 `msg` 变量

```js
let vm = new Vue({
  el: "#app",
  data: {
    msg: "父组件内容,不指定插槽名字,填充到默认插槽",
  },
});
```

## 父组件给默认插槽填充内容

```html
<div id="app">
  <child>
    <template>
      <a href="//h.codehhr.cn"><h1>{{msg}}</h1></a>
    </template>
    <!-- 父级的填充内容如果指定到子组件的没有对应名字插槽 , 那么该内容不会被填充到默认插槽中 -->
    <!-- 这里指定 body 名字的内容就不会填充到默认插槽里 -->
    <template v-slot:body>
      <a href="//h.codehhr.cn"><h1>{{msg}}</h1></a>
    </template>
  </child>
</div>
```

<!-- endtab -->

{% endtabs %}

## 总结

- 父级的填充内容如果指定到子组件的没有对应名字插槽 , 那么该内容 `不会` 被填充到默认插槽中
- 如果子组件没有默认插槽 , 而父级的填充内容指定到默认插槽中 , 那么该内容就 `不会` 填充到子组件的任何一个插槽中
- 如果子组件有多个默认插槽 , 而父组件所有指定到默认插槽的填充内容 , 将 `会` `全都` 填充到子组件的每个默认插槽中
