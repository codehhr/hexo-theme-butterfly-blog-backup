---
title: hexo 报错 use_date_for_updated is deprecated...
date: 2020-11-08 18:10:14
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/sunrise.jpg
cover: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/tom/tom.jpg
tags:
  - hexo
  - 博客
categories:
  - 博客
  - hexo
---

# hexo 报错 use_date_for_updated is deprecated...

```
WARN  Deprecated config detected: "use_date_for_updated" is deprecated, please use "updated_option" instead. See https://hexo.io/docs/configuration for more details.
```

## 如图:

![usedateforupd](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/hexo/usedateforupd.png)

# 解决办法

编辑根目录的 `_config.yml` 文件 , 把 `use_date_for_updated` 值改为 `updated_option`

# The_End
