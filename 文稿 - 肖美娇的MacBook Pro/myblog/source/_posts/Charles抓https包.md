---
title: Charles抓https包
date: 2019-04-04 11:48:46
tags:
---

##  初衷

* 需要抓https包的时候，不同手机安装证书各有不同。然后问身边人和自己研究总结了几点，希望对大家有用。总结起来两大块：一个Charles的配置；一个是手机上证书的安装（坑比较多）。

前提：手机要连着Charles的代理

<!--more--->

##   第一步：Charles的准备

### 1. Charles点击图中位置，会提示一个下载证书的地址，手机用浏览器输入。并下载

![](https://ww3.sinaimg.cn/large/006tNc79gy1fdf97jhusmj313d0etdir.jpg)

![](http://s1.wacdn.com/wis/527/d2d79d7728b2cbb3_779x175.png)

安装证书的链接：chls.pro/ssl

### 2. 配置charles的ssl 设置 
![](https://ww1.sinaimg.cn/large/006tNc79gy1fdf9b5zx7ij308y0cm75c.jpg)

![](https://ww4.sinaimg.cn/large/006tNc79gy1fdf9jmzrmxj30fr0bs0sz.jpg)

##  第二步：Android手机的准备工作

### 一. 按照第一步的1操作，如果手机浏览器不行，下载不下来，就换个浏览器（比如：手机自带浏览器下载后安装不了，换QQ浏览器居然就好了）

### 二. 换了浏览器还是提示安装失败的话，点击手机设置-》安全-》从sd卡安装，找到刚刚下的证书的名字。进行安装
![](https://ww2.sinaimg.cn/large/006tNc79gy1fdf9ejvyflj30bt0l0mxh.jpg)

### 三. 如果这样还是不行（比如傲娇的Android 7.0的华为手机），

#### 1. 浏览器下载的时候会提示你这个证书的下载路径，如图
![](https://ww1.sinaimg.cn/large/006tNc79gy1fdf9g0d7yuj30bt0l0dfx.jpg)
#### 2. 用手机的文件管理器打开这个文件，然后移动到sd卡的目录下。如图，（可以放在一个好找的目录比如：/emulated/0/）
![](https://ww3.sinaimg.cn/large/006tNc79gy1fdf9gz463hj30bt0l0gmg.jpg)

#### 3. 还是回到设置里面的从sd卡读取，点击图中蓝色部分，然后找到刚刚移动后的证书，点击进行安装就可以了
![](https://ww1.sinaimg.cn/large/006tNc79gy1fdf9i6j6maj30bt0l0mx7.jpg)


##  第三步：iOS手机的准备工作

### 按照提示安装就好了，iOS 11以上的手机要设置-》关于手机-》证书信任设置里信任刚刚的证书就好了