---
title: Android SDK相关命令
date: 2019-04-04 15:19:33
tags:
---

## aapt 

* 可以理解为编译安卓资源文件的，多了不说百度都有。是Android sdk自带的一款工具。


###  简单使用


####  安装

1. 前提要安装Android-sdk，运行aapt

<!--more-->

![alt text](https://s1.wacdn.com/wis/93/3acf851dfe78af29_1180x398.png)



2. 运行图中命令 android update sdk --no-ui --filter 'build-tool-23.0.1'（然而我执行失败了）不过失败了没有关系，运行Android sdk manager,安装图中的tools

![alt text](https://s1.wacdn.com/wis/93/ed3c4b7d27f65028_1330x504.png)


3. 成功

![alt text](https://s1.wacdn.com/wis/93/f0a86ef71a501b50_1810x1194.png)

### 简单命令

1. aapt dump badging XXX.apk 查看apk的包名等信息


2. aapt dump configurations XXX.apk 查看apk一些配置


其他的可以看下[这篇博客](http://blog.csdn.net/g19920917/article/details/20244937)，网上相关资源也很多，大家可以按照需求学习。


### 校验签名

* jarsigner -verify -verbose -certs apk包路径 校验签名


## adb

### 查看设备是否连接
* adb devices

### 安装安卓包
* adb install XXX(安装包路径)

### 覆盖安装（升级）
* adb install -r XXX (安装包路径)

