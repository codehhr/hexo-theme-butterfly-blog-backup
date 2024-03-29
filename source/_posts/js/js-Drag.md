---
title: 原生 JS 实现拖放
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/js/jstop.jpeg
cover: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/js/js.jpeg
date: 2020-06-05 05:34:33
tags:
  - javascript
  - js
  - 拖放
categories:
  - js
---

# 原生 JS 快速实现拖放

拖放是很常见的一种交互效果，很多时候我们都会借助于第三方的控件来实现，其实用原生 js 实现起来也非常的方便。接下来我们就用原生 js 和 css 快速实现拖放效果

### html

```html
<body>
  <div class="droppable">
    <div class="draggable" draggable="true"></div>
  </div>
  <div class="droppable"></div>
  <div class="droppable"></div>
  <div class="droppable"></div>
  <div class="droppable"></div>
</body>
```

注意点： 1. 容器的的 class 为 droppable，用于接收被拖拽的元素，可被拖拽的元素 class 为 draggable，同时设置 draggable 属性为 true，表示该元素可以被拖拽。 2. 默认情况下，只有图片、链接还有被选中的文字能被拖拽，其他元素需要设置 draggable 为 true 才能被拖拽。所以为了凸显 draggable 的用法，这里使用 `<div>` 而不是 `<image>` 来作为被拖拽的元素。

### css

在实现样式的时候，除了实现静态的样式，一些过渡状态也需要增加样式以提升视觉体验：

1.  元素被拖动的过程中增加边框等效果； 2. 当元素被拖动到容器上方时，容器也应增加样式表明容器可以接收一个被拖拽的元素。

```css
body {
  background-color: darksalmon;
}

.draggable {
  background-image: url("http://source.unsplash.com/random/150x150");
  position: relative;
  height: 150px;
  width: 150px;
  top: 5px;
  left: 5px;
  cursor: pointer;
}

.droppable {
  display: inline-block;
  height: 160px;
  width: 160px;
  margin: 10px;
  border: 3px salmon solid;
  background-color: white;
}

.dragging {
  border: 4px yellow solid;
}

.drag-over {
  background-color: #f4f4f4;
  border-style: dashed;
}

.invisible {
  display: none;
}
```

注意点： 1. 图片来源于 百度; 2. .dragging 为 draggable 元素正在被拖动的状态，增加黄色 border； 3. .drag-over 为 draggable 元素被拖动到容器上方时容器的状态，增加灰色虚线 border。

### js

最后，我们需要通过 js 监听 draggable 和 droppable 的相关的事件。

```javascript
// 查询draggable和droppable
const draggable = document.querySelector(".draggable");
const droppables = document.querySelectorAll(".droppable");

// 监听draggable的相关事件
draggable.addEventListener("dragstart", dragStart);
draggable.addEventListener("dragend", dragEnd);

function dragStart() {
  this.className += " dragging";
  setTimeout(() => {
    this.className = "invisible";
  }, 0);
}

function dragEnd() {
  this.className = "draggable";
}

// 监听droppable的相关事件
for (const droppable of droppables) {
  droppable.addEventListener("dragover", dragOver);
  droppable.addEventListener("dragleave", dragLeave);
  droppable.addEventListener("dragenter", dragEnter);
  droppable.addEventListener("drop", dragDrop);
}

function dragOver(e) {
  e.preventDefault();
}

function dragEnter(e) {
  e.preventDefault();
  this.className += " drag-over";
}

function dragLeave(e) {
  this.className = "droppable";
}

function dragDrop(e) {
  this.className = "droppable";
  this.append(draggable);
}
```

注意点： 1. 当 draggable 元素被拖动时，原来容器中的 draggable 元素并不会消失，需要我们手动将其隐藏（class 设置为 invisible），如果同步操作会立马触发 dragend 事件导致拖动效果消失，所以在 setTimeout 的回调中异步设置可确保拖动操作开始后再隐藏 draggable 元素； 2. 在 dragEnter 和 dragOver 方法中我们需要通过 preventDefault 来取消事件以表明容器是一个合法的 droppable 元素，不然容器的 drop 事件将无法触发，接下来的操作也将无法进行，详细解释请参考 MDN DropTarget； 3.在 dragDrop 方法中直接使用 append 方法将 draggable 元素移动至当前容器下面。

---

完整示例演示：https://codehhr.gitee.io/web/jsdrag/

# The_End
