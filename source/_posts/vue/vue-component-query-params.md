---
title: Vue 父子组件互相传值
date: 2021-07-25 15:16:48
updated:
tags:
  - Vue
  - Vue 组件
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

# Vue 父子组件互相传值

{% tabs components %}

<!-- tab  父组件传值子组件 -->

{% btn 'https://vue-daily.netlify.app/father-to-son.html',在线演示,far fa-hand-point-right,green larger %}

{% note blue no-icon flat %}
设置 `props` 属性就可以接受父组件传值
{% endnote %}

## 父组件

```html
<div id="app">
  <child :parent-msg="msg"></child>
</div>
```

在父组件 `data` 上定义一个 `msg` , 用于传递给子组件

```js
let vm = new Vue({
  el: "#app",
  data: {
    msg: "父组件内容",
  },
  methods: {},
});
```

## 子组件

顺便定义一个方法 , 用来触发拿到父组件传的值 , 当然也可以直接写在 `created` 里

```html
<template id="child">
  <div>
    <h1>我是子组件</h1>
    <button @click="getDateFromParent">子组件按钮</button>
  </div>
</template>
```

### props 设置传递类型 ( 三种方式 )

可以设置多个类型 , 可以传 `Number` 也可以传 `String`

**第一种方式**

```js
parentMsg: String;
```

**第二种方式**

```js
parentMsg: [String, Number],
```

**第三种方式**

需要注意的是 , 当类型是 `Object` 或者 `Array` , 默认值必须是一个函数

```js
parentMsg: {
    type: [String, Number],
    default() {
        return {};
    },
},
```

### 示例

```js
Vue.component("child", {
  template: "#child",
  data() {
    return {};
  },
  props: {
    parentMsg: {
      type: [String, Number],
      default() {
        return {};
      },
    },
  },
  methods: {
    getDateFromParent() {
      console.log(this.parentMsg);
    },
  },
});
```

## 注意事项

**data 和 props 的区别 :**

`data` 是组件私有的 , `props` 是父组件传过来的
`data` 是可以修改的 , `props` 是只读的

<!-- endtab  -->

<!-- tab 子组件传值父组件 -->

{% btn 'https://vue-daily.netlify.app/son-to-father.html',在线演示,far fa-hand-point-right,green larger %}

**子组件调用父组件的方法**

- 在父组件中给引用的子组件注册一个事件 ( 事件名是自定义的 )
- 子组件可以触发这个事件 `$emit('事件名字')`

**子组件给父组件传递数据**

- `$emit` 方法第二个参数可以定义子组件给父组件传递的内容
- 在父组件中怎么拿到这内容
  - 父组件这个方法没有自定参数 , 在父组件的方法中直接加个参数就可以拿到
  - 父组件有自定义参数 , 可以传入 `$event` 拿到子组件传递的数据 , 通过 `$event` 只能传递第一个参数

## 示例

### 子组件

```html
<template id="child">
  <div>
    <button @click="childBtn">子组件按钮</button>
  </div>
</template>
```

```js
Vue.component("child", {
  template: "#child",
  data() {
    return {};
  },
  methods: {
    childBtn() {
      this.$emit("passingdatatoparent", "我是子组件内容");
    },
  },
});
```

### 父组件

```html
<div id="app">
  <child @passingDataToParent="getDataFromChild"></child>
</div>
```

```js
let vm = new Vue({
  el: "#app",
  data: {
    msg: "",
  },
  methods: {
    getDataFromChild(data) {
      console.log(data);
    },
  },
});
```

<!-- endtab -->

{% endtabs %}

# The_End
