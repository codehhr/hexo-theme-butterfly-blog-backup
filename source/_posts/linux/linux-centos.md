---
title: VMware 安装 CentOS7 后的简单配置
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/sunrise.jpg
date: 2020-10-06 20:48:41
tags:
  - linux
  - CentOS
categories:
  - linux
  - CentOS
---

# 1.连网

如果能连网,跳过此步
试着 ping 一下百度

```bash
ping baidu.com
```

## 动态分配 IP

```bash
sudo vim /etc/sysconfig/network-scripts/ifcfg-ens33
```

记得前面加上 `sudo` ,其实你不加根本编辑不了,哈哈哈哈哈哈 !
后面的 `ens33` 可能不太一样,是网卡名,输入的时候按 `Tab` 补全就行了

![dhcp](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/centos/dhcp.png)

如上图所示需要改动两个地方

```bash
BOOTPROTO=dhcp
ONBOOT=yes
```

顺便说一下`vim`这个编辑器,按`i`,`o`,`I`,`A`都可以进入插入模式，退出保存先按`esc`,然后按 `ZZ` (大写的) 就可以了,或者按 `esc` 后输入`:wq`再按回车

然后重启网络服务

```bash
sudo systemctl restart network
```

输入`ip addr`可以查看 ip,试着 ping 一下 baidu ,已经有网了

![ipaddr](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/centos/ipaddr.png)

# 2.换为国内软件源,方便快速下载(其实有好几种方式)

> ## 作为参考: https://mirrors.cnnic.cn/help/centos/

## 可以先把原来的源文件备份一下

```bash
sudo mv /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.backup
```

## 下载阿里和网易的 CentOS-Base.repo

### 我用的 CentOS-7

```bash
sudo wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo
或者
sudo curl -o /etc/yum.repos.d/CentOS-Base.repo http://mirrors.163.com/.help/CentOS7-Base-163.repo
```

## 清除 yum 缓存并生成新的 yum 缓存

```bash
sudo yum clean all
sudo yum makecache
```

## 安装 epel 源

```bash
sudo yum list | grep epel-release
sudo yum install -y epel-release
```

## 使用阿里镜像提供的 epel 源

```bash
sudo wget -O /etc/yum.repos.d/epel-7.repo http://mirrors.aliyun.com/repo/epel-7.repo
```

## 重新清除 yum 缓存并生成新的 yum 缓存

```bash
sudo yum clean all
sudo yum makecache
```

## 系统升级

```bash
sudo yum -y update
```

会更新所有软件
`-y`可选,加上会同意所有项,即默认 `yes`

# 3.安装,卸载软件

比如安装`git`

```bash
sudo yum -y install git
```

卸载 `git`

```bash
sudo yum -y remove git
```

# The_End
