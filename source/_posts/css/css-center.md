---
title: css常用居中方式
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/sunrise.jpg
cover: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/divcss.jpeg
date: 2020-07-27 23:04:33
tags:
  - css布局
categories:
  - css
---

{% tabs center %}

<!-- tab 水平居中 -->

# 一、水平居中

## 内联元素

父级元素加 `text-align: center` 即可

```html
<div class="container">
  <a>内联元素</a>
</div>
```

```css
.container {
  text-align: center;
}
```

## 块级元素

给定宽度,然后 margin 上下为 0,左右 auto 即可

```html
<div class="container">块级元素</div>
```

```css
.container {
  width: 200px;
  margin: 0 auto;
}
```

## 多个块级元素

### 第一种方式

子元素设置成内联,父级元素加 `text-align:center`即可

```html
<div class="container">
  <div>第一个块</div>
  <div>第二个块</div>
  <div>第三个块</div>
</div>
```

```css
.container {
  text-align: center;
}
.container div {
  display: inline-block;
}
```

### 第二种方式

利用 flexbox 弹性布局

```html
<div class="container">
  <div>第一个块</div>
  <div>第二个块</div>
  <div>第三个块</div>
</div>
```

```css
.container {
  display: flex;
  justify-content: center;
}
```

<!-- endtab -->

<!-- tab 垂直居中 -->

# 二、垂直居中

## 内联元素

### 第一种方式

设置 padding

```html
<div class="container">需要垂直居中的内容(内联)</div>
```

```css
.container {
  padding: 40px 40px;
}
```

### 第二种方式

按照父级元素的高度,设置子元素的行高

```html
<div class="container">需要垂直居中的内容(内联)</div>
```

```css
.container {
  height: 100px;
  line-height: 100px;
}
```

### 第三种方式

利用 flexbox,父级元素需给定高度

```html
<div class="container">
  <a href="">爷要垂直居中</a>
  <a href="">爷要垂直居中</a>
  <a href="">爷要垂直居中</a>
</div>
```

```css
.container {
  width: 200px;
  height: 200px;
  display: flex;
  flex-direction: column;
  justify-content: center;
}
```

## 块级元素

### 第一种方式

父元素相对定位 `position:relative`,子元素绝对定位 `position: absolute`

```html
<div class="container">
  <div>爷要垂直居中</div>
</div>
```

```css
.container {
  position: relative;
  width: 200px;
  height: 200px;
}
.container div {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
}
```

### 第二种方式

利用 flexbox

```html
<div class="container">
  <div>爷要垂直居中</div>
</div>
```

```css
.container {
  width: 200px;
  height: 200px;
  display: flex;
  flex-direction: column;
  justify-content: center;
}
```

<!-- endtab -->

<!-- tab 水平和垂直居中 -->

# 三、水平和垂直居中

### 第一种方式

父元素相对定位 `position:relative`,子元素绝对定位 `position: absolute`

```html
<div class="container">
  <div>爷要水平和垂直居中</div>
</div>
```

```css
.container {
  position: relative;
  width: 200px;
  height: 200px;
}
.container div {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background-color: red;
}
```

### 第二种方式

使用 flexbox

```html
<div class="container">
  <div>我要垂直居中啊a我要垂直居中啊a我要垂直居中啊</div>
</div>
```

```css
.container {
  width: 200px;
  height: 200px;
  display: flex;
  align-items: center;
  justify-content: center;
}
.container div {
  width: 100px;
  height: 100px;
}
```

<!-- endtab -->

{% endtabs %}

![lalala](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/emoji/s.png)

## 最后说一点,如果具体宽高已知,给定具体数值也可以直接实现

# The_End
