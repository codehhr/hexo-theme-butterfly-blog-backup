---
title: 配置 loader 进行 css 打包
date: 2021-09-20 16:07:08
updated:
tags:
  - Webpack
  - loader
categories:
  - Webpack
keywords:
description:
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/sunrise.jpg
cover: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/webpack/logo.jpeg
comments:
copyright:
copyright_author:
copyright_author_href:
copyright_url:
copyright_info:
---

{% note info flat %}
`Webpack` 原生支持 `js` 和 `json` , 可以使用 `loader` 告诉 `webpack` 加载 `CSS` 文件 , 或者将 `TypeScript` 转为 `JavaScript`
{% endnote %}

# 安装相对应的 loader

```bash
npm install style-loader css-loader -S -D
```

# 引入 CSS

在入口文件里使用 `import` 引入 `css`

```js
import "./style.css";
```

# loader 的配置

在 `webpack.config.js` 里添加配置

```js
module: {
  // 对某个格式的文件进行转换
  rules: [
    {
      // 正则匹配
      test: /\.css$/,
      // style-loader 将 js 的样式内容插入
      // css-loader 将 css 转换为 js
      // use 数组里 loader 解析的顺序是从后往前 (逆序)
      use: ["style-loader", "css-loader"],
    },
  ];
}
```

目前 `webpack.config.js` 的完整配置是

```js
let path = require("path");
module.exports = {
  // 入口文件
  entry: "./src/index.js",
  // 输出
  output: {
    // 输出文件名
    filename: "pack.js",
    // 输出路径 (绝对路径)
    // 利用 path 模块获取当前路径
    path: path.resolve(__dirname, "dist"),
  },
  // 打包模式; 开发环境--development, 生产环境--production
  mode: "development",
  module: {
    // 对某个格式的文件进行转换
    rules: [
      {
        // 正则匹配
        test: /\.css$/,
        // style-loader 将 js 的样式内容插入
        // css-loader 将 css 转换为 js
        // use 数组里 loader 解析的顺序是从后往前 (逆序)
        use: ["style-loader", "css-loader"],
      },
    ],
  },
};
```

# 尝试打包

在根目录 (`webpack.config.js` 所在路径) 下直接输入 `webpack`

```bash
webpack
```

## 验证

在 `html` 文件里引入打包好的 `js` 文件 , 用浏览器打开验证 `样式` 是否生效
