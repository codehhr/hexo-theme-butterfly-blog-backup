---
title: 更换 grub 主题
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/linux/linux.jpeg
cover: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/setGrubTheme/preview.gif
date: 2020-06-02 00:13:17
tags:
  - linux
  - grub
categories:
  - linux
---

#### 默认的 grub 界面比较简陋

![grubThemes](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/setGrubTheme/grub.jpeg)

然后突然有想法了,想换个主题

# 具体操作

## 1.下载 grub 主题包

> ### 去这个地址下载主题(应该是这个地址)： https://www.gnome-look.org/browse/cat/109/order/latest/

![grubThemes](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/setGrubTheme/grubThemes.png)

比如这个主题
![grub](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/setGrubTheme/preview.gif)

### 点击 `Files`

![files](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/setGrubTheme/files.png)

## 2.配置 grub

### 自动安装

每个主题包里应该都有 `README.md` 文件,当然你完全可以按照他说明的做

把整个解压的文件夹放到：

```bash
/boot/grub/themes/
```

#### 好像大部分的主题包里都有一个 `install.sh` 文件 ,直接运行它也行 <span id="green-block">推荐</span>

```bash
给它可执行权限
sudo chmod +x install.sh
---
运行
sudo ./install.sh
```

### 手动安装

#### 如果是 Debian 系的，直接安装 grub-customizer：

```bash
sudo apt install grub-customizer
```

#### 或者编辑这个文件 <span id="green-block">推荐</span> ：

```bash
/etc/default/grub
```

#### 添加下面一行：

```bash
GRUB_THEME="/boot/grub/themes/主题包名/theme.txt"
```

### 3.更新 grub

#### 执行

```bash
sudo update-grub
```

#### 或者

```bash
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

主题包里面的背景图片和图标可自定义

完事~

# The_End
