---
title: Manjaro安装后简单配置
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/manjaro/manjaro-top-img.png
cover: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/manjaro/manjaro_screenshot.png
date: 2019-06-01 18:00:29
tags:
  - linux
  - manjaro
categories:
  - linux
  - manjaro
---

## 一个相见恨晚的 Linux 操作系统

Manjaro 到底有多受欢迎?

```
DistroWatch是一个包含了各种Linux发行版及其他自由/开放源代码的类Unix操作系统。
( 如OpenSolaris、MINIX及BSD等 ) 的新闻、人气排名、以及其他一般信息等的网站。
它包含了数百种发行版的信息。
原文链接：https://distrowatch.com/table.php?distribution=manjaro
```

---

![screenshot](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/i3/i3.png)

# Manjaro 安装后简单配置

## 1. 添加 `archlinuxcn` 源

编辑这个文件

```bash
/etc/pacman.conf
```

在文末添加以下内容,添加清华源,或者别的也行,里面有国内的一些软件

```bash
[archlinuxcn]
SigLevel = Never
Server = https://mirrors.tuna.tsinghua.edu.cn/archlinuxcn/$arch
```

保存退出

#### 按照地区自动更新为最快最稳定的软件源镜像地址

```bash
sudo pacman-mirrors -c China
```

#### 强制更新一下 :

```bash
sudo pacman -Syyu
```

========================一路回车就行= = = = = = = = = = = = = = = = = = =

## 2.安装软件

需要安装的软件 `pacman` 里基本都有

### 1.安装 vim

```bash
sudo pacman -S vim
```

### 2.更换 shell

默认为 `bash`,我比较喜欢 `fish`,方便好用,配置也简单

```bash
安装fish
sudo pacman -S fish
---
更改shell为fish
chsh -s /usr/bin/fish
---
安装oh-my-fish(一个友好的shell)
curl -L https://get.oh-my.fish | fish
```

#### 可能国内原因,raw.githubusercontent.com 访问不了,安装 oh-my-fish 会失败,可以先尝试 clone 到本地再安装,或者添加 raw.githubusercontent 的 ip 到 hosts 文件

```bash
git clone https://github.com/oh-my-fish/oh-my-fish
# 如果你网不好,可以克隆镜像仓库(比如:https://github.com.cnpmjs.org/oh-my-fish/oh-my-fish)
cd oh-my-fish
bin/install --offline
```

#### 简单配置一下 fish

终端输入：

```bash
fish_config
```

然后它会自动打开浏览器

##### 选一个主题，然后点`set theme`

在`promt`栏里选个提示符，然后点`promt set`
然后就可以关闭浏览器了
回到终端，回车即可

### 3.安装 录屏软件（推荐`simplescreenrecorder`这个比较小）

```bash
sudo pacman -S simplescreenrecorder
```

### 4.安装 VScode

```bash
sudo pacman -S visual-studio-code-bin
```

或者

```bash
sudo pacman -S code
```

### 5.安装网易云音乐

```bash
sudo pacman -S netease-cloud-music
```

---

### 6.安装中文输入法

```bash
sudo pacman -S fcitx5 fcitx5-im fcitx5-rime
sudo pacman -S fcitx5-material-color # 主题
sudo pacman -S fcitx5-configtool  # 图形化配置界面

```

##### 添加配置文件 `~/.xprofile` 填入以下几句

```bash
export GTK_IM_MODULE=fcitx5

export QT_IM_MODULE=fcitx5

export XMODIFIERS="@im=fcitx5"
```

##### 然后重启 ( 建议设置为开机让 `fcitx5` 自启 )

##### 重启后你应该会看见一个小键盘的图标,右击选 `config`,添加 `rime` 输入法,默认应该是 `ctrl+space` 切换输入法

![fcitx-configtool](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/manjaro/fcitx-configtool.png)

![rime](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/manjaro/rime.png)

# The_End
