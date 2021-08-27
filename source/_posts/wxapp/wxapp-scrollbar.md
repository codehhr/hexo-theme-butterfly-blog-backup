---
title: 微信小程序滚动条设置
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/sunrise.jpg
cover: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/wx/wxminipro.jpg
date: 2020-07-21 22:45:19
tags:
  - 微信小程序
  - 滚动条
  - scroll
  - scrollbar
categories:
  - 微信小程序
---

# 隐藏滚动条

```css
::-webkit-scrollbar {
  width: 0rpx;
  height: 0rpx;
  background-color: transparent;
}
```

其实设置为宽高为 0 或者背景颜色透明,其中任何一项都可以实现,或者你直接 `opacity:0;` 也可以,障眼法哈哈哈

# 设置滚动条样式

```css
::-webkit-scrollbar {
  width: 4px;
  height: 4px;
  color: #ffffff;
}

/* 设置滚动条轨道 内阴影+圆角 */
::-webkit-scrollbar-track {
  -webkit-box-shadow: inset 0 0 10px rgba(0, 0, 0, 0.3);
  box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.1);
  border-radius: 10px;
  background-color: #ffffff;
}

/* 设置滚动条 内阴影+圆角 */
::-webkit-scrollbar-thumb {
  border-radius: 10px;
  -webkit-box-shadow: inset 0 0 10px rgba(0, 0, 0, 0.3);
  box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.1);
  background-color: #39b54a;
}
```

# The_End
