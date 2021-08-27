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

![Fuck NVIDIA](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/nvidia/fuck-nvidia.jpeg)

# So NVIDIA ~ Fuck You !

之前因为装 `NVIDIA` 驱动 , `sddm` 进不去了 , 之后几经周折 , 我已把它拿下 , 即使他挂了 , 我也能让他起死回生 (开玩笑,开玩笑 ~ ~ ~ )

# 1.如果你不打算折腾,只想用 `intel` 核显

```bash
sudo pacman -S xf86-video-intel
```

# 2.`intel` + `nvidia` 双显卡切换

```bash
sudo pacman -S nvidia bbswitch
sudo pacman -S optimus-manager-qt-kde  (这个应该在 archlinuxcn 源里,我直接 `yay -S optimus-manager-qt`)
```

##### 如果安装 `optimus-manager-qt` 最后提示编译失败,重新安装 `base-devel` 就行,好像是在那里面,也没准是之前我少装了什么包,最后重启

### 重启后打开`optimus-manager-qt`

![optimus-manager-qt](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/nvidia/optimus-manager-qt.png)

### 右击可以切换模式

![optimus-manager-at-icon](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/nvidia/optimus-manager-qt-icon.png)

# The_End
