---
title: ArchLinux 双显卡方案
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/linux/linux.jpg
cover: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/i3/archscreenshotcmin.png
date: 2021-04-28 23:08:38
tags:
  - linux
  - arch
  - nvidia
  - bbswitch
  - optimus-manager
categories:
  - linux
  - arch
---

{% note warning no-icon %}
**如果开机进不去桌面, 可以尝试按 `ctrl`+`alt`+`F2 ~ F6`, `Linux` 默认有好几个 `tty` 终端, `F1` 到 `F6` 应该都能进去, 开机默认是 `tty1`**
{% endnote %}

![Fuck NVIDIA](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/nvidia/fuck-nvidia.jpeg)

# So NVIDIA ~ Fuck You !

之前因为装 `NVIDIA` 驱动 , `sddm` 进不去了 , 之后几经周折 , 我已把它拿下 , 即使他挂了 , 我也能让他起死回生 (开玩笑,开玩笑 ~ ~ ~ )

# 1.如果你不打算折腾,只想用 `intel` 核显

```sh
sudo pacman -S xf86-video-intel
```

# 2.`intel` + `nvidia` 双显卡切换

## 方案 (1)

### 安装 大黄蜂 和 依赖

```sh
sudo pacman -S bumblebee bbswitch nvidia opencl-nvidia lib32-nvidia-utils lib32-opencl-nvidia mesa lib32-mesa-libgl xf86-video-intel
```

### 把当前用户添加到 `bumblebee` 组里, `username` 对应当前用户名

```sh
sudo gpasswd -a username bumblebee
```

### 配置 `bumblebee`, 编辑下面这个文件

```sh
/etc/bumblebee/bumblebee.conf
```

**修改两处**

1. 设置 `Driver` 为 `nvidia`, 大概在第 `22` 行

```sh
Driver=nvidia
```

2. 电源管理设置为 `bbswitch`, 默认是 `auto`, 大概在 `57` 行

```sh
PMMethod=bbswitch
```

### 设置为开机自启

```sh
sudo systemctl enable bumblebeed
```

### 然后重启

重启后在终端输入 `nvidia-smi` 可以显示正在使用 `NVIDIA` 的进程

## 方案 (2)

```sh
sudo pacman -S nvidia bbswitch
sudo pacman -S optimus-manager-qt-kde  (这个包好像不在 pacman 管理的源里, 直接用 'AUR', 我直接 'yay -S optimus-manager-qt')
```

**如果安装 `optimus-manager-qt` 最后提示编译失败,重新安装 `base-devel` 就行,好像是在那里面,也没准是之前我少装了什么包,最后重启**

### 重启后打开`optimus-manager-qt`

![optimus-manager-qt](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/nvidia/optimus-manager-qt.png)

### 右击可以切换模式

![optimus-manager-at-icon](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/nvidia/optimus-manager-qt-icon.png)

# The_End
