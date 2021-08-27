---
title: jQuery ( 一 )
date: 2021-06-29 16:39:11
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/sunrise.jpg
cover:
tags:
  - js
  - javascript
  - jQuery
categories:
  - js
  - jQuery
comments:
---

# jQuery 整体结构图

![jQuery](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/js/jquery.png)

# jQuery 语法

## 基础语法

美元符号定义 `jQuery` , `jQuery` 简化了 `DOM` 操作
`jQuery` 使用 `$(selector).action()` 的格式给一个 ( 或多个 ) 元素绑定事件 , 具体来说 , `$(selector)` 让 `jQuery` 选择匹配 `CSS` 选择器 `selector` 的元素 , 并将它/它们传递给叫做 `.action()` 的事件 `API`

## 实例

`jQuery` 入口函数

```js
// jQuery 入口函数
$(document).ready(function () {
  alert("Hello World!");
  $("#blackBox").hide();
});
```

**上述代码和以下原生 `js` 代码功能相同 :**

```js
window.onload = function () {
  alert("Hello World!");
  document.getElementById("blackBox").style.display = "none";
};
```

## jQuery 入口函数与 JavaScript 入口函数的区别

![load and ready](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/js/loadandready.png)

# JQuery 选择器

## 基本选择器

| 名称       | 用法                | 描述                                                                                |
| ---------- | ------------------- | ----------------------------------------------------------------------------------- |
| ID 选择器  | `$("#id")`          | 获取指定 ID 的元素                                                                  |
| 类选择器   | `$(".class")`       | 获取同一类 `class` 的元素                                                           |
| 标签选择器 | `$("div")`          | 获取同一类标签的所有元素                                                            |
| 并集选择器 | `$("div,p,li")`     | 使用逗号分隔,只要符合条件之一就可,获取所有的 `div`,`p`,`li` 元素                    |
| 交集选择器 | `$("div.redClass")` | 此选择器 `div` 和 `.redClass` 之间没有空格,是指 `class` 为 `redClass` 的 `div` 元素 |

## 层级选择器

| 名称       | 用法         | 描述                                                            |
| ---------- | ------------ | --------------------------------------------------------------- |
| 子代选择器 | `$("ul>li")` | 使用 `>`号,获取儿子层级的元素,注意,并不会获取孙子层级的元素     |
| 后代选择器 | `$"ul li")`  | 使用空格,代表后代选择器,获取 `ul` 下的所有 `li` 元素,包括孙子等 |

## 过滤选择器

|              | 用法                               | 描述                                                                    |
| ------------ | ---------------------------------- | ----------------------------------------------------------------------- |
| `:eq(index)` | `$("li:eq(2)").css("color","red")` | 获取到的 `li` 元素中,选择索引号为 `2` 的元素,索引号 `index` 从 `0` 开始 |
| `:odd`       | `$("li:odd").css("color","red")`   | 获取到的 `li` 元素中,选择索引号为 奇数 的元素                           |
| `:even`      | `$("li:even").css("color","red")`  | 获取到的 `li` 元素中,选择索引号为 偶数 的元素                           |

## 筛选选择器 (方法)

|                      | 用法                         | 说明                                         |
| -------------------- | ---------------------------- | -------------------------------------------- |
| `children(selector)` | `$("ul").children("li")`     | 相当于 `$("ul>li")` , 子类选择器             |
| `find(selector)`     | `$("ul").find("li")`         | 相当于 `$("ul li")` , 后代选择器             |
| `siblings(selector)` | `$("#first").siblings("li")` | 查找兄弟节点 , 不包括自己本身                |
| `parent()`           | `$("#first").parent()`       | 查找父亲                                     |
| `eq(index)`          | `$("li").eq(2)`              | 相当于 `$("li:eq(2)")` , `index` 从 `0` 开始 |
| `next()`             | `$("li").next()`             | 找下一个兄弟                                 |
| `prev()`             | `$("li").prev()`             | 找上一次兄弟                                 |
| `Index()`            | `$("li").index()`            | 获取当前的位置 (索引)                        |
| `not()`              | `$("p").not(".intro")`       | 返回不带有类名 `intro` 的所有 `p` 元素       |

## DOM 对象和 jQuery 对象的转换

### DOM 对象转 JQuery 对象

```js
$(DOM);
```

**比如 :**

```js
$("div");
$(".class");
$(this);
// ...
```

### JQuery 对象转 DOM 对象

```js
$(DOM)[0];
```

**比如 :**

```js
$("div")[0];
$(".class")[0];
$(this)[0];
// ...
```

# jQuery 事件

## 事件语法

### 单击事件

```js
$("button").click(function () {
  // 动作触发后执行的代码 !
});
```

### 双击事件

```js
$("button").dblclick(function () {
  // 动作触发后执行的代码 !
});
```

### 鼠标进入

```js
$("#div").mouseenter(function () {
  // 动作触发后执行的代码 !
});
```

### 鼠标移出

```js
$("#div").mouseleave(function () {
  // 动作触发后执行的代码 !
});
```

### 获取焦点

```js
$("input").focus(function () {
  // 动作触发后执行的代码 !
});
```

### 失去焦点

```js
$("input").blur(function () {
  // 动作触发后执行的代码 !
});
```

# jQuery 的 css() 方法

`jQuery` 的 `css()` 方法设置或返回被选元素的一个或多个样式属性

## 返回 CSS 属性

```js
$("p").css("background-color");
```

## 设置 CSS 属性

```js
$("p").css("background-color", "yellow");
```

## 设置多个 CSS 属性

```js
$("p").css({
  "background-color": "yellow",
  "font-size": "20px",
});
```

# jQuery css 类

## addClass( )

向被选元素添加一个或多个类

```css
.important {
  font-weight: bold;
  font-size: xx-large;
}
.blue {
  color: #0000ff;
}
```

```js
$("button").click(function () {
  $("h1,p").addClass("blue");
  $("div").addClass("important");
});
```

## removeClass( )

从被选元素删除一个或多个类

```js
$("button").click(function () {
  $("h1,h2,p").removeClass("blue");
});
```

## toggleClass( )

对被选元素进行添加或删除类的切换操作

```js
$("button").click(function () {
  $("h1,h2,p").toggleClass("blue");
});
```

## eq( )

方法返回带有被选元素的指定索引号的元素 , 索引号从 `0` 开头 , 所以第一个元素的索引号是 `0`

```js
$(selector).eq(index);
```

## index( )

`index()` 方法返回指定元素相对于其他 <span id="green-block">同级</span> 元素的 `index` 位置

```js
$("li").click(function () {
  console.log($(this).index());
});
```

## not()

`Not()` 方法返回指定元素之外的元素

```js
$("input").not(".inputA");
```

# jQuery 动画

## jQuery 隐藏显示

可以使用 `hide()` 和 `show()` 方法来隐藏和显示 `HTML` 元素

```js
$("#hide").click(function () {
  $("p").hide();
});
$("#show").click(function () {
  $("p").show();
});
```

可以使用 `toggle()` 方法来切换 `hide()` 和 `show()` 方法

```js
$("button").click(function () {
  $("p").toggle();
});
```

## jQuery 淡入淡出

`fadeIn()` 用于淡入已隐藏的元素 , `fadeOut()` 方法用于淡出可见元素

```js
$("button").click(function () {
  $("#div1").fadeIn();
  $("#div2").fadeIn("slow");
  $("#div3").fadeOut(3000);
});
```

`fadeToggle()` 方法可以在 `fadeIn()` 与 `fadeOut()` 方法之间进行切换

```js
$("button").click(function () {
  $("#div2").fadeToggle("fast");
});
```

`fadeTo()` 方法允许渐变为给定的不透明度 ( 值介于 `0` 与 `1` 之间 )

```js
$("button").click(function () {
  $("#div1").fadeTo("slow", 0.15);
});
```

## jQuery 滑动

`slideDown()` 方法用于向下滑动元素 , `slideUp()` 方法用于向上滑动元素

```js
$("#flip").click(function () {
  $("#div1").slideDown();
  $("#div1").slideUp();
});
```

`slideToggle()` 方法可以在 `slideDown()` 与 `slideUp()` 方法之间进行切换

```js
$("#flip").click(function () {
  $("#panel").slideToggle();
});
```

## jQuery 自定义动画

`animate()` 方法用于创建自定义动画 , 可选的 `speed` 参数规定效果的时长 , 它可以取以下值 : `"slow"`,`"fast"` 或`毫秒` , 可选的 `callback` 参数是动画完成后所执行的函数名称

```js
$("button").click(function () {
  $("div").animate({
    left: "250px",
    opacity: "0.5",
    width: "150px",
    height: "150px",
  });
});
```

## stop( )

`jQuery` 的 `stop()` 方法用于停止动画或效果 , 在它们完成之前 , 适用于所有 `jQuery` 效果函数 , 包括滑动 , 淡入淡出和自定义动画

```js
$("#stop").click(function () {
  $("#panel").stop();
});
```

## 回调函数

在当前动画 `100%` 完成之后执行

```js
$("button").click(function () {
  $("p").hide("slow", function () {
    alert("段落现在被隐藏了");
  });
});
```

# 案例

## 简单的 tab 切换

```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.tab {
  margin: 100px auto;
  width: 800px;
  height: 400px;
  background-color: #abaeb6;
}
.tab-title {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.tab-title-item {
  width: 25%;
  height: 40px;
  text-align: center;
  line-height: 40px;
  border-right: 1px solid #171829;
  border-bottom: 1px solid #171829;
}
.tab-title-item:nth-last-of-type(1) {
  border-right: none;
}
.tab-title-item:hover {
  background-color: #82858f;
}
.tab-content-item {
  font-size: 40px;
  text-align: center;
  line-height: 360px;
}
```

```html
<div class="tab">
  <div class="tab-title">
    <div class="tab-title-item">A</div>
    <div class="tab-title-item">B</div>
    <div class="tab-title-item">C</div>
    <div class="tab-title-item">D</div>
  </div>
  <div class="tab-content">
    <div class="tab-content-item">A</div>
    <div class="tab-content-item">B</div>
    <div class="tab-content-item">C</div>
    <div class="tab-content-item">D</div>
  </div>
</div>
```

```js
$(function () {
  $(".tab-content-item").hide();
  $(".tab-content-item:eq(0)").show();

  $(".tab-title-item").click(function () {
    $(".tab-content-item").hide();
    $(".tab-content-item").eq($(this).index()).show();
  });
});
```

## 手风琴

```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.main {
  margin: 100px auto;
  width: 600px;
  /* height: 200px; */
  background-color: #9298a5;
  display: flex;
  flex-direction: column;
  align-items: center;
}
.item {
  width: inherit;
}
.title {
  width: inherit;
  height: 50px;
  text-align: center;
  line-height: 50px;
  cursor: pointer;
}
.title:hover {
  background-color: #c1d5e2;
}
.content {
  height: 100px;
  text-align: center;
  line-height: 100px;
  font-size: 48px;
  font-weight: 800;
  color: #ffffff;
  background-color: #696d77;
}
```

```html
<div class="main">
  <div class="item">
    <div class="title">首 页</div>
    <div class="content">666</div>
  </div>
  <div class="item">
    <div class="title">归 档</div>
    <div class="content">666</div>
  </div>
  <div class="item">
    <div class="title">标签</div>
    <div class="content">666</div>
  </div>
  <div class="item">
    <div class="title">分类</div>
    <div class="content">666</div>
  </div>
</div>
```

```js
$(function () {
  $(".content").hide();
  $(".title").click(function () {
    $(".content").slideUp();
    $(this).next().stop().slideDown();
  });
});
```
