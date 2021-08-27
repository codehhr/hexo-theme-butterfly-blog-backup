---
title: 用 Hugo 快速搭建博客
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/sunrise.jpg
cover: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/hugo/hugo.jpg
date: 2019-06-01 18:32:16
tags:
  - hugo
  - 博客
categories:
  - 博客
  - hugo
---

# 用 Hugo 搭建博客

Hugo 是一个用 Go 编写的静态站点生成器，生成速度很快
下面是具体操作：

# 1.安装 Hugo

### Windows 用户

使用 Chocolatey 或者 Scoop 快速安装，取决于你使用什么包管理

```
choco install hugo -confirm
```

```
scoop install hugo
```

也可以到 https://github.com/gohugoio/hugo/releases 下载对应的操作系统版本的 Hugo 二进制文件！

把 hugo.exe 所在目录添加到系统变量里, `hugo version` 可查看是否添加成功！

### Mac 用户

直接用 `Homebrew` 安装

```
brew install hugo
```

### Linux 用户

这里就不多说了

```
基于Debian的 ：sudo apt-get install hugo
```

```
基于ArchLinux的 ：sudo pacman -S hugo
```

# 2.生成站点

比如新建一个 myblog 的网站：

```
hugo new site myblog
```

也就一瞬间完成的事，此时生成了一个文件名为 `myblog` 的文件夹

然后到 `Hugo Theme` 选一个主题

https://themes.gohugo.io/

---

![Hugo-Theme](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/hugo/hugo_themes.png)

---

比如这个 "`Jane`"

---

![Hugo-Theme-jane](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/hugo/jane.png)

其实每个主题里面都有教程，这里实际操作一下

### 1.切换到 `myblog` 目录

```
cd myblog
```

把主题克隆下来 , 需要用到 `git` ，如果没有自行安装一下

```
git clone https://github.com/xianmin/hugo-theme-jane.git --depth=1 themes/jane
```

### 2.然后新建一篇文章试试效果

```
hugo new post/blog.md
```

随便在里面写点东西，这里需要你会 `markdown` 语法，其实也不难，半天就能学会

---

【【 如果你懒，也可以把主题文件夹里的示例复制过来 】】

```
cp -r themes/jane/exampleSite/content ./
```

---

### 3.把主题里的配置文件复制到 myblog 的配置文件下，就是`config.toml`这玩意儿

```
cp themes/jane/exampleSite/config.toml ./
```

好，现在可以把博客在本地运行起来了

```
hugo server -t jane --buildDrafts
```

# 3.把博客放到远端仓库

Github 是个免费仓库，用它就完事了

当然需要你先在 github 上注册一下

完事之后，登录你的 github

---

### 新建一个仓库，存放你的博客

#### New Repositories

---

Repository name 格式要求：`用户名.github.io` (用户名小写)

---

别的不用管，下面直接点 Create Repository

---

#### 生成 `public` 文件夹

在终端下输入（myblog 目录下）

```
hugo --theme=jane --baseUrl="https://用户名.github.io" --buildDrafts
```

这时候会生成一个 `public` 文件夹

把这个 public 文件夹推送到 github 仓库就完事啦~

#### 把 `public` 文件夹推送到 Github

// 下面依次输入：

```
cd public
git init
git add .
git commit -m "提交的备注"
```

如果是第一次使用 git ，途中他会提示让你配置一下

```
  //设置用户邮箱
git config --global user.email "你的github邮箱"
  //设置用户名
git config --global user.name "你的github用户名"
```

跟远端关联 (也就是你的 github 地址 / 仓库地址)

```
git remote add origin https://github.com/用户名/用户名.github.io.git
```

然后，推到远端

```
git push -u origin master
```

需要输入用户名和密码

完事

---

以后访问博客就用下面的地址：

```
用户名.github.io
```

# 4.常用命令总结 :

在你的博客根目录下(blog)

```
创建一篇新文章
hugo new post/example.md
---
重新生成 public 文件夹
hugo
---
进入 public 文件夹
cd public
---
依次输入
git init ( git 初始化仓库 , 只需创建时输入一次 , 以后就省略这一步 )
git add .
git commit -m "提交的备注"
---
部署到远端
git push ( git 第一次提交需要指定分支 , 使用 git push -u origin master , 之后直接 git push )
```

# The_End
