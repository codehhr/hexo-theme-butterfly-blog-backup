---
title: 用脚手架搭建一个 vue 项目
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/sunrise.jpg
cover: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/vue/vue.jpg
date: 2021-02-27 09:54:01
tags:
  - Vue
  - Vue脚手架
categories:
  - Vue
  - Vue脚手架
---

# 一、需要安装 node 环境

> 下载地址: https://nodejs.org/en/
> 中文网: http://nodejs.cn/

#### 安装后为方便国内使用，可以把 npm 换成 taobao 的 cnpm (速度快)

```bash
npm install -g cnpm --registry=https://registry.npm.taobao.org
```

检查是否安装成功,查看版本号

![node](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/vue/node.png)

# 二、全局安装 vue 脚手架

全局安装可能需要管理员权限( Windows 以管理员身份运行; Linux 加 sudo )

```bash
npm install -g @vue/cli
或者用 cnpm
cnpm install -g @vue/cli
简写
cnpm i -g @vue/cli
```

#### 安装成功后可查看版本

```bash
vue -V  (大写V)
```

![vueversion](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/vue/vueversion.png)

# 三、创建项目

为方便编辑,我一般都在 `vscode` 里操作

## 1.比如创建一个叫 project 的项目

```bash
vue create project
```

#### 如果安装了 cnpm 就会询问是否使用淘宝镜像(cnpm)

![vuecreateusecnpm](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/vue/vuecreateusecnpm.png)

都可以,只是影响网速快慢,我装了 `cnpm`,这里我填 `Y`

## 2. 选择配置方式

![vuecreatechooseconf](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/vue/vuecreatechooseconf.png)

> #### 说明:
>
> - `Default (babel,eslint)`: 默认配置
> - `Manually select features`: 手动选择配置

键盘上下就可以选择,选 `Manually select features` (最下面那个),俺不用默认配置

## 3. 手动选择项目所需要的包

![vuecreateconf](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/vue/vuecreateconf.png)

> #### 说明:
>
> - `Babel`: Babel 编译,将 ES6 编译成 ES5,进行兼容
> - `TypeScript`: 给 JavaScript 添加特性的语言扩展
> - `Progressive Web App (PWA) Support`: 让网页渐进式变成 App
> - `Router`: Vue 路由
> - `Vuex`: Vue 状态管理
> - `CSS Pre-processors`: CSS 预编译器 (包括 SCSS/Sass、Less、Stylus)
> - `Linter / Formatter`: 代码检测和格式化
> - `Unit Testing`: 单元测试
> - `E2E Testing`: 端到端测试
>
> ##### 根据需求进行勾选,上下键选择,空格是取消或选中,选完最后回车

#### 如图:

![vuecreateconfafter](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/vue/vuecreateconfafter.png)

## 4. 选择版本

![vuecreatechooseversion](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/vue/vuecreatechooseversion.png)

## 5. 路由是否采用 history 模式

选啥都可以,之后可以改

![vuecreateusehistoryforrouter](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/vue/vuecreateusehistoryforrouter.png)

## 6. 选择 CSS 编译方法

![vuecreatepickcssway](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/vue/vuecreatepickcssway.png)

按需选择,我选的 `Less`

## 7. 选择代码规范

![vuecreatepickeslintway](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/vue/vuecreatepickeslintway.png)

我选的 `Standard config`

> #### 说明:
>
> - `eslint with ...` : 只进行报错提醒;
> - `eslint + A ...` : 不严谨模式;
> - `eslint + S ...` : 正常模式;
> - `eslint + P ...` : 严格模式;

## 8. 选择合适代码检验规范

![vuecreatelintonsave](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/vue/vuecreatelintonsave.png)

选 `lint on save`,也就是报存时检验

## 9. 选择放置配置的文件

![vuecreateconfplace](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/vue/vuecreateconfplace.png)

我选的第一个,放到一个独立文件里

## 10. 是否保存配置为以后使用

![vuecreatesaveconf](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/vue/vuecreatesaveconf.png)

先不保存 (`N`)

## 11. 安装完成

![vuecreatedone](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/vue/vuecreatedone.png)

## 12. 运行项目

其实安装完成后有提示

```bash
cd project (进入项目根目录)
npm run serve
```

![vuenpmrunserve](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/vue/vuenpmrunserve.png)

会在本地 `8080` 端口运行

#### 如图

![vuerunning](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/vue/vuerunning.png)

# The_End
