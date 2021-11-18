---
title: Vue 组件复用
date: 2021-07-24 21:36:16
updated:
tags:
  - Vue
  - Vue 组件复用
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

# 可能因 `http` 的原因无法正常显示,那就看代码吧

{% btn 'https://vue-daily.netlify.app/component-reuse.html',效果预览,far fa-hand-point-right,green larger %}

# 代码

{% hideToggle 组件复用 %}

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <script src="https://cdn.bootcdn.net/ajax/libs/vue/2.6.14/vue.min.js"></script>
    <script src="https://cdn.bootcdn.net/ajax/libs/axios/0.21.1/axios.js"></script>
    <style>
      #app {
        margin: 100px auto;
        width: 1200px;
      }
      .course-list {
        margin: 20px 0;
        display: flex;
        align-items: center;
        justify-content: space-between;
        flex-wrap: wrap;
      }
      h1 {
        text-align: center;
      }
      .course-item {
        margin: 2px;
        width: 234px;
        height: 140px;
      }
      .cover {
        height: 122px;
        overflow: hidden;
      }
    </style>
  </head>
  <body>
    <div id="app">
      <course-list type="free" page-Size="10">
        <template v-slot:course-title>
          <div><h1>免费课程</h1></div>
        </template>
      </course-list>
      <course-list type="boutique">
        <template v-slot:course-title>
          <div><h1>精品课程</h1></div>
        </template>
      </course-list>
      <course-list type="discount">
        <template v-slot:course-title>
          <div><h1>限时折扣课程</h1></div>
        </template>
      </course-list>
    </div>

    <template id="course-list">
      <div>
        <slot name="course-title"></slot>
        <div class="course-list">
          <div class="course-item" v-for="(item,index) in courselist">
            <div class="cover"><img :src="item.coverFileUrl" alt="" /></div>
          </div>
        </div>
      </div>
    </template>

    <script>
      http: Vue.component("course-list", {
        template: "#course-list",
        data() {
          return {
            courseApi:
              "http://wkt.myhope365.com/weChat/applet/course/list/type",
            courselist: [],
          };
        },
        props: {
          type: [String, Number],
          pageSize: {
            type: [String, Number],
            default: 5,
          },
          pageNum: {
            type: [String, Number],
            default: 1,
          },
        },
        methods: {
          getCourseList() {
            let formData = new FormData();
            formData.append("type", this.type);
            formData.append("pageNum", this.pageNum);
            formData.append("pageSize", this.pageSize);
            axios.post(this.courseApi, formData).then((res) => {
              this.courselist = res.data.rows;
            });
          },
        },
        created() {
          this.getCourseList();
        },
      });

      let vm = new Vue({
        el: "#app",
        data: {},
        methods: {},
      });
    </script>
  </body>
</html>
```

{% endhideToggle %}
