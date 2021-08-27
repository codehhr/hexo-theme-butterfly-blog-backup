---
title: Vue 品牌管理小案例
date: 2021-07-21 14:45:50
updated:
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

{% btn 'https://codehhr.github.io/vue-daily/brand-managment.html',在线预览,far fa-hand-point-right,green larger %}

{% hideToggle Vue 简单的品牌管理案例 %}

```html
<script src="https://cdn.bootcdn.net/ajax/libs/vue/2.6.14/vue.js"></script>
<link
  href="https://cdn.bootcdn.net/ajax/libs/twitter-bootstrap/3.4.1/css/bootstrap.css"
  rel="stylesheet"
/>

<style>
  .container {
    margin: 60px auto;
  }
  .form-group {
    margin: 0 20px;
  }
  th,
  td {
    text-align: center;
    line-height: 50px !important;
  }
</style>

<div id="app">
  <div class="container">
    <div class="panel panel-info">
      <div class="panel-heading">
        <h3 class="panel-title">品牌管理</h3>
      </div>
      <div class="panel-body">
        <form action="" method="POST" class="form-inline" role="form">
          <div class="form-group">
            <label for="search">搜索</label>
            <input
              id="search"
              type="text"
              class="form-control"
              placeholder="请输入品牌关键字"
              v-model:value="keyword"
              @change="showBrandList"
            />
          </div>
          <div class="form-group">
            <label for="name">名字</label>
            <input
              id="name"
              type="text"
              class="form-control"
              placeholder="请输入品牌名字"
              v-model:value="name"
            />
          </div>

          <button type="button" class="btn btn-primary" @click="addBrand">
            添加
          </button>
        </form>
      </div>

      <table class="table table-striped table-bordered">
        <thead>
          <tr>
            <th>ID</th>
            <th>NAME</th>
            <th>Time</th>
            <th>OPTION</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(item,index) in showBrandList()">
            <td>{{index+1}}</td>
            <td>{{item.name}}</td>
            <td>{{item.time | timeFilter("YYYY-MM-DD hh:mm:ss")}}</td>
            <td>
              <button
                type="button"
                class="btn btn-danger"
                @click="delBrand(index)"
              >
                删除
              </button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</div>

<script>
  let vm = new Vue({
    el: "#app",
    data: {
      name: "",
      keyword: "",
      brandList: JSON.parse(localStorage.getItem("brandList")) || [
        { name: "迈凯轮", time: new Date() },
        { name: "科尼赛格", time: new Date() },
        { name: "兰博基尼", time: new Date() },
        { name: "BMW", time: new Date() },
      ],
    },
    created() {},
    methods: {
      // 显示
      showBrandList() {
        // this.brandList = localStorage.getItem("brandList");
        return this.brandList.filter((item) => {
          return item.name.includes(this.keyword);
        });
      },
      // 添加
      addBrand() {
        if (this.name) {
          this.brandList.push({
            name: this.name,
            time: new Date(),
          });
          localStorage.setItem("brandList", JSON.stringify(this.brandList));
          this.name = "";
        } else {
          alert("空");
        }
      },
      // 删除
      delBrand(index) {
        this.brandList.splice(index, 1);
        localStorage.setItem("brandList", JSON.stringify(this.brandList));
      },
    },
    filters: {
      //定义过滤器 , 格式化时间
      timeFilter(nothing, dateFormat) {
        let date = new Date();
        return dateFormat
          .replace("YYYY", date.getFullYear())
          .replace("MM", (date.getMonth() + 1).toString().padStart(2, "0"))
          .replace("DD", date.getDate().toString().padStart(2, "0"))
          .replace("hh", date.getHours().toString().padStart(2, "0"))
          .replace("mm", date.getMinutes().toString().padStart(2, "0"))
          .replace("ss", date.getSeconds().toString().padStart(2, "0"));
      },
    },
  });
</script>
```

{% endhideToggle %}
