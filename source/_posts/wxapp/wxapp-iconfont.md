---
title: 微信小程序使用彩色图标(阿里巴巴 iconfont Symbol 的用法)
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/sunrise.jpg
cover: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/wx/wxminipro.jpg
date: 2020-08-14 17:26:49
tags:
  - 微信小程序
  - iconfont
categories:
  - 微信小程序
---

# 前提

需要安装好 nodejs (略)

用于下载插件

# 安装插件

```
npm install mini-program-iconfont-cli --save-dev
```

![miniprogram](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/wx/miniprogram.png)

# 初始化配置文件

```
npx iconfont-init
```

![initiconfontjson](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/wx/initiconfontjson.png)

### 会生成一个 inconfont.json 文件

![iconjsonfile](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/wx/iconjsonfile.png)

### 填入给你的 Symbol 链接

![jsurl](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/wx/jsurl.png)

# 生成小程序组件

```
npx iconfont-wechat
```

![initwechaticon](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/wx/initwechaticon.png)

# 使用图标

### 在 app.json 文件里设置使用图标组件

```json
"usingComponents": {
    "iconfont": "/iconfont/iconfont"
  }
```

### 在 wxml 中使用

```html
<iconfont name="dog"></iconfont>
```

### 如图:

![dog](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/wx/dog.png)

# 更改图标大小

在 `iconfont.wxml` 中可以随意修改,每次找有点麻烦
![iconfontwxml](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/wx/iconfontwxml.png)

也不建议你去修改 `iconfont.js` 里的 `svgSize` 的大小

可以修改 `iconfont.json` 里 `default_icon_size` 的值
![resize](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/wx/resize.png)

然后更新一下 `iconfont-wechat` 就可以设置图标全局的大小了

```
npx iconfont-wechat
```

# 项目更新图标

当你的项目图标更新了，需要更新你的 Symbol 链接，然后在 iconfont.json 里修改参数 symbol_url

然后更新一下 `iconfont-wechat` 就可以了

```
npx iconfont-wechat
```

# The_End
