---
title: Linux 终端走代理
date: 2021-11-09 20:29:42
updated:
tags:
  - linux
categories:
  - linux
keywords:
description:
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/linux/linux.jpg
cover: 
comments:
copyright:
copyright_author:
copyright_author_href:
copyright_url:
copyright_info:
---

<!-- {% note info flat %}
**可以吧代理设置写入当前终端环境的 `rc` 文件或者在当前终端执行 ( 只作用在当前终端, 比较推荐 )**
{% endnote %} -->

# 在当前终端执行

假设端口是 `2000`, 且是 `socks5` 协议

```sh
export ALL_PROXY=socks5://127.0.0.1:2000
```
