---
title: Vue 打包优化
date: 2021-11-18 22:16:21
updated:
tags:
  - Vue
  - vue优化
categories:
  - Vue
  - Vue 脚手架
keywords:
description:
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/sunrise.jpg
cover: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/vue/vue.jpg
comments:
copyright:
copyright_author:
copyright_author_href:
copyright_url:
copyright_info:
---

# 生成打包页面

在 `package.json` 文件里的 `build` 命令后面添加 `--report`

```js
"build": "vue-cli-service build --report",
```

或者在使用 `build` 命令时加上 `--report`

```sh
npm run build --report
```

# 安装打包分析插件

**webpack-bundle-analyzer 的 [Github](https://github.com/webpack-contrib/webpack-bundle-analyzer)**

```sh
npm install --save-dev webpack-bundle-analyzer
```

## 配置 vue 打包配置文件

在 `vue.config.js` 里对应添加以下内容

```js
const BundleAnalyzerPlugin =
  require("webpack-bundle-analyzer").BundleAnalyzerPlugin;

module.exports = {
  publicPath: "./", // 使用相对路径
  configureWebpack: {
    plugins: [new BundleAnalyzerPlugin()],
  },
};
```

当再用 `npm run build` 的时候就会生成一个有关各模块大小的 `html` 页面, 也可以在控制台看到打包出来的 `js` 文件大小, 如下图

![build-report](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/vue/build-report.png)

# 利用引入 `cdn` 的方式来减小打包体积

## 首先在 `vue.config.js` 里的 `configureWebpack` 里添加 `externals` 配置

其属性对应的是导入过的模块, 值对应的是模块暴露的全局变量

```js
const BundleAnalyzerPlugin =
  require("webpack-bundle-analyzer").BundleAnalyzerPlugin;

module.exports = {
  configureWebpack: {
    externals: {
      vue: "Vue",
      "vue-router": "VueRouter",
      vuex: "Vuex",
      "element-ui": "ELEMENT",
      axios: "axios",
    },
    plugins: [new BundleAnalyzerPlugin()],
  },
};
```

这样在打包的时候就不会把 `main.js` 里对应的 `import` 的模块打包进去

## 引入 `cdn`

[**bootcdn**](https://www.bootcdn.cn/)

在 `public` 目录里的 `index.html` 里添加对应的 `cdn` 链接

```html
<script src="https://cdn.bootcdn.net/ajax/libs/vue/2.6.14/vue.min.js"></script>
<script src="https://cdn.bootcdn.net/ajax/libs/vue-router/3.5.2/vue-router.min.js"></script>
<script src="https://cdn.bootcdn.net/ajax/libs/vuex/3.6.2/vuex.min.js"></script>
<script src="https://cdn.bootcdn.net/ajax/libs/axios/0.21.1/axios.min.js"></script>
```

如果引入了样式组件库, 同样在 `public/index.html` 里引入对应的链接
比如 `element-ui`

```html
<link
  href="https://cdn.bootcdn.net/ajax/libs/element-ui/2.15.3/theme-chalk/index.min.css"
  rel="stylesheet"
/>
<script src="https://cdn.bootcdn.net/ajax/libs/element-ui/2.15.3/index.min.js"></script>
```

**这样再打包后的体积就会变小了**

# The_End
