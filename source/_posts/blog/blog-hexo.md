---
title: 用 Hexo 快速搭建博客
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/sunrise.jpg
cover: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/hexo/hexocover.jpg
date: 2020-02-01 18:32:26
tags:
  - hexo
  - 博客
categories:
  - 博客
  - hexo
---

# 如何做到一毛不拔的搭建网站

![s](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/emoji/s.png)

### 以下操作中需要安装的地方需要使用管理员权限,因为我不清楚哪里会出现 `permission denied`

---

# 1 . 安装 `nodejs`

![nodejs](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/hexo/nodejs.png)

---

### 对应 windows 用户，下载对应的 ".msi" 的文件安装就行

### Linux 和 Mac 用户...此处省略

---

安装成功后可以查看版本

```
node -v
```

```
npm -v
```

---

![version](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/hexo/version.png)

---

### 为方便国内使用，可以把 npm 换成 taobao 的 cnpm

```
npm install -g cnpm --registry=https://registry.npm.taobao.org
```

# 2 . 本地搭建

### 安装 `hexo`

```
cnpm install -g hexo-cli
```

查看版本,验证成功

```
hexo -v
```

### 创建一个文件夹，比如名为 `blog`

```
mkdir blog
```

### 进入 `blog` , 初始化`hexo`

```
hexo init
```

### 等他完事后,可以在 http://localhost:4000/ 下本地预览

```
hexo s
```

#### 如图 :

---

![s](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/hexo/server.png)

### 如果渲染不出来，尝试安装以下解决

```
cnpm install  hexo-renderer-pug hexo-renderer-stylus hexo-renderer-jade hexo-generator-feed hexo-generator-sitemap hexo-browsersync hexo-generator-archive --save
```

### 如果新建一篇文章

文件名最好为英文，方便操作

```
hexo n name
```

他会在 `source/_posts` 下生成一篇名为 name 的 markdown 文件，内容自己写

# 3 . 推到远端

登录你的 github , 新建一个仓库

![github](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/hexo/github.png)

仓库名为 用户名.github.io 用户名小写

![repo_name](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/hexo/repo_name.png)

现在是个空仓库

![empty](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/hexo/empty.png)

---

回到终端下

### 安装 `hexo-deployer`

```
cnpm install --save hexo-deployer-git
```

### 修改 \_config.yml 文件

在 blog 目录下

如图修改最下面 , repo 改为自己的仓库地址

![depolyer](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/hexo/deployer.png)

### 部署到远端

```
hexo d
```

![done](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/hexo/done.png)

你可以刷新 github 仓库, 里面已经有东西了

![unempty](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/hexo/unempty.png)

### 完事

---

### 你的博客地址就是:

用户名.github.io

# 4 . 更换主题

### hexo 主题 : https://hexo.io/themes/

每个主题里都有说明

比如：lx

在 blog 目录下

```
git clone https://github.com/blleng/hexo-theme-lx themes/lx
```

按照他说明的改一下就行了

把 `blog/_config.yml` 里的 `theme` 改成要换的主题名就完事了, 比如把 `landscape` 改成 `lx`

### 可以本地先预览一下

```
hexo s
```

### 推到远端

```
hexo g

hexo d
```

# 5 . 常用命令总结 :

```
创建一篇新文章
hexo n example
---
清理旧的数据
hexo clean
---
重新生成一下
hexo g
---
部署到远端
hexo d
```

# The_End
