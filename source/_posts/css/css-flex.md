---
title: css3自动换行排列
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/sunrise.jpg
cover: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/divcss.jpeg
date: 2020-07-22 10:42:19
tags:
  - css布局
  - flex
categories:
  - css
---

# 如果一行放不下就会自动换行

```css
display: flex;
flex-wrap: wrap;
```

## 示例 :

### html

```html
<div class="container">
  <div class="box"></div>
  <div class="box"></div>
  <div class="box"></div>
  <div class="box"></div>
  <div class="box"></div>
  <div class="box"></div>
</div>
```

### css

```css
.container {
  display: flex;
  flex-wrap: wrap; /*换行*/
  /* flex-wrap: wrap-reverse; //反方向换行 */
  align-content: flex-start; /*紧揍排列,解决换行出现空行*/
  justify-content: space-between; /*左右布局,平分间隙*/
  width: 520px;
  height: 300px;
  background-color: rgb(181, 235, 235);
}
.box {
  margin-top: 6px;
  width: 100px;
  height: 100px;
  background-color: rgb(223, 155, 155);
}
```

## 如图 :

![flex-wrap](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/css3flex/flexwrap.png)

# The_End
