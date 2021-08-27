---
title: 微信小程序切换标签改变样式
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/sunrise.jpg
cover: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/wx/wxminipro.jpg
date: 2020-08-10 16:21:53
tags:
  - 微信小程序
  - 标签
  - tab
categories:
  - 微信小程序
---

# 微信小程序切换标签改变样式

![swichtab](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/wx/swichtab.gif)

### wxml

```html
<!--顶部导航栏-->
<view class="swiper-tab">
  <view
    class="tab-item {{currentTab==0 ? 'active' : ''}}"
    data-current="0"
    bindtap="swichNav"
    >A</view
  >
  <view
    class="tab-item {{currentTab==1 ? 'active' : ''}}"
    data-current="1"
    bindtap="swichNav"
    >B</view
  >
  <view
    class="tab-item {{currentTab==2 ? 'active' : ''}}"
    data-current="2"
    bindtap="swichNav"
    >C</view
  >
</view>

<!--内容主体-->
<swiper
  class="swiper"
  current="{{currentTab}}"
  duration="400"
  bindchange="swiperChange"
>
  <block wx:for="{{tabs}}" wx:key="item">
    <swiper-item>
      <view>{{item}}</view>
    </swiper-item>
  </block>
</swiper>
```

### wxss

```css
.swiper-tab {
  display: flex;
  flex-direction: row;
  line-height: 60rpx;
  border-bottom: 2rpx solid #777;
}

.tab-item {
  width: 33.3%;
  text-align: center;
  font-size: 15px;
  color: rgb(235, 135, 135);
}

.swiper {
  width: 100%;
  font-size: 100rpx;
  height: 1140rpx;
  background: #dfdfdf;
}

.active {
  color: blue;
  border-bottom: 5rpx solid blue;
}
```

### js

```javascript
Page({
  data: {
    // tab切换
    currentTab: 0,
    tabs: ["A", "B", "C"],
  },
  swichNav: function (e) {
    // console.log(e);
    var that = this;
    if (this.data.currentTab === e.target.dataset.current) {
      return false;
    } else {
      that.setData({
        currentTab: e.target.dataset.current,
      });
    }
  },
  swiperChange: function (e) {
    // console.log(e);
    this.setData({
      currentTab: e.detail.current,
    });
  },
});
```

# The_End
