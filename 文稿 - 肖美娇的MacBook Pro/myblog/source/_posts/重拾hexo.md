---
title: 重拾hexo
date: 2018-12-14 15:05:53
tags:

---


## hexo是什么

* 方便的搭建自己博客平台的工具
* 能自动关联GitHub
* 能本地预览、快速部署

## 环境准备

* 下载node.js并安装（官网下载安装），默认会安装npm。
* 下载安装git（官网下载安装）
* 下载安装hexo。方法：命令行 运行npm install -g hexo（要翻墙）

<!--more-->

## 本地搭建hexo静态博客
* 新建一个文件夹，如MyBlog
* 进入该文件夹内，右击运行git，输入：hexo init（生成hexo模板，可能要翻墙）
* 最后运行：hexo server （运行程序，访问本地localhost:4000可以看到博客已经搭建成功）



## 将博客与Github关联
* 在Github上创建名字为XXX.github.io的项目，XXX为自己的github用户名。

* 打开本地的MyBlog文件夹项目内的_config.yml配置文件，将其中的type设置为git(看图冒号后面有空格，我之前就被坑了)

![](https://ws1.sinaimg.cn/large/006tNbRwly1fy6ax52ublj314s078gn7.jpg)

  * 运行：npm install hexo-deployer-git –save
  * 运行：hexo g（本地生成静态文件）
  * 运行：hexo d（将本地静态文件推送至Github）

然后打开浏览器，直接访问 https://sa6r1na.github.io/ 就可以。


## 写第一篇文章
* 在MyBlog目录下执行：hexo new “我的第一篇文章”，会在source->_posts文件夹内生成一个.md文件。
* 编辑该文件（遵循Markdown规则）
	* 修改起始字段：
	* title 文章的标题
	* date 创建日期 （文件的创建日期 ）
	* updated 修改日期 （ 文件的修改日期）
	* comments 是否开启评论 true
	* tags 标签
	* categories 分类
	* permalink url中的名字（文件名）

* 编写正文内容（MakeDown）
	* hexo clean 删除本地静态文件（Public目录），可不执行。
	* hexo g 生成本地静态文件（Public目录）
	* hexo deploy 将本地静态文件推送至github（hexo d）

	
	
## 主题
* 默认的主题比较丑，像我这种外貌协会一定会找个自己喜欢的主题的。方式可以通过GitHub上搜“hexo theme”,可以先看下预览图，找到自己喜欢的。
* 按照github上的介绍，修改_config.yml配置文件

![](https://ws3.sinaimg.cn/large/006tNbRwly1fy6b3p2psqj30hg05a74m.jpg)

* 预览下我的博客

![](https://ws1.sinaimg.cn/large/006tNbRwly1fy6bfxt7npj31ee0psadb.jpg)


## 总结

* 以上，赶紧体验下hexo来写自己的博客
* 其他的可以看下面这篇博客，有其他的详细介绍 [Hexo搭建博客教程](https://thief.one/2017/03/03/Hexo%E6%90%AD%E5%BB%BA%E5%8D%9A%E5%AE%A2%E6%95%99%E7%A8%8B/)