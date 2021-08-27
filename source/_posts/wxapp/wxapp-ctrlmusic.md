---
title: 微信小程序 背景音乐
cover: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/wx/wxminipro.jpg
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/sunrise.jpg
date: 2020-12-03 00:25:16
tags:
  - 微信小程序
  - 背景音乐
categories:
  - 微信小程序
---

# 微信小程序背景音乐

## 直接上代码

### wxml

```html
<!-- music -->
<view class="music {{isplay?'playing':''}}" bindtap="ctrlMusic">
  <image src="{{musicimg}}"></image>
</view>
```

### wxss

```css
/* music */
.music {
  position: relative;
  top: 200px;
  margin: 0 auto;
  border: 2px solid #000000;
  width: 96rpx;
  height: 96rpx;
  border-radius: 50%;
  z-index: 10;
}

/* 音符旋转动画 */
.playing {
  animation: rotate 2s linear infinite;
}

@keyframes rotate {
  from {
    transform: rotate(0deg);
  }

  to {
    transform: rotate(360deg);
  }
}

/* 音符 */
.music image {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 80%;
  height: 80%;
}
```

### js

```js
Page({
  data: {
    musicimg: "/img/music.png", //背景音乐符号图片
    isplay: false,
  },
  // 控制背景音乐
  ctrlMusic: function () {
    const backgroundAudioManager = wx.getBackgroundAudioManager();
    backgroundAudioManager.title = "New Life";
    backgroundAudioManager.epname = "New Life";
    backgroundAudioManager.singer = "Peter Jeremias";
    backgroundAudioManager.coverImgUrl =
      "https://ae01.alicdn.com/kf/Ud08f63ccb57b41988e5921036e61bca2r.jpg";
    backgroundAudioManager.src = "https://codehhr.gitee.io/musics/new_life.mp3";
    // 播放
    if (!this.data.isplay) {
      this.setData({
        isplay: !this.data.isplay,
      });
      console.log("music playing !");
      // 结束时循环
      backgroundAudioManager.onEnded(() => {
        console.log("music end !");
        this.setData({
          isplay: !this.data.isplay,
        });
        console.log("music replay !");
        this.ctrlMusic();
      });
    }
    // 暂停
    else {
      this.setData({
        isplay: !this.data.isplay,
      });
      backgroundAudioManager.pause();
      backgroundAudioManager.onPause(() => {
        console.log("music stop !");
      });
    }
  },
});
```

## 效果图

![music](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/wx/music.gif)

# The_End
