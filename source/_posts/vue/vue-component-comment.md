---
title: Vue 评论小案例
date: 2021-07-25 16:40:49
updated:
tags:
  - vue
categories:
  - vue
  - vue基础
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

# 效果

{% btn 'https:/vue-daily.netlify.app/vue-component-comment.html',在线预览,far fa-hand-point-right,green larger %}

# 代码

{% hideToggle Vue 评论小案例 %}

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link
      href="https://cdn.bootcdn.net/ajax/libs/twitter-bootstrap/3.4.1/css/bootstrap.css"
      rel="stylesheet"
    />
    <script src="https://cdn.bootcdn.net/ajax/libs/vue/2.6.14/vue.js"></script>

    <style>
      .container {
        margin: 60px auto;
        overflow: hidden;
      }
      button {
        outline: none !important;
      }
      .comment-list {
        margin: 10px 0;
      }
      td {
        padding: 10px !important;
      }
    </style>
  </head>

  <body>
    <div id="app">
      <div class="container">
        <div class="panel panel-info">
          <div class="panel-heading">
            <h3 class="panel-title">Vue 评论小案例</h3>
          </div>
          <div class="panel-body">
            <!-- 引用提交评论组件 start -->
            <commit-comment @func="getDataFromCommit"></commit-comment>
            <!-- 引用提交评论组件 end -->

            <!-- 评论列表 start -->
            <table class="table table-striped table-hover">
              <tbody>
                <tr v-for="(item,index) in list" :key="index">
                  <td>
                    <span class="pull-left">{{item.comment}}</span>
                    <span class="badge pull-right">{{item.username}}</span>
                  </td>
                </tr>
              </tbody>
            </table>
            <!-- 评论列表 end -->
          </div>
        </div>
      </div>
    </div>

    <!-- 提交评论组件 start -->
    <template id="commit-comment">
      <div class="comment-list">
        <div class="form-group">
          <!-- <label for="username"></label> -->
          <input
            id="username"
            type="text"
            class="form-control"
            v-model="username"
            placeholder="用户名"
          />
        </div>
        <div class="form-group">
          <!-- <label for="comment"></label> -->
          <textarea
            id="comment"
            class="form-control"
            v-model="comment"
            placeholder="评论内容"
          ></textarea>
        </div>
        <div class="form-group">
          <button class="btn btn-info" @click="addComment">发表评论</button>
        </div>
      </div>
    </template>
    <!-- 提交评论组件 end -->

    <script>
      let vm = new Vue({
        el: "#app",
        data: {
          list: [],
        },
        methods: {
          getDataFromCommit() {
            this.list = JSON.parse(localStorage.getItem("commentList") || "[]");
          },
        },
        created() {
          // 确保拿到的是个数组,不然遍历会报错
          if (
            Array.isArray(
              JSON.parse(localStorage.getItem("commentList") || "[]")
            )
          ) {
            this.getDataFromCommit();
          } else {
            return;
          }
        },
        components: {
          "commit-comment": {
            template: "#commit-comment",
            data() {
              return {
                username: "",
                comment: "",
              };
            },
            methods: {
              addComment() {
                if (!this.username || !this.comment) {
                  alert("兄弟 , 空着呢 ~");
                } else {
                  // 从本地缓存拿出 commentList
                  let commentList = JSON.parse(
                    localStorage.getItem("commentList") || "[]"
                  );

                  // 数组首部分加入新的数据
                  commentList.unshift({
                    username: this.username,
                    comment: this.comment,
                  });

                  // 把新的数组存入本体缓存
                  localStorage.setItem(
                    "commentList",
                    JSON.stringify(commentList)
                  );

                  this.username = this.comment = "";
                  this.$emit("func");
                }
              },
            },
          },
        },
      });
    </script>
  </body>
</html>
```

{% endhideToggle %}
