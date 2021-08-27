---
title: jQuery ( 二 )
date: 2021-06-30 16:50:51
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

# jQuery 事件机制

## 注册事件

`bind()` , `on()` 方法向被选元素添加一个或多个事件处理程序 , 以及当事件发生时运行的函数

```js
$("#div").bind({
  mouseover() {
    $(this).css("background-color", "blue");
  },
  mouseout() {
    $(this).css("background-color", "black");
  },
});
```

```js
$("p").on("click", function () {
  alert("该段落被点击了。");
});
```

## 事件对象 event

`event` 对象有以下属性:

- `type` : 事件类型 , 比如 `click`
- `which` : 触发该事件的鼠标按钮或键盘的键
- `target` : 事件发生的初始对象
- `data` : 传入事件对象的数据
- `pageX` : 事件发生时 , 鼠标位置的水平坐标 ( 以页面左上角为基准 )
- `pageY` : 事件发生时 , 鼠标位置的垂直坐标 ( 以页面左上角为基准 )

```js
$("button").click(function (event) {
  console.log(evet);
});
```

## each( )

`each()` 方法为每个匹配元素规定要运行的函数

```js
$("button").click(function () {
  $("li").each(function () {
    console.log($(this).text());
  });
});
```

## jQuery.each( )  函数用于遍历指定的对象和数组

```js
let arr = [10, 20, 30, 40];

$.each(arr, (index, value) => {
  console.log(`我是第${index + 1}元素 , 值是${value}`);
});

let obj = {
  name: "张三",
  age: 20,
  eat() {
    return "Good";
  },
};

$.each(obj, (key, value) => {
  console.log(`${key}:${value}`);
});
```

## jQuery 对 HTML 的设置与捕获

### html( )

`html()` 设置或返回所选元素的内容 ( 包括 `HTML` 标记 )

```js
$("button").click(function () {
  alert("HTML: " + $("#test").html());
});

$("button").click(function () {
  $("#test2").html("<b>Hello world!</b>");
});
```

### text( )

`text()` 设置或返回所选元素的文本内容

```js
$("button").click(function () {
  alert("Text: " + $("#test").text());
});
$("button").click(function () {
  $("#test1").text("Hello world!");
});
```

### val( )

`val()` 设置或返回表单字段的值

```js
$("button").click(function () {
  alert("值为: " + $("input").val());
});
$("button").click(function () {
  $("input").val("666");
});
```

### text( ) html( ) 以及 val( ) 的回调函数

`text()` , `html()` 以及 `val()` , 同样拥有回调函数 , 回调函数有两个参数 : 被选元素列表中当前元素的下标 , 以及原始 ( 旧的 ) 值然后以函数新值返回您希望使用的字符串

```js
$("button").click(function () {
  $("div").text(function (index, originText) {
    return `旧文本 :${originText},新文本 :HelloWorld (${index})`;
  });
});
```

### attr( ) 和 prop( )

`attr()` , `prop()` 方法用于获取和返回属性值
`attr()` 不仅可以返回元素的原生属性 , 还可以返回元素的自定义属性
具有 `true` 和 `false` 两个属性值的属性 , 如 `checked`, `selected` 或者 `disabled` 使用 `prop()`

```js
$("button").click(function () {
  console.log($("a").attr("href"));
});
$("button").click(function () {
  $("a").attr("href", "https://codehhr.cn");
});
```

```js
$("button").click(function () {
  console.log($("a").prop("href"));
});
$("button").click(function () {
  $("a").prop("href", "https://codehhr.cn");
});
```

# jQuery 对 HTML 的页面尺寸操作

![jQueryBox](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/js/jquerybox.png)

## width( ) 和 height( )

`height()` 方法设置或返回元素的高度 ( 不包括内边距 , 边框或外边距 )
`width()` 方法设置或返回元素的宽度 ( 不包括内边距 , 边框或外边距 )

```js
$("button").click(function () {
  console.log(`div 的宽度是: ${$("#div1").width()}`);
  console.log(`div 的高度是: ${$("#div1").height(20)}`);
});
```

## innerWidth( ) 和 innerHeight( )

`innerWidth()` 方法返回元素的宽度 ( 包括内边距 )
`innerHeight()` 方法返回元素的高度 ( 包括内边距 )

```js
$("button").click(function () {
  console.log(`div 宽度 , 包含内边距: ${$("#div1").innerWidth()}`);
  console.log(`div 高度 , 包含内边距: ${$("#div1").innerHeight()}`);
});
```

## outerWidth() 和 outerHeight() 方法

`outerWidth()` 方法返回元素的宽度 ( 包括内边距和边框 )
`outerHeight()` 方法返回元素的高度 ( 包括内边距和边框 )

```js
$("button").click(function () {
  console.log(`div 宽度 , 包含内边距和边框: ${$("#div1").outerWidth()}`);
  console.log(`div 高度 , 包含内边距和边框: ${$("#div1").outerHeight()}`);
});
```

## scrollTop() 和 scrollLeft() 方法

`scrollTop()` 方法设置或者返回滚动条被卷去的元素的高度
`scrollLeft()` 方法设置或者返回滚动条被卷去的元素的宽度

```js
$("button").click(function () {
  console.log($(document).scrollTop());
  console.log($(document).scrollLeft());
});
```

# jQuery 添加元素和删除元素

## append( )

`append()` 方法在被选元素的结尾插入内容 ( 仍然在该元素的内部 )

```js
$("ul").append("<li>append here</li>");
```

🢃

```html
<ul>
  <li></li>
  <li></li>
  <li>append here</li>
</ul>
```

## prepend( )

`prepend()` 方法在被选元素的开头插入内容

```js
$("ul").prepend("<li>prepend here</li>");
```

🢃

```html
<ul>
  <li>prepend here</li>
  <li></li>
  <li></li>
</ul>
```

## after( )

jQuery 的 `after()` 方法在被选元素之后插入内容

```js
$("div").after("<p>after</p>");
```

🢃

```html
<div></div>
<p>after</p>
```

## before( )

jQuery 的 `before()` 方法在被选元素之前插入内容

```js
$("div").before("<p>before</p>");
```

🢃

```html
<p>before</p>
<div></div>
```

## remove( ) 和 empty( )

`remove()` 删除被选元素 ( 及其子元素 )
`empty()` 从被选元素中删除子元素

`empty()`把子元素删除掉了 , 本身没有删除掉 , 所以本身占位置
`remove()`把自己和子元素都删除掉了 , 本身已删除掉 , 所以不占位置

**比如** 原 `DOM` 结构 🢃

```html
<ul>
  <li>1</li>
  <li>2</li>
  <li>3</li>
</ul>
```

### empty( )

```js
$("ul").empty();
```

结果 : 🢃

```html
<ul>
  <!-- 子元素都被删掉了 -->
</ul>
```

### remove( )

```js
$("ul").remove();
```

结果 : 🢃

```html
<!-- 把自己和子元素都删掉了,本身已删除掉  -->
```

# jquery 插件的认识

`jquery` 不可能包含所有的功能 , 我们可以通过插件扩展 `jquery` 的功能
`jquery` 有着丰富的插件 , 使用这些插件能给 `jquery` 提供一些额外的功能

# jquery.color.js 的使用

## 引入 js 文件

`jquery` 中的 `animate` 动画本身不支持变色 m 但是 `jquery.color.js` 弥补了这一缺陷
`jquery.color.js` 依赖于 `jQuery` , 所以需要先引用 `jquery.js`

```html
<script src="jquery.js"></script>
<script src="jquery.color.js"></script>
```

## 示例

```js
$("button").on("click", function () {
  $("div").animate(
    {
      width: "200px",
      "background-color": "red",
    },
    2000,
    function () {
      console.log("动画结束");
    }
  );
});
```

# jquery.lazyload.js 的使用

## 引入 js 文件

```html
<script src="jquery.js"></script>
<script src="jquery.lazyload.js"></script>
```

## 示例

```html
<img width="640" height="480" data-original="./img/test.jpg" alt="" />
<button>按钮</button>
```

```js
$(function () {
  $("button").click(function () {
    $("img").lazyload();
  });
});
```

# jquery.ui.js 的使用

`jQuery` `UI` 是建立在 `jQuery` `JavaScript` 库上的一组用户界面交互 , 特效 , 小部件及主题

## 引入

```html
<link rel="stylesheet" href="./css/jquery-ui.css" />
<script src="./js/jquery.js"></script>
<script src="./js/jquery-ui.min.js"></script>
```

## 示例

### 操作日期选择器

```html
<input type="text" id="date" />
```

```js
$("#date").datepicker();
```

### 拖动

允许鼠标拖动元素 , 在任意的 `DOM` 元素上启用 `draggable` 功能 , 通过鼠标点击并在视区中拖动来移动 `draggable` 对象

```html
<div id="draggable"></div>
```

```js
$(function () {
  $("#draggable").draggable();
});
```
