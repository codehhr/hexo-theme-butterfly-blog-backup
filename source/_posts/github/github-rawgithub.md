---
title: 解决raw.githubusercontent.com无法连接问题
date: 2019-06-2 17:58:07
tags:
  - curl
  - github
categories:
  - github
---

# 解决 GitHub 的 raw.githubusercontent.com 无法连接问题

在使用 curl 下载文件时,如果出现以下情况

```
curl: (7) Failed to connect to raw.githubusercontent.com port 443: Connection refused
```

# 查询 raw.githubusercontent.com 的 IP

修改 hosts 文件

文件路径 `/etc/hosts`

添加以下内容

```
# GitHub Start
52.74.223.119 github.com
192.30.253.112 gist.github.com
192.30.253.113 gist.github.com
192.30.253.119 gist.github.com
54.169.195.247 api.github.com
185.199.111.153 assets-cdn.github.com
151.101.76.133 raw.githubusercontent.com
151.101.108.133 user-images.githubusercontent.com
151.101.76.133 gist.githubusercontent.com
151.101.76.133 cloud.githubusercontent.com
151.101.76.133 camo.githubusercontent.com
151.101.185.194 github.global.ssl.fastly.net
# GitHub End
```

# 如果你有代理那当以上都是废话

# The_End
