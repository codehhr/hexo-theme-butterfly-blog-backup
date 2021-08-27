---
title: Kali 下用 swaks 发送邮件
top_img: https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1591016903476&di=5e474f83fe10606ca99eae72563f2d17&imgtype=0&src=http%3A%2F%2Fwww.blackmoreops.com%2Fwp-content%2Fuploads%2F2015%2F11%2FChange-GRUB-background-in-Kali-Linux-blackMORE-OPs-10.jpg
cover: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/kali/kali.jpg
date: 2019-06-01 18:15:51
tags:
  - linux
  - kali
  - swaks
categories:
  - linux
  - kali
---

# kali 下的邮件发送工具 swaks

![kali.jpg](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/kali/kali.jpg)

```
Swaks 是一个功能强大，灵活，可编写脚本，面向事务的 SMTP 测试工具，目前 Swaks 托管在私有 svn 存储库中。
    官方项目 http：//jetmore.org/john/code/swaks/
```

## 1.测试邮箱的连通性

kali 自带 swaks 工具，无需安装

```bash
swaks --to xxx@qq.com
```

拿我的 QQ 举例

```bash
root@kali:~
➤ swaks --to 1871973389@qq.com                                          01:59:06
=== Trying mx3.qq.com:25...
=== Connected to mx3.qq.com.
<-  220 newxmmxsza22.qq.com MX QQ Mail Server.
 -> EHLO kali.lan
<-  250-newxmmxsza22.qq.com
<-  250-STARTTLS
<-  250-SIZE 73400320
<-  250 OK
 -> MAIL FROM:<root@kali.lan>
<-  250 OK.
 -> RCPT TO:<1871973389@qq.com>
<-  250 OK 1
 -> DATA
<-  354 End data with <CR><LF>.<CR><LF>.
 -> Date: Sat, 07 Dec 2019 01:59:07 -0500
 -> To: 1871973389@qq.com
 -> From: root@kali.lan
 -> Subject: test Sat, 07 Dec 2019 01:59:07 -0500
 -> Message-Id: <20191207015907.007285@kali.lan>
 -> X-Mailer: swaks v20190914.0 jetmore.org/john/code/swaks/
 ->
 -> This is a test mailing
 ->
 ->
 -> .
<-  250 Ok: queued as
 -> QUIT
<-  221 Bye.
=== Connection closed with remote host.
```

返回 250 Ok，说明该邮箱可以正常通信。

---

## 2.开启 SMTP 服务

QQ 的 或 163 官网的都可以,个人感觉 163 的还方便些

![SMTP_server](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/kali/screenshot_smtp.png)

记住 smtp 的密码

## 3.利用 SMTP 发送邮件

```bash
swaks --to 收件箱 --from 发件箱 --body 邮件内容 --header "Subject:hello" --server smtp.qq.com -p 25 -au 发件箱 -ap SMTP的密码
```

参数说明：

```bash
    --to //收件人邮箱;
    --from //发件人邮箱;
    --ehlo qq.com //伪造邮件的ehlo头，即发件人邮箱的域名，身法认证;
    --body "https://goobe.io" //引号内为邮件正文;
    --header "Subject:hello" //邮件头信息，Subject为邮件标题;
    --data email.txt //将正常邮件内容保存成TXT文件，再作为正常邮件发出;
    --help 显示命令帮助
    --verison 显示版本信息

	输出内容的含义:
    “===”:swaks输出的信息行
    “*“:swaks中产生的错误
    ” ->”:发送到目标的预期行(无错误)
    “<- “:服务器的预期回复(无错误)
    “<**”:服务器返回的错误信息
```

## 4.发送附件

```bash
swaks --to 收件箱 --from 发件箱  --body 邮件内容  --header "Subject:hello" --attach example.doc --server smtp.qq.com -p 25 -au 发件箱 -ap SMTP密码
```

## 5.伪造邮件

```bash
--data email.txt //将正常邮件内容保存成TXT文件，再作为正常邮件发出
```

发送内容为 email.txt (记得添加文件路经) 里的全部内容  
= = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = =

先找一分邮件，查看邮件原文，复制里面的内容，存为 .txt

= = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = =  
去掉 Received 和 To 两行 （发送时用 --from 和 --to 代替）  
= = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = =

```bash
swaks --data ./email.txt --to 收件箱 --from 发件箱 --server smtp.qq.com -p 25 -au 发件箱 -ap SMTP密码
```

收件箱收到的是 email.txt 里的内容

### 好了,到这就结束了,其实理论上 swaks 可以伪造邮件里的任何一个参数

# The_End
