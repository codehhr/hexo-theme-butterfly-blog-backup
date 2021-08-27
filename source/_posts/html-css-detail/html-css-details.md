---
title: 一些 html css 细节
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/sunrise.jpg
cover: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/divcss.jpeg
date: 2020-11-10 21:48:46
tags:
  - html
  - css
  - input光标
  - 插入符
  - placeholder
categories:
  - Html-Css-细节
---

# 一、 input 光标(插入符)颜色

```css
input: {
  caret-color: #c0c0ff;
}
```

# 二、 修改 placeholder 颜色

```css
input::placeholder {
  color: #c0c0ff;
}
/* input::-webkit-input-placeholder {
  color: #c0c0ff;
}
input::-moz-placeholder {
  color: #c0c0ff;
} */
```

# 三、 在移动端 app 下,搜索的时候让软键盘右下角按钮显示为 `搜索`

默认应该是显示 `换行`

![default](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/htmlcssdetails/default.png)

## 解决:

不用 `action` (通过 `ajax` 发送请求), 让 `onsubmit="return false"` 就可以

```html
<form action="" onsubmit="return false">
  <input type="text" placeholder="something " />
</form>
```

![showsearch](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/htmlcssdetails/showsearch.png)

# The_End
