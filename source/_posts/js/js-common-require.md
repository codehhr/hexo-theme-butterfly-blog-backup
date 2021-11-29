---
title: 关于 commonjs & requirejs
date: 2021-11-29 10:08:00
updated:
tags:
  - js
  - commonjs
  - requirejs
categories:
  - js
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

<!-- {% note info flat %}
info 提示块标籤
{% endnote %} -->

# `commonjs` 主要是为了代码模块化 (node 端)

假设有一个目录是 `commonjs`,里面有俩文件,分别是`math.js` 和`server.js`

## math.js

```js
// math.js
let add = (x, y) => {
  return x + y;
};

let minus = (x, y) => {
  return x - y;
};

module.exports = {
  add,
  minus,
};
```

## server.js

```js
// server.js
let math = require("./math.js");
console.log(math.add(2, 1));
console.log(math.minus(2, 1));
```

# `requirejs` 是让浏览器端支持代码模块化的方式

假设有一个目录是 `requirejs`, 里面有仨文件,分别是 `add.js` , `minus.js` 和 `index.html`

`requirejs` 提供 `define` 方法来定义模块,第一个参数是依赖的模块,第二个参数是对外暴露此模块

## add.js

```js
// add.js
let add = (x, y) => {
  return x + y;
};

define([], function () {
  return add;
});
```

## minus.js

```js
// minus.js
let minus = (x, y) => {
  return x - y;
};

define([], function () {
  return minus;
});
```

## 在浏览器端执行

引入 `requirejs` 链接,比如 `CDN`, 再给 `data-main` 属性赋值入口文件 (比如是 `main.js`)

```html
<script
  src="https://cdn.bootcdn.net/ajax/libs/require.js/2.3.6/require.min.js"
  data-main="./main.js"
></script>
```

## main.js

这里依赖的路径以入口文件为基准

```js
require(["./add.js", "./minus.js"], function (add, minus) {
  console.log(add(2, 1));
  console.log(minus(2, 1));
});
```
