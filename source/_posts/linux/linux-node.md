---
title: Linux安装node环境以及cnpm
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/sunrise.jpg
cover: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/node/node.jpg
date: 2020-02-28 21:14:58
tags:
  - node
  - cnpm
  - npm
categories:
  - node
---

### 其实我老早以前就发现 node 版本太高也不行

#### 以往的版本下载地址: https://nodejs.org/zh-cn/download/releases/

# 下载并解压到 `/usr/local/` 下

![node](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/node/node.png)

# 设置全局

### 直接链接过,记得版本对应改一下

```bash
# node

sudo ln -s /usr/local/node-v12.12.0-linux-x64/bin/node /usr/local/bin/node

---

# npm

sudo ln -s /usr/local/node-v12.12.0-linux-x64/bin/npm /usr/local/bin/npm
```

### 安装 taobao 的 cnpm (更快)

```bash
sudo npm install -g cnpm --registry=https://registry.npm.taobao.org
```

### 添加到全局

```bash
sudo ln -s /usr/local/node-v12.12.0-linux-x64/bin/cnpm /usr/local/bin/cnpm
```

### 查看版本

![version](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/node/version.png)

# The_End
