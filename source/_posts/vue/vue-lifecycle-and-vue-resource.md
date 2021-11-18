---
title: Vue 生命周期 和 Vue-resource
date: 2021-07-21 14:50:30
updated:
tags:
  - Vue
  - Vue 生命周期
  - Vue-resource
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

# 什么是生命周期

从 `Vue` 实例创建 , 运行 , 到销毁期间 , 总是伴随着各种各样的事件 , 这些事件 , 统称为生命周期 !

# vue 生命周期钩子函数

每个 `Vue` 实例在被创建时都要经过一系列的初始化过程——例如 , 需要设置数据监听 , 编译模板 , 将实例挂载到 `DOM` 并在数据变化时更新 `DOM` 等 , 同时在这个过程中也会运行一些叫做生命周期钩子的函数 , 这给了用户在不同阶段添加自己的代码的机会

**`生命周期函数`=`生命周期事件`=`生命周期钩子`**

# vue 生命周期

![vue 生命周期](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/vuebasic/vuelifecycle.png)

**详解**

![vue 生命周期](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/vuebasic/vuelifecycledetail.png)

{% hideToggle Vue生命周期函数 %}

```html
<!-- 引入 Vue -->
<script src="https://cdn.bootcdn.net/ajax/libs/vue/2.6.14/vue.js"></script>

<div id="app">{{msg}}</div>

<script>
  let vm = new Vue({
    el: "#app",
    data: {
      msg: "Hello World",
    },
    methods: {},
    beforeCreate() {
      // 这是我们遇到的第一个生命周期函数
      // 在 beforeCrate 生命周期函数执行的时候, data 和 methods 中的数据还没初始化
      console.log("beforeCreate");
      console.log(this.msg); // -> undefined
    },
    created() {
      // 此时 data 和 methods 中的数据已经好了始化
      // 如果要调用 methods 中的方法或操作 data 里的数据,最早只能在 created 中操作
      console.log("created");
      console.log(this.msg); // -> Hello World
    },
    beforeMount() {
      // 此时模板已在内存中编译好了,还未渲染到页面上,页面还是旧的
      console.log("beforeMount");
    },
    mounted() {
      // 执行完 mounted ,就表示这个 Vue 示例已经初始化完毕了
      // 如果要通过某些插件操作页面上的 DOM 节点,最早要在 mounted 中进行
      console.log("mounted");
    },
    beforeUpdate() {
      // 当 data 里的数据改变后会执行 beforeUpdate
      // 此时页面显示的数据还是旧的, data 里的数据是最新的,页面尚未和数据保持同步
      console.log("beforeUpdate");
    },

    // beforeUpdate 执行后,在内存里会渲染出一份最新的 内存 DOM 树,会重新渲染到真是的页面上去
    // 这时候,就完成了数据从 data(model层) -> view(视图层) 的更新

    updated() {
      // updated 执行的时候,页面和 data 数据已经保持同步了,都是最新的
      console.log("updated");
    },
    beforeDestroy() {
      // 准备销毁实例
      // 此时还没有真正的执行销毁,还处于可用的状态
    },
    destroyed() {
      // 当执行到 destroyed函数的时候,组件已经被完全销毁了,data,methods,指令,过滤器...已经不可用了
    },
  });
</script>
```

{% endhideToggle %}

# vue-resource 的使用

- 直接在页面中 , 通过 `script` 标签 , 引入 `vue-resource` 的脚本文件 ;
- 注意：引用的先后顺序是: 先引用 `Vue` 的脚本文件 , 再引用 `vue-resource` 的脚本文件

```html
<!-- 引入 vue.js -->
<script src="https://cdn.bootcdn.net/ajax/libs/vue/2.6.14/vue.js"></script>
<!-- 引入 vue-resource.js -->
<script src="https://cdn.bootcdn.net/ajax/libs/vue-resource/1.5.3/vue-resource.js"></script>
```

**如果想在页面加载的时候就请求,可以写在 `update` 生命周期函数里**

## get 请求

```js
// get 请求
this.$http
  .get("http://wkt.myhope365.com/weChat/applet/course/banner/list?number=2")
  .then((res) => {
    console.log(res);
  })
  .catch((e) => {
    console.log(e);
  });
```

## post 请求

```js
// post请求
// post 方法接收三个参数：
//    参数1： 要请求的 URL 地址
//    参数2： 要发送的数据对象
//    参数3： 指定 post 提交的编码类型为 application/x-www-form-urlencoded 或 application/json
this.$http
  .post(
    "http://wkt.myhope365.com/weChat/applet/subject/list",
    { enable: 1 },
    { emulateJSON: false }
  )
  .then((res) => {
    console.log(res);
  });
```

# The_End
