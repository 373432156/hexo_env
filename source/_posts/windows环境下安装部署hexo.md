---
title: windows环境下安装部署hexo
date: 2019-08-12 23:32:53
tags: 
- hexo
categories:
- tools
- hexo
---

# 在windows下安装hexo

> 转载链接：https://www.jianshu.com/p/343934573342

hexo是什么？简单的说，就是一个静态博客的生成工具，我这个博客就是就是基于hexo生成的。文章结尾的官网链接中也有介绍。

昨天才把这个博客用hexo折腾出来，所以想记录下来折腾的过程，留着以后备用。

这里只说如何在windows下成功安装hexo并运行起来，关于主题以及配置不做记录。

<!--more-->

### 安装node.js

因为hexo是基于node.js的，所以node.js是必须要装的，安装也特别简单，去 [官网](https://link.jianshu.com?t=https%3A%2F%2Fnodejs.org%2Fen%2F) 下载适合自己windows的版本。安装过程一直下一步就行了，什么也不用选，在网上查资料的时候，看到有说要在Custom Setup这一步记得选**Add to PATH**，但我在安装的时候这个选项是默认选好的，不用动它，也许是版本的原因，建议在安装时留意一下，毕竟自己配置环境变量还是有点麻烦。

安装好以后，打开CMD命令窗口，输入 `npm -v` ，如果出现版本号，那说明安装成功了并且环境变量也配置好了，如果是未知命令那就要配置一下环境变量。

### 安装hexo

这一步我是用git bash来安装的，如果安装了git，那么就可以用git bash，如果没有装，那就用CMD窗口，效果是一样一样的，命令都是一样的。

安装hexo的命令：

```
npm install -g hexo-cli
```

这一步安装的比较慢，可能跟网络环境有关，我在用git bash安装的时候半天没反应，然后用CMD安装成功了。

输入 `hexo -v` 出现一系列的版本号就是安装成功啦，就像下面这样：

```
$ hexo -v
hexo: 3.4.2
hexo-cli: 1.0.4
os: Windows_NT 6.1.7601 win32 x64
http_parser: 2.7.0
node: 8.9.1
v8: 6.1.534.47
uv: 1.15.0
zlib: 1.2.11
ares: 1.10.1-DEV
modules: 57
nghttp2: 1.25.0
openssl: 1.0.2m
icu: 59.1
unicode: 9.0
cldr: 31.0.1
tz: 2017b
```

### 生成博客

从现在开始，我们就可以用hexo来生成一个博客了。

首先新建一个文件夹，位置随意，然后 `cd` 到这个文件夹下，运行命令：

```
hexo init
```

hexo会将这个文件夹初始化成一个博客专用文件夹，生成过程稍微要点时间，耐心等待。

初始化完成后，会有一个默认主题以及一个hello-word的默认文章。所以我们可以先生成博客来看一下效果，运行命令：

```
hexo generate  //可以简写成 hexo g
```

然后hexo会开始生成博客，生成结束后，会多出一个public的文件夹，这个文件夹就是hexo生成的一个完整的静态网站，也就是我们的博客。网站生成好了，我们要浏览它，所以要开启一下服务器，运行命令：

```
hexo server  //可以简写成 hexo s
```

然后打开浏览器，输入 `localhost:4000` 就可以浏览我们的博客了。

### 远程部署

远程部署指的是，博客在我们本地生成好了以后部署到远程仓库去，如果远程仓库支持pages服务的话，那就可以通过这样的方法发布和更新博客。

要使用远程部署需要先安装hexo-deployer-git，注意，这是适用于git类型仓库的方法，其他仓库的方法在文章结尾提供的官网连接中有说明。

运行命令：

```
npm install hexo-deployer-git --save
```

安装好hexo-deployer-git后，修改博客目录配置文件中的deploy字段：

```
deploy:
  type: git
  repo: git仓库项目地址
  branch: 分支
  message: 自定义提交说明，这个字段可以没有
```

如果git仓库是ssh，则需要生成.ssh，这是git的操作，不做详述。

有关于博客主题的更换，以及详细配置等 参见官网 [https://hexo.io/zh-cn/docs/](https://link.jianshu.com?t=https%3A%2F%2Fhexo.io%2Fzh-cn%2Fdocs%2F)

::smile: