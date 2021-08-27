---
title: 几种常见css布局
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/sunrise.jpg
cover: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/divcss.jpeg
date: 2020-06-05 05:34:52
tags:
  - css布局
categories:
  - css
---

# 单列布局

![danlie](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/danlie.jpg)

### 第一种

给定宽度，margin:auto 即可实现

### html

```html
<div class="header"></div>
<div class="content"></div>
<div class="footer"></div>
```

### css

```css
.header {
  margin: 0 auto;
  max-width: 960px;
  height: 100px;
  background-color: blue;
}
.content {
  margin: 0 auto;
  max-width: 960px;
  height: 400px;
  background-color: yellow;
}
.footer {
  margin: 0 auto;
  max-width: 960px;
  height: 100px;
  background-color: green;
}
```

### 第二种

### html

```html
<div class="header">
  <div class="nav"></div>
</div>
<div class="content"></div>
<div class="footer"></div>
```

### css

```css
.header {
  margin: 0 auto;
  max-width: 960px;
  height: 100px;
  background-color: blue;
}
.nav {
  margin: 0 auto;
  max-width: 800px;
  background-color: darkgray;
  height: 50px;
}
.content {
  margin: 0 auto;
  max-width: 800px;
  height: 400px;
  background-color: aquamarine;
}
.footer {
  margin: 0 auto;
  max-width: 960px;
  height: 100px;
  background-color: aqua;
}
```

---

# 等高布局

当有内容填充一侧时,另一侧高度跟左侧保持相等

### html

```html
<div class="parent">
  <div class="box1">
    <p>content</p>
    <p>content</p>
    <p>content</p>
    <p>content</p>
    <p>content</p>
    <p>content</p>
    <p>content</p>
  </div>
  <div class="box2">
    <p>content</p>
  </div>
</div>
```

### css

通过设定 margin-bottom 和 padding-bottom，然后让父容器溢出隐藏，就能达到等高的效果

```css
.parent {
  border: 4px solid rgb(69, 209, 228);
  overflow: hidden;
}
.box1 {
  float: left;
  width: 100px;
  background-color: rgb(230, 56, 56);
  margin-bottom: -2000px;
  padding-bottom: 2000px;
}
.box2 {
  float: right;
  width: 100px;
  background-color: rgb(67, 67, 221);
  margin-bottom: -2000px;
  padding-bottom: 2000px;
}
```

### 实例：

![example](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/sameheight.png)

---

# 三列布局(双飞翼,圣杯)

左侧固定，右侧固定，中间自适应的三列布局

```
实现方式有很多：
    1.BFC
    2.定位
    3.浮动
    4.flex弹性
```

示例：

### html

```html
<div class="container">
  <div class="center">
    <h1>center</h1>
  </div>
  <div class="left">
    <h1>Left</h1>
  </div>
  <div class="right">
    <h1>Right</h1>
  </div>
</div>
```

### css

```css
.container {
  padding-left: 220px;
  padding-right: 220px;
}
.left {
  float: left;
  width: 200px;
  height: 400px;
  background: red;
  margin-left: -100%;
  position: relative;
  left: -220px;
}
.center {
  float: left;
  width: 100%;
  height: 500px;
  background: yellow;
}
.right {
  float: left;
  width: 200px;
  height: 400px;
  background: blue;
  margin-left: -200px;
  position: relative;
  right: -220px;
}
```

### 实例：

![example](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/shuangfeiyi.png)

# 未完待续 . . .
