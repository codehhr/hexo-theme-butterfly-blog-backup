---
title: jQuery ECharts 的使用
date: 2021-07-06 11:30:16
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/sunrise.jpg
cover:
tags:
  - js
  - javascript
  - jQuery
  - echarts
categories:
  - js
  - jQuery
comments:
---

# ECharts 的使用

## ECharts 是什么

ECharts 是一个使用 `JavaScript` 实现的开源可视化库 , 涵盖各行业图表 , 满足各种需求
ECharts 遵循 `Apache-2.0` 开源协议 , 免费商用
ECharts 兼容当前绝大部分浏览器 ( IE8/9/10/11 , Chrome , Firefox , Safari 等 ) 及兼容多种设备 , 可随时随地任性展示

> ## [echarts.apache.org/](https://echarts.apache.org/)

## 使用实例

### 引入 `jQuery.js` 和 `echarts.js`

```html
<script src="/js/jquery.min.js"></script>
<script src="/js/echarts.min.js"></script>
```

<script src="/js/jquery.min.js"></script>
<script src="/js/echarts.min.js"></script>

<img class="tom-img" src="https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/tom/tom.jpg"></img>

### 创建一个容器

```html
<div class="pie1"></div>
```

### 给定容器具体大小

```css
.pie1 {
  margin: 0 auto;
  width: 800px;
  height: 600px;
}
```

## 完整的数据配置

<style>
.pie1,
.pie2,
.bar,
.kline,
.radar,
.draggable {
  box-sizing: border-box;
  margin: 0 auto;
  width: 100%;
  height: 600px;
  overflow: auto;
}
@media screen and (max-width: 768px){
.pie1,
.pie2,
.bar,
.kline,
.radar,
.draggable {
  box-sizing: border-box;
  margin: 0 auto;
  width: 100%;
  height: 500px;
  overflow: auto;
  }
}
</style>

### 饼状图

<div class="pie1"></div>

{% hideToggle 饼状图配置 %}

```html
<div class="pie1"></div>
```

```css
.pie1 {
  margin: 0 auto;
  width: 800px;
  height: 600px;
}
```

```js
// 饼图
function echartsPie1() {
  let chart = echarts.init($(".pie1")[0]);
  let option = {
    title: {
      text: "Text",
      subtext: "Subtext",
      left: "center",
    },
    tooltip: {
      trigger: "item",
    },
    legend: {
      orient: "vertical",
      left: "left",
    },
    series: [
      {
        name: "NAME",
        type: "pie",
        radius: "50%",
        data: [
          { value: 148, name: "A" },
          { value: 735, name: "B" },
          { value: 580, name: "C" },
          { value: 484, name: "D" },
          { value: 300, name: "E" },
        ],
        emphasis: {
          itemStyle: {
            shadowBlur: 10,
            shadowOffsetX: 0,
            shadowColor: "rgba(0, 0, 0, 0.5)",
          },
        },
      },
    ],
  };
  chart.setOption(option);
}
echartsPie1();
```

<script>
// 饼图
function echartsPie1() {
  let chart = echarts.init($(".pie1")[0]);
  let option = {
    title: {
      text: "Text",
      subtext: "Subtext",
      left: "center",
    },
    tooltip: {
      trigger: "item",
    },
    legend: {
      orient: "vertical",
      left: "left",
    },
    series: [
      {
        name: "NAME",
        type: "pie",
        radius: "50%",
        data: [
          { value: 148, name: "A" },
          { value: 735, name: "B" },
          { value: 580, name: "C" },
          { value: 484, name: "D" },
          { value: 300, name: "E" },
        ],
        emphasis: {
          itemStyle: {
            shadowBlur: 10,
            shadowOffsetX: 0,
            shadowColor: "rgba(0, 0, 0, 0.5)",
          },
        },
      },
    ],
  };
  chart.setOption(option);
}
echartsPie1();
</script>

{% endhideToggle %}

### 带背景的柱状图

<div class="bar"></div>

{% hideToggle 带背景的柱状图配置 %}

```html
<div class="bar"></div>
```

```css
.bar {
  margin: 0 auto;
  width: 800px;
  height: 600px;
}
```

```js
// 带背景的柱状图
function echartsBar() {
  let echart = echarts.init($(".bar")[0]);
  let option = {
    xAxis: {
      type: "category",
      data: ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"],
    },
    yAxis: {
      type: "value",
    },
    series: [
      {
        name: "NAME",
        data: [120, 200, 150, 80, 70, 110, 130],
        type: "bar",
        showBackground: true,
        backgroundStyle: {
          color: "rgba(180, 180, 180, 0.2)",
        },
      },
    ],
  };
  echart.setOption(option);
}
echartsBar();
```

<script>
// 带背景的柱状图
function echartsBar() {
  let echart = echarts.init($(".bar")[0]);
  let option = {
    xAxis: {
      type: "category",
      data: ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"],
    },
    yAxis: {
      type: "value",
    },
    series: [
      {
        name: "NAME",
        data: [120, 200, 150, 80, 70, 110, 130],
        type: "bar",
        showBackground: true,
        backgroundStyle: {
          color: "rgba(180, 180, 180, 0.2)",
        },
      },
    ],
  };
  echart.setOption(option);
}
echartsBar();
</script>

{% endhideToggle %}

### 另一种饼图

<div class="pie2"></div>

{% hideToggle 另一种饼图配置 %}

```html
<div class="pie2"></div>
```

```css
.pie2 {
  margin: 0 auto;
  width: 800px;
  height: 600px;
}
```

```js
function echartsPie2() {
  let echart = echarts.init($(".pie2")[0]);
  let option = {
    legend: {
      top: "bottom",
    },
    toolbox: {
      show: true,
      // feature: {
      //   mark: { show: true },
      //   dataView: { show: true, readOnly: false },
      //   restore: { show: true },
      //   saveAsImage: { show: true },
      // },
    },
    series: [
      {
        name: "NAME",
        type: "pie",
        radius: [50, 250],
        center: ["50%", "50%"],
        roseType: "area",
        itemStyle: {
          borderRadius: 8,
        },
        data: [
          { value: 40, name: "rose 1" },
          { value: 38, name: "rose 2" },
          { value: 32, name: "rose 3" },
          { value: 30, name: "rose 4" },
          { value: 28, name: "rose 5" },
          { value: 26, name: "rose 6" },
          { value: 22, name: "rose 7" },
          { value: 18, name: "rose 8" },
        ],
      },
    ],
  };
  echart.setOption(option);
}
echartsPie2();
```

<script>
function echartsPie2() {
  let echart = echarts.init($(".pie2")[0]);
  let option = {
    legend: {
      top: "bottom",
    },
    toolbox: {
      show: true,
      // feature: {
      //   mark: { show: true },
      //   dataView: { show: true, readOnly: false },
      //   restore: { show: true },
      //   saveAsImage: { show: true },
      // },
    },
    series: [
      {
        name: "NAME",
        type: "pie",
        radius: [50, 250],
        center: ["50%", "50%"],
        roseType: "area",
        itemStyle: {
          borderRadius: 8,
        },
        data: [
          { value: 40, name: "rose 1" },
          { value: 38, name: "rose 2" },
          { value: 32, name: "rose 3" },
          { value: 30, name: "rose 4" },
          { value: 28, name: "rose 5" },
          { value: 26, name: "rose 6" },
          { value: 22, name: "rose 7" },
          { value: 18, name: "rose 8" },
        ],
      },
    ],
  };
  echart.setOption(option);
}
echartsPie2();
</script>

{% endhideToggle %}

### K 线图

<div class="kline"></div>

{% hideToggle K 线图配置 %}

```html
<div class="kline"></div>
```

```css
.kline {
  margin: 0 auto;
  width: 800px;
  height: 600px;
}
```

```js
function echartsKline() {
  let echart = echarts.init($(".kline")[0]);
  let option = {
    xAxis: {
      data: ["2017-10-24", "2017-10-25", "2017-10-26", "2017-10-27"],
    },
    yAxis: {},
    series: [
      {
        type: "k",
        data: [
          [20, 34, 10, 38],
          [40, 35, 30, 50],
          [31, 38, 33, 44],
          [38, 15, 5, 42],
        ],
      },
    ],
  };
  echart.setOption(option);
}
echartsKline();
```

<script>
function echartsKline() {
  let echart = echarts.init($(".kline")[0]);
  let option = {
    xAxis: {
      data: ["2017-10-24", "2017-10-25", "2017-10-26", "2017-10-27"],
    },
    yAxis: {},
    series: [
      {
        type: "k",
        data: [
          [20, 34, 10, 38],
          [40, 35, 30, 50],
          [31, 38, 33, 44],
          [38, 15, 5, 42],
        ],
      },
    ],
  };
  echart.setOption(option);
}
echartsKline();
</script>

{% endhideToggle %}

### 雷达图

<div class="radar"></div>

{% hideToggle 雷达图配置 %}

```html
<div class="radar"></div>
```

```css
.radar {
  margin: 0 auto;
  width: 800px;
  height: 600px;
}
```

```js
function echartsRadar() {
  let echart = echarts.init($(".radar")[0]);
  let option = {
    title: {
      text: "基础雷达图",
    },
    legend: {
      data: ["预算分配（Allocated Budget）", "实际开销（Actual Spending）"],
    },
    radar: {
      // shape: 'circle',
      indicator: [
        { name: "销售（Sales）", max: 6500 },
        { name: "管理（Administration）", max: 16000 },
        { name: "信息技术（Information Technology）", max: 30000 },
        { name: "客服（Customer Support）", max: 38000 },
        { name: "研发（Development）", max: 52000 },
        { name: "市场（Marketing）", max: 25000 },
      ],
    },
    series: [
      {
        name: "预算 vs 开销（Budget vs spending）",
        type: "radar",
        data: [
          {
            value: [4200, 3000, 20000, 35000, 50000, 18000],
            name: "预算分配（Allocated Budget）",
          },
          {
            value: [5000, 14000, 28000, 26000, 42000, 21000],
            name: "实际开销（Actual Spending）",
          },
        ],
      },
    ],
  };
  echart.setOption(option);
}
echartsRadar();
```

<script>
function echartsRadar() {
  let echart = echarts.init($(".radar")[0]);
  let option = {
    title: {
      text: "基础雷达图",
    },
    legend: {
      data: ["预算分配（Allocated Budget）", "实际开销（Actual Spending）"],
    },
    radar: {
      // shape: 'circle',
      indicator: [
        { name: "销售（Sales）", max: 6500 },
        { name: "管理（Administration）", max: 16000 },
        { name: "信息技术（Information Technology）", max: 30000 },
        { name: "客服（Customer Support）", max: 38000 },
        { name: "研发（Development）", max: 52000 },
        { name: "市场（Marketing）", max: 25000 },
      ],
    },
    series: [
      {
        name: "预算 vs 开销（Budget vs spending）",
        type: "radar",
        data: [
          {
            value: [4200, 3000, 20000, 35000, 50000, 18000],
            name: "预算分配（Allocated Budget）",
          },
          {
            value: [5000, 14000, 28000, 26000, 42000, 21000],
            name: "实际开销（Actual Spending）",
          },
        ],
      },
    ],
  };
  echart.setOption(option);
}
echartsRadar();
</script>

{% endhideToggle %}

### 可拖拽图

<div class="draggable"></div>

{% hideToggle 可拖拽图配置 %}

```html
<div class="draggable"></div>
```

```css
.draggable {
  margin: 0 auto;
  width: 800px;
  height: 600px;
}
```

```js
function echartsDraggable() {
  let myChart = echarts.init($(".draggable")[0]);
  let symbolSize = 20;
  let data = [
    [40, -10],
    [-30, -5],
    [-76.5, 20],
    [-63.5, 40],
    [-22.1, 50],
  ];

  let option = {
    title: {
      text: "Try Dragging these Points",
      left: "center",
    },
    tooltip: {
      triggerOn: "none",
      formatter: function (params) {
        return (
          "X: " +
          params.data[0].toFixed(2) +
          "<br>Y: " +
          params.data[1].toFixed(2)
        );
      },
    },
    grid: {
      top: "8%",
      bottom: "12%",
    },
    xAxis: {
      min: -100,
      max: 70,
      type: "value",
      axisLine: { onZero: false },
    },
    yAxis: {
      min: -30,
      max: 60,
      type: "value",
      axisLine: { onZero: false },
    },
    dataZoom: [
      {
        type: "slider",
        xAxisIndex: 0,
        filterMode: "none",
      },
      {
        type: "slider",
        yAxisIndex: 0,
        filterMode: "none",
      },
      {
        type: "inside",
        xAxisIndex: 0,
        filterMode: "none",
      },
      {
        type: "inside",
        yAxisIndex: 0,
        filterMode: "none",
      },
    ],
    series: [
      {
        id: "a",
        type: "line",
        smooth: true,
        symbolSize: symbolSize,
        data: data,
      },
    ],
  };

  setTimeout(function () {
    myChart.setOption({
      graphic: data.map(function (item, dataIndex) {
        return {
          type: "circle",
          position: myChart.convertToPixel("grid", item),
          shape: {
            cx: 0,
            cy: 0,
            r: symbolSize / 2,
          },
          invisible: true,
          draggable: true,
          ondrag: function (dx, dy) {
            onPointDragging(dataIndex, [this.x, this.y]);
          },
          onmousemove: function () {
            showTooltip(dataIndex);
          },
          onmouseout: function () {
            hideTooltip(dataIndex);
          },
          z: 100,
        };
      }),
    });
  }, 0);

  window.addEventListener("resize", updatePosition);

  myChart.on("dataZoom", updatePosition);

  function updatePosition() {
    myChart.setOption({
      graphic: data.map(function (item, dataIndex) {
        return {
          position: myChart.convertToPixel("grid", item),
        };
      }),
    });
  }

  function showTooltip(dataIndex) {
    myChart.dispatchAction({
      type: "showTip",
      seriesIndex: 0,
      dataIndex: dataIndex,
    });
  }

  function hideTooltip(dataIndex) {
    myChart.dispatchAction({
      type: "hideTip",
    });
  }

  function onPointDragging(dataIndex, pos) {
    data[dataIndex] = myChart.convertFromPixel("grid", pos);

    // Update data
    myChart.setOption({
      series: [
        {
          id: "a",
          data: data,
        },
      ],
    });
  }
  myChart.setOption(option);
}
echartsDraggable();
```

<script>
function echartsDraggable() {
  let myChart = echarts.init($(".draggable")[0]);
  let symbolSize = 20;
  let data = [
    [40, -10],
    [-30, -5],
    [-76.5, 20],
    [-63.5, 40],
    [-22.1, 50],
  ];

  let option = {
    title: {
      text: "Try Dragging these Points",
      left: "center",
    },
    tooltip: {
      triggerOn: "none",
      formatter: function (params) {
        return (
          "X: " +
          params.data[0].toFixed(2) +
          "<br>Y: " +
          params.data[1].toFixed(2)
        );
      },
    },
    grid: {
      top: "8%",
      bottom: "12%",
    },
    xAxis: {
      min: -100,
      max: 70,
      type: "value",
      axisLine: { onZero: false },
    },
    yAxis: {
      min: -30,
      max: 60,
      type: "value",
      axisLine: { onZero: false },
    },
    dataZoom: [
      {
        type: "slider",
        xAxisIndex: 0,
        filterMode: "none",
      },
      {
        type: "slider",
        yAxisIndex: 0,
        filterMode: "none",
      },
      {
        type: "inside",
        xAxisIndex: 0,
        filterMode: "none",
      },
      {
        type: "inside",
        yAxisIndex: 0,
        filterMode: "none",
      },
    ],
    series: [
      {
        id: "a",
        type: "line",
        smooth: true,
        symbolSize: symbolSize,
        data: data,
      },
    ],
  };

  setTimeout(function () {
    myChart.setOption({
      graphic: data.map(function (item, dataIndex) {
        return {
          type: "circle",
          position: myChart.convertToPixel("grid", item),
          shape: {
            cx: 0,
            cy: 0,
            r: symbolSize / 2,
          },
          invisible: true,
          draggable: true,
          ondrag: function (dx, dy) {
            onPointDragging(dataIndex, [this.x, this.y]);
          },
          onmousemove: function () {
            showTooltip(dataIndex);
          },
          onmouseout: function () {
            hideTooltip(dataIndex);
          },
          z: 100,
        };
      }),
    });
  }, 0);

  window.addEventListener("resize", updatePosition);

  myChart.on("dataZoom", updatePosition);

  function updatePosition() {
    myChart.setOption({
      graphic: data.map(function (item, dataIndex) {
        return {
          position: myChart.convertToPixel("grid", item),
        };
      }),
    });
  }

  function showTooltip(dataIndex) {
    myChart.dispatchAction({
      type: "showTip",
      seriesIndex: 0,
      dataIndex: dataIndex,
    });
  }

  function hideTooltip(dataIndex) {
    myChart.dispatchAction({
      type: "hideTip",
    });
  }

  function onPointDragging(dataIndex, pos) {
    data[dataIndex] = myChart.convertFromPixel("grid", pos);

    // Update data
    myChart.setOption({
      series: [
        {
          id: "a",
          data: data,
        },
      ],
    });
  }
  myChart.setOption(option);
}
echartsDraggable();
</script>

{% endhideToggle %}

# The_End
