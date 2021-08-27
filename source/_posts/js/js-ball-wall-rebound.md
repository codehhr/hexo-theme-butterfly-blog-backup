---
title: 用 Js 实现小球触壁反弹
date: 2021-06-15 11:22:23
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/sunrise.jpg
cover:
tags:
  - js
  - javascript
  - 触壁反弹
categories:
  - js
aside:
comments:
---

# 效果图

![The-wall-rebound](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/js/ball.gif)

### html

```html
<div class="box">
  <div class="ball"></div>
</div>

<button class="start">开始</button>
<button class="stop" disabled="true">暂停</button>
```

### css

```css
.box {
  position: relative;
  width: 500px;
  height: 400px;
  border: 2px solid #66555d;
}
.ball {
  position: absolute;
  width: 40px;
  height: 40px;
  border-radius: 50%;
  background-color: #56c6d4;
}
button {
  padding: 8px 20px;
}
```

### js

```js
var goUp = false,
  goLeft = false,
  step = 10,
  ballLeft = 0,
  ballTop = 0,
  timer = null;
var ballMaxLeft = $(".box").clientWidth - $(".ball").offsetWidth;
var ballMaxTop = $(".box").clientHeight - $(".ball").offsetHeight;

$(".start").onclick = function () {
  this.setAttribute("disabled", true);
  $(".stop").disabled = false;
  timer = setInterval(function () {
    // 垂直方向
    if (goUp) {
      if (ballTop <= 0) {
        goUp = false;
      } else {
        ballTop -= step;
        goUp = true;
      }
    } else {
      if (ballTop >= ballMaxTop) {
        goUp = true;
      } else {
        ballTop += step;
      }
    }

    // 水平方向
    if (goLeft) {
      if (ballLeft <= 0) {
        goLeft = false;
      } else {
        ballLeft -= step;
        goLeft = true;
      }
    } else {
      if (ballLeft >= ballMaxLeft) {
        goLeft = true;
      } else {
        ballLeft += step;
      }
    }
    $(".ball").style.top = ballTop + "px";
    $(".ball").style.left = ballLeft + "px";
  }, 20);
};

$(".stop").onclick = function () {
  clearInterval(timer);
  this.disabled = true;
  $(".start").disabled = false;
};
```
