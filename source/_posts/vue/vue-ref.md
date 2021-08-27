---
title: Vue ref 的使用
date: 2021-07-25 17:27:02
updated:
tags:
categories:
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

# 获取 dom 节点

- 给 `dom` 节点记上 `ref` 属性 , 可以理解为给 `dom` 节点起了个名字
- 加上 `ref` 之后 , 在 `$refs` 属性中多了这个元素的引用
- 通过 `Vue` 实例的 `$refs` 属性拿到这个 `dom` 元素

# 获取组件

- 给组件记上 `ref` 属性 , 可以理解为给组件起了个名字
- 加上 `ref` 之后 , 在 `$refs` 属性中多了这个组件的引用
- 通过 `Vue` 实例的 `$refs` 属性拿到这个组件的引用 , 之后可以通过这个引用调用子组件的方法 , 或者获取子组件的数据

# 在线预览

{% btn 'https:/vue-daily.netlify.app/ref.html',在线预览,far fa-hand-point-right,green larger %}

# 代码

{% hideToggle Vue ref 的使用 %}

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <script src="https://cdn.bootcdn.net/ajax/libs/vue/2.6.14/vue.js"></script>
    <!-- <script src='https://codehhr.github.io/web/vue.js'></script> -->
  </head>
  <body>
    <div id="app">
      <button ref="btn" id="btn">按钮</button>
      <my-template ref="mycomponent" id="my-component"></my-template>
    </div>

    <template id="my-template">
      <div>
        <h1>组件</h1>
      </div>
    </template>
    <script>
      Vue.config.devtools = true;
      Vue.component("my-template", {
        template: "#my-template",
        data() {
          return {
            msg: "myComponent",
          };
        },
      });
      let vm = new Vue({
        el: "#app",
        data: {},
        methods: {},
        mounted() {
          console.log(document.querySelector("#btn"));
          console.log(this.$refs.btn);
          console.log(document.querySelector("#my-component"));
          console.log(this.$refs.mycomponent.msg);
        },
      });
    </script>
  </body>
</html>
```

{% endhideToggle %}
