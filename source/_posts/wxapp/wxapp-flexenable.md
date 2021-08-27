---
title: 微信小程序警告设置 enable-flex 属性以使 flexbox 布局生效的解决办法
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/sunrise.jpg
cover: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/wx/wxminipro.jpg
date: 2020-07-21 22:35:21
tags:
  - 微信小程序
  - flexbox
categories:
  - 微信小程序
---

# 微信小程序警告设置 enable-flex 属性以使 flexbox 布局生效的解决办法

### 具体情况:

scroll-view 滚动，设置 display：flex 不生效并警告设置 enable-flex 属性以使 flexbox 布局生效

添加 `enable-flex` 属性,值设置为 `true` 就可以了

```html
<scroll-view enable-flex="true"> </scroll-view>
```

# The_End
