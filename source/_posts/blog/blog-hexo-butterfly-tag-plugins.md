---
title: Hexo butterfly 的标签功能
date: 2021-07-18 20:11:24
updated:
tags:
  - hexo
  - 博客
categories:
  - 博客
  - hexo
  - butterfly
keywords:
description:
top_img:
cover:
comments:
toc:
toc_number:
copyright:
copyright_author:
copyright_author_href:
copyright_url:
copyright_info:
---

> ### https://butterfly.js.org/posts/4aa8abbe/#Note-Bootstrap-Callout

# Note (Bootstrap Callout)

{% note info flat %}
标签外挂是 `Hexo` 独有的功能 , 并不是标准的 `Markdown` 格式
以下的写法 , 只适用于 `Butterfly` 主题 , 用在其它主题上不会有效果 , 甚至可能会报错 , 使用前请留意
外挂虽然能为主题带来一些额外的功能和 `UI` 方面的强化 , 但是 , 标籤外挂也有明显的限制 , 使用时请留意
{% endnote %}

{% note warning flat %}
标籤外挂虽然能为主题带来一些额外的功能和 UI 方面的强化 , 但是 , 标籤外挂也有明显的限制 , 使用时请留意
{% endnote %}

{% tabs note %}

<!-- tab 通应设置 -->

修改 `主题配置文件`

```yml
note:
  # Note tag style values:
  #  - simple    bs-callout old alert style. Default.
  #  - modern    bs-callout new (v2-v3) alert style.
  #  - flat      flat callout style with background, like on Mozilla or StackOverflow.
  #  - disabled  disable all CSS styles import of note tag.
  style: simple
  icons: false
  border_radius: 3
  # Offset lighter of background in % for modern and flat styles (modern: -12 | 12; flat: -18 | 6).
  # Offset also applied to label tag variables. This option can work with disabled note tag.
  light_bg_offset: 0
```

`icons` 和 `light_bg_offset` 只对方法一生效
`Note` 标签外挂有两种用法

<!-- endtab -->

<!-- tab 用法 1 -->

```md
{% note [class] [no-icon] [style] %}
Any content (support inline tags too.io).
{% endnote %}
```

| 名称      | 用法                                                                                                       |
| --------- | ---------------------------------------------------------------------------------------------------------- |
| `class`   | 【可选】标识，不同的标识有不同的配色 ( `default` / `primary` / `success` / `info` / `warning` / `danger` ) |
| `no-icon` | 【可选】`不显示icon`                                                                                       |
| `style`   | 【可选】可以覆盖配置中的 `style` ( `simple`/`modern`/`flat`/`disabled` )                                   |

```md
{% note simple %}
默认 提示块标籤
{% endnote %}

{% note default simple %}
default 提示块标籤
{% endnote %}

{% note primary simple %}
primary 提示块标籤
{% endnote %}

{% note success simple %}
success 提示块标籤
{% endnote %}

{% note info simple %}
info 提示块标籤
{% endnote %}

{% note warning simple %}
warning 提示块标籤
{% endnote %}

{% note danger simple %}
danger 提示块标籤
{% endnote %}
```

## simple

{% note simple %}
默认 提示块标籤
{% endnote %}

{% note default simple %}
default 提示块标籤
{% endnote %}

{% note primary simple %}
primary 提示块标籤
{% endnote %}

{% note success simple %}
success 提示块标籤
{% endnote %}

{% note info simple %}
info 提示块标籤
{% endnote %}

{% note warning simple %}
warning 提示块标籤
{% endnote %}

{% note danger simple %}
danger 提示块标籤
{% endnote %}

## modern

```md
{% note modern %}
默认 提示块标籤
{% endnote %}

{% note default modern %}
default 提示块标籤
{% endnote %}

{% note primary modern %}
primary 提示块标籤
{% endnote %}

{% note success modern %}
success 提示块标籤
{% endnote %}

{% note info modern %}
info 提示块标籤
{% endnote %}

{% note warning modern %}
warning 提示块标籤
{% endnote %}

{% note danger modern %}
danger 提示块标籤
{% endnote %}
```

{% note modern %}
默认 提示块标籤
{% endnote %}

{% note default modern %}
default 提示块标籤
{% endnote %}

{% note primary modern %}
primary 提示块标籤
{% endnote %}

{% note success modern %}
success 提示块标籤
{% endnote %}

{% note info modern %}
info 提示块标籤
{% endnote %}

{% note warning modern %}
warning 提示块标籤
{% endnote %}

{% note danger modern %}
danger 提示块标籤
{% endnote %}

## flat

```md
{% note flat %}
默认 提示块标籤
{% endnote %}

{% note default flat %}
default 提示块标籤
{% endnote %}

{% note primary flat %}
primary 提示块标籤
{% endnote %}

{% note success flat %}
success 提示块标籤
{% endnote %}

{% note info flat %}
info 提示块标籤
{% endnote %}

{% note warning flat %}
warning 提示块标籤
{% endnote %}

{% note danger flat %}
danger 提示块标籤
{% endnote %}
```

{% note flat %}
默认 提示块标籤
{% endnote %}

{% note default flat %}
default 提示块标籤
{% endnote %}

{% note primary flat %}
primary 提示块标籤
{% endnote %}

{% note success flat %}
success 提示块标籤
{% endnote %}

{% note info flat %}
info 提示块标籤
{% endnote %}

{% note warning flat %}
warning 提示块标籤
{% endnote %}

{% note danger flat %}
danger 提示块标籤
{% endnote %}

## disabled

```md
{% note disabled %}
默认 提示块标籤
{% endnote %}

{% note default disabled %}
default 提示块标籤
{% endnote %}

{% note primary disabled %}
primary 提示块标籤
{% endnote %}

{% note success disabled %}
success 提示块标籤
{% endnote %}

{% note info disabled %}
info 提示块标籤
{% endnote %}

{% note warning disabled %}
warning 提示块标籤
{% endnote %}

{% note danger disabled %}
danger 提示块标籤
{% endnote %}
```

{% note disabled %}
默认 提示块标籤
{% endnote %}

{% note default disabled %}
default 提示块标籤
{% endnote %}

{% note primary disabled %}
primary 提示块标籤
{% endnote %}

{% note success disabled %}
success 提示块标籤
{% endnote %}

{% note info disabled %}
info 提示块标籤
{% endnote %}

{% note warning disabled %}
warning 提示块标籤
{% endnote %}

{% note danger disabled %}
danger 提示块标籤
{% endnote %}

## no-icon

```md
{% note no-icon %}
默认 提示块标籤
{% endnote %}

{% note default no-icon %}
default 提示块标籤
{% endnote %}

{% note primary no-icon %}
primary 提示块标籤
{% endnote %}

{% note success no-icon %}
success 提示块标籤
{% endnote %}

{% note info no-icon %}
info 提示块标籤
{% endnote %}

{% note warning no-icon %}
warning 提示块标籤
{% endnote %}

{% note danger no-icon %}
danger 提示块标籤
{% endnote %}
```

{% note no-icon %}
默认 提示块标籤
{% endnote %}

{% note default no-icon %}
default 提示块标籤
{% endnote %}

{% note primary no-icon %}
primary 提示块标籤
{% endnote %}

{% note success no-icon %}
success 提示块标籤
{% endnote %}

{% note info no-icon %}
info 提示块标籤
{% endnote %}

{% note warning no-icon %}
warning 提示块标籤
{% endnote %}

{% note danger no-icon %}
danger 提示块标籤
{% endnote %}

<!-- endtab -->

<!-- tab 用法 2 ( 自定义 icon ) -->

> 3.2.0 以上版本支

```md
{% note [color] [icon] [style] %}
Any content (support inline tags too.io).
{% endnote %}
```

| 名称    | 用法                                                                                 |
| ------- | ------------------------------------------------------------------------------------ |
| `color` | 【可选】颜色 ( `default` / `blue` / `pink` / `red` / `purple` / `orange` / `green` ) |
| `icon`  | 【可选】可配置自定义 `icon` (只支持 `fontawesome` 图标, 也可以配置 `no-icon` )       |
| `style` | 【可选】可以覆盖配置中的 `style` ( `simple`/`modern`/`flat`/`disabled` )             |

## simple

```md
{% note 'fab fa-cc-visa' simple %}
你是刷 Visa 还是 UnionPay
{% endnote %}
{% note blue 'fas fa-bullhorn' simple %}
2021 年快到了....
{% endnote %}
{% note pink 'fas fa-car-crash' simple %}
小心开车 安全至上
{% endnote %}
{% note red 'fas fa-fan' simple%}
这是三片呢？还是四片？
{% endnote %}
{% note orange 'fas fa-battery-half' simple %}
你是刷 Visa 还是 UnionPay
{% endnote %}
{% note purple 'far fa-hand-scissors' simple %}
剪刀石头布
{% endnote %}
{% note green 'fab fa-internet-explorer' simple %}
前端最讨厌的浏览器
{% endnote %}
```

{% note 'fab fa-cc-visa' simple %}
你是刷 Visa 还是 UnionPay
{% endnote %}
{% note blue 'fas fa-bullhorn' simple %}
2021 年快到了....
{% endnote %}
{% note pink 'fas fa-car-crash' simple %}
小心开车 安全至上
{% endnote %}
{% note red 'fas fa-fan' simple%}
这是三片呢？还是四片？
{% endnote %}
{% note orange 'fas fa-battery-half' simple %}
你是刷 Visa 还是 UnionPay
{% endnote %}
{% note purple 'far fa-hand-scissors' simple %}
剪刀石头布
{% endnote %}
{% note green 'fab fa-internet-explorer' simple %}
前端最讨厌的浏览器
{% endnote %}

## modern

```md
{% note 'fab fa-cc-visa' modern %}
你是刷 Visa 还是 UnionPay
{% endnote %}
{% note blue 'fas fa-bullhorn' modern %}
2021 年快到了....
{% endnote %}
{% note pink 'fas fa-car-crash' modern %}
小心开车 安全至上
{% endnote %}
{% note red 'fas fa-fan' modern%}
这是三片呢？还是四片？
{% endnote %}
{% note orange 'fas fa-battery-half' modern %}
你是刷 Visa 还是 UnionPay
{% endnote %}
{% note purple 'far fa-hand-scissors' modern %}
剪刀石头布
{% endnote %}
{% note green 'fab fa-internet-explorer' modern %}
前端最讨厌的浏览器
{% endnote %}
```

## flat

```md
{% note 'fab fa-cc-visa' flat %}
你是刷 Visa 还是 UnionPay
{% endnote %}
{% note blue 'fas fa-bullhorn' flat %}
2021 年快到了....
{% endnote %}
{% note pink 'fas fa-car-crash' flat %}
小心开车 安全至上
{% endnote %}
{% note red 'fas fa-fan' flat%}
这是三片呢？还是四片？
{% endnote %}
{% note orange 'fas fa-battery-half' flat %}
你是刷 Visa 还是 UnionPay
{% endnote %}
{% note purple 'far fa-hand-scissors' flat %}
剪刀石头布
{% endnote %}
{% note green 'fab fa-internet-explorer' flat %}
前端最讨厌的浏览器
{% endnote %}
```

{% note 'fab fa-cc-visa' flat %}
你是刷 Visa 还是 UnionPay
{% endnote %}
{% note blue 'fas fa-bullhorn' flat %}
2021 年快到了....
{% endnote %}
{% note pink 'fas fa-car-crash' flat %}
小心开车 安全至上
{% endnote %}
{% note red 'fas fa-fan' flat%}
这是三片呢？还是四片？
{% endnote %}
{% note orange 'fas fa-battery-half' flat %}
你是刷 Visa 还是 UnionPay
{% endnote %}
{% note purple 'far fa-hand-scissors' flat %}
剪刀石头布
{% endnote %}
{% note green 'fab fa-internet-explorer' flat %}
前端最讨厌的浏览器
{% endnote %}

## disabled

```md
{% note 'fab fa-cc-visa' disabled %}
你是刷 Visa 还是 UnionPay
{% endnote %}
{% note blue 'fas fa-bullhorn' disabled %}
2021 年快到了....
{% endnote %}
{% note pink 'fas fa-car-crash' disabled %}
小心开车 安全至上
{% endnote %}
{% note red 'fas fa-fan' disabled %}
这是三片呢？还是四片？
{% endnote %}
{% note orange 'fas fa-battery-half' disabled %}
你是刷 Visa 还是 UnionPay
{% endnote %}
{% note purple 'far fa-hand-scissors' disabled %}
剪刀石头布
{% endnote %}
{% note green 'fab fa-internet-explorer' disabled %}
前端最讨厌的浏览器
{% endnote %}
```

{% note 'fab fa-cc-visa' disabled %}
你是刷 Visa 还是 UnionPay
{% endnote %}
{% note blue 'fas fa-bullhorn' disabled %}
2021 年快到了....
{% endnote %}
{% note pink 'fas fa-car-crash' disabled %}
小心开车 安全至上
{% endnote %}
{% note red 'fas fa-fan' disabled %}
这是三片呢？还是四片？
{% endnote %}
{% note orange 'fas fa-battery-half' disabled %}
你是刷 Visa 还是 UnionPay
{% endnote %}
{% note purple 'far fa-hand-scissors' disabled %}
剪刀石头布
{% endnote %}
{% note green 'fab fa-internet-explorer' disabled %}
前端最讨厌的浏览器
{% endnote %}

## no-icon

```md
{% note no-icon %}
你是刷 Visa 还是 UnionPay
{% endnote %}
{% note blue no-icon %}
2021 年快到了....
{% endnote %}
{% note pink no-icon %}
小心开车 安全至上
{% endnote %}
{% note red no-icon %}
这是三片呢？还是四片？
{% endnote %}
{% note orange no-icon %}
你是刷 Visa 还是 UnionPay
{% endnote %}
{% note purple no-icon %}
剪刀石头布
{% endnote %}
{% note green no-icon %}
前端最讨厌的浏览器
{% endnote %}
```

{% note no-icon %}
你是刷 Visa 还是 UnionPay
{% endnote %}
{% note blue no-icon %}
2021 年快到了....
{% endnote %}
{% note pink no-icon %}
小心开车 安全至上
{% endnote %}
{% note red no-icon %}
这是三片呢？还是四片？
{% endnote %}
{% note orange no-icon %}
你是刷 Visa 还是 UnionPay
{% endnote %}
{% note purple no-icon %}
剪刀石头布
{% endnote %}
{% note green no-icon %}
前端最讨厌的浏览器
{% endnote %}

<!-- endtab -->

{% endtabs %}

# 未完待续 ...
