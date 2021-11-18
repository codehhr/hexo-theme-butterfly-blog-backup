---
title: Vue 中路由的使用
date: 2021-07-25 17:36:06
updated:
tags:
  - Vue
  - Vue-router
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

# 什么是路由

- 后端路由 : 对于普通的网站 , 所有的超链接都是 URL 地址 , 所有的 `URL` 地址都对应服务器上对应的资源
- 前端路由 : 对于单页面应用程序来说 , 主要通过 URL 中的 `hash` ( `#` 号 ) 来实现不同页面之间的切换 , 同时 , `hash` 有一个特点 : `HTTP` 请求中不会包含 `hash` 相关的内容 ; 所以 , 单页面程序中的页面跳转主要用 `hash` 实现;
- 在单页面应用程序中 , 这种通过 `hash` 改变来切换页面的方式 , 称作前端路由 ( 区别于后端路由 )

{% btn 'https://router.vuejs.org/zh/',中文官网,far fa-hand-point-right,green larger %}

# 路由的基本使用

- 引入 `js` 文件 , 这个 `js` 需要放在 `vue.js`的后面 , 自动安装 ( 提供了一个 `VueRouter` 的构造方法 )
- 创建路由 `new VueRouter()` , 接受的参数是一个对象
- 在实例化的对象里配置属性 `routes:[]` , 这个数组里的对象包含 `path` 属性和 `component` 属性
- `path` 属性是 `url` , `component` 属性就是显示的组件 ( 传组件的对象 )
- 创建的路由需要和 `vue` 实例关联一下
- 路由到的组件显示在哪个位置 `<router-view></router-view>`

## 示例

引入 `vue-router.js`

```html
<script src="https://cdn.bootcdn.net/ajax/libs/vue/2.6.14/vue.js"></script>
<script src="https://cdn.bootcdn.net/ajax/libs/vue-router/3.5.2/vue-router.js"></script>
```

```html
<body>
  <div id="app">
    <!-- 通过路由切换的组件会显示在这里 -->
    <router-view></router-view>
  </div>

  <template id="login">
    <div>
      <h1>登录</h1>
    </div>
  </template>

  <script>
    const login = {
      template: "#login",
    };

    // 这里实例化了一个路由
    const router = new VueRouter({
      routes: [
        {
          path: "/login",
          //这里需要注意的是直接把组件的对象放在这里
          component: login,
        },
      ],
    });

    let vm = new Vue({
      el: "#app",
      // 把路由挂在到实例上
      router: router,
    });
  </script>
</body>
```

# 路由的跳转

- `router-link` 标签可以设置 `to` 属性
- 默认是 `a` 标签 , 可以通过 `tag` 设置包裹标签

**示例**

```html
<router-link to="/login">登录</router-link>
<router-link to="/register">注册</router-link>
```

# 路由重定向

`redirect` 可以进行路由的重定向

{% btn 'https://vue-daily.netlify.app/vue-router.html',在线演示,far fa-hand-point-right,green larger %}

```html
<template id="home">
  <div><h1>Home</h1></div>
</template>
<template id="blog">
  <div><h1>Blog</h1></div>
</template>
```

```js
let home = {
    template: "#home",
};
}
let blog = {
    template: "#blog",
};

const router = new VueRouter({
  routes: [
    {
      path: "/home",
      redirect: "/blog",
    },
    {
      path: "/blog",
      component: blog,
    },
  ],
});
```

# 选中路由高亮

{% btn 'https://vue-daily.netlify.app/vue-router.html',在线演示,far fa-hand-point-right,green larger %}

- 使用默认的样式
  直接设置 `.router-link-active`
- 自定义样式
  配置  `linkActiveClass:'自定义的类名'`

```js
const router = new VueRouter({
  routes: [
    {
      path: "/index",
      component: index,
    },
  ],
  linkActiveClass: "router-active",
});
```

# 定义参数

## 通过 `query` 的方式在 `url` 后加 `?参数名=参数的值`

获取参数 : `$route.query.参数名`

## 使用浏览器参数的方式传递参数

- 设置路由的时候 `/路由地址/:参数名`
- 获取参数 `$route.params.参数名`

# 示例

{% hideToggle 路由传惨 %}

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <script src="https://cdn.bootcdn.net/ajax/libs/vue/2.6.14/vue.js"></script>
    <script src="https://cdn.bootcdn.net/ajax/libs/vue-router/3.5.2/vue-router.js"></script>
    <!-- <script src='https://codehhr.github.io/web/vue.js'></script> -->
    <style>
      #app {
        margin: 100px auto;
        width: 1200px;
      }
      .router-link-active {
        font-size: 2rem;
        color: #ffffff;
        background-color: #5e6466;
      }
      a {
        margin: 0 2px;
      }
      a.router-active {
        font-weight: 800;
        font-size: 2rem;
        color: #ffffff;
        background-color: #5e6466;
      }
    </style>
  </head>
  <body>
    <div id="app">
      <router-link to="/index">Index</router-link>
      <router-link to="/home">Home</router-link>
      <router-link to="/blog?categories=vue&tag=vue-touter">Blog</router-link>
      <!-- <router-link :to="{path:'/about?page=2'}">About</router-link> -->
      <router-link
        :to="{path:'/about',query:{
          id:1,
          page:2
      }}"
        >About</router-link
      >
      <!-- 观察地址变化 -->
      <router-link
        v-for="(item,index) in list"
        :key="item.id"
        :to="{
        path:'/about',
        query:{id:item.id,page:item.content}
      }"
      >
        {{item.content}}
      </router-link>

      <router-link :to="{name:'detail',params:{id:2}}">Detail</router-link>
      <router-view></router-view>
    </div>

    <template id="index">
      <div><h1>Index</h1></div>
    </template>
    <template id="home">
      <div><h1>Home</h1></div>
    </template>
    <template id="about">
      <div><h1>About</h1></div>
    </template>
    <template id="blog">
      <div><h1>Blog</h1></div>
    </template>
    <template id="detail">
      <div>
        <h1>Detail</h1>
      </div>
    </template>

    <script>
      let index = {
        template: "#index",
      };
      let home = {
        template: "#home",
      };
      let about = {
        template: "#about",
        created() {
          console.log(this.$route.query);
        },
      };
      let blog = {
        template: "#blog",
        created() {
          console.log(this.$route.query);
        },
      };
      let detail = {
        template: "#detail",
        created() {
          console.log(this.$route.params);
        },
      };

      const router = new VueRouter({
        routes: [
          {
            path: "/index",
            component: index,
          },
          {
            path: "/home",
            component: home,
          },
          {
            path: "/blog",
            component: blog,
          },
          {
            path: "/about",
            component: about,
          },
          {
            path: "/detail/:id",
            component: detail,
            name: "detail",
          },
        ],
        linkActiveClass: "router-active",
      });

      let vm = new Vue({
        el: "#app",
        data: {
          list: [
            { id: 1, content: "A" },
            { id: 2, content: "B" },
            { id: 3, content: "C" },
          ],
        },
        methods: {},
        // 把路由挂在到实例上
        router,
      });
    </script>
  </body>
</html>
```

{% endhideToggle %}
