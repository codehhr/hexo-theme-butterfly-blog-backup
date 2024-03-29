---
title: Vue 路由守卫
date: 2021-07-31 20:27:13
updated:
tags:
  - Vue
  - Vue-router
  - beforeEach
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

# 全局前置守卫

你可以使用 `router.beforeEach` 注册一个全局前置守卫

```js
const router = new VueRouter({ ... })

router.beforeEach((to, from, next) => {
  // ...
})
```

当一个导航触发时 , 全局前置守卫按照创建顺序调用,守卫是异步解析执行 , 此时导航在所有守卫 `resolve` 完之前一直处于 等待中

**每个守卫方法接收三个参数 :**

- `to: Route`: 即将要进入的目标 `路由对象`
- `from: Route`: 当前导航正要离开的路由
- `next: Function`: 一定要调用该方法来 `resolve` 这个钩子,执行效果依赖 `next` 方法的调用参数
- `next()`: 进行管道中的下一个钩子,如果全部钩子执行完了 , 则导航的状态就是 `confirmed` (确认的)
  - `next(false)`: 中断当前的导航,如果浏览器的 `URL` 改变了 (可能是用户手动或者浏览器后退按钮) , 那么 `URL` 地址会重置到 `from` 路由对应的地址
  - `next('/')` 或者 `next({ path: '/' })`: 跳转到一个不同的地址,当前的导航被中断 , 然后进行一个新的导航,你可以向 `next` 传递任意位置对象 , 且允许设置诸如 `replace: true`、`name: 'home'` 之类的选项以及任何用在 `router-link` 的 `to` `prop` 或 `router.push` 中的选项
  - `next(error)`: `(2.4.0+)` 如果传入 `next` 的参数是一个 `Error` 实例 , 则导航会被终止且该错误会被传递给 `router.onError()` 注册过的回调

**确保 `next` 函数在任何给定的导航守卫中都被严格调用一次 , 它可以出现多于一次 , 但是只能在所有的逻辑路径都不重叠的情况下，否则钩子永远都不会被解析或报错** , 这里用一个在用户未能验证身份时重定向到 `/login` 的示例

**错误示范**

```js
// 错误示范
router.beforeEach((to, from, next) => {
  if (to.name !== "Login" && !isAuthenticated) next({ name: "Login" });
  // 如果用户未能验证身份,则 next 会被调用两次,这是不对的
  next();
});
```

**正确示范**

```js
// 正确示范
router.beforeEach((to, from, next) => {
  if (to.name !== "Login" && !isAuthenticated) {
    next({ name: "Login" });
  } else {
    next();
  }
});
```

# 路由独享的守卫

你可以在路由配置上直接定义 `beforeEnter` 守卫 :
这些守卫与全局前置守卫的方法参数是一样的

```js
const router = new VueRouter({
  routes: [
    {
      path: "/foo",
      component: Foo,
      beforeEnter: (to, from, next) => {
        // ...
      },
    },
  ],
});
```
