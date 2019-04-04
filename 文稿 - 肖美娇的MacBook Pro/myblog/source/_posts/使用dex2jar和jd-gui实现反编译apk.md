---
title: 使用dex2jar和jd-gui实现反编译apk
date: 2019-04-04 11:46:47
tags:
---


### 安装
* 下载dex2jar(Mac版本和Windows版本都有）
* 下载jd-gui(Mac版本和Windows版本都有）

资源都比较好找就不给出来了

<!--more--->

### 使用

#### 1.dex2jar下载并解压
* 解压后看到有个d2j-dex2jar.sh文件，先用chmod 777将文件变成可执行的

#### 2.将apk文件解压
* 解压后看到有个classes.dex文件，将此文件放到dex2jar解压后文件目录下
![](http://ww2.sinaimg.cn/large/006tNc79gy1ff4u6odtgkj30ro074dgd.jpg)

#### 3.将下载后的jd-gui解压
* 解压后看到.app文件打开
![](http://ww3.sinaimg.cn/large/006tNc79gy1ff4u89wgvtj30my068aa3.jpg)

#### 4.执行反编译脚本
* 回到dex2jar解压后的目录下，执行
`sh d2j-dex2jar.sh classes2.dex`
![](http://ww4.sinaimg.cn/large/006tNc79gy1ff4uak1c39j31900iw40t.jpg)

#### 5.用jd-gui打开生成的jar文件
![](http://ww4.sinaimg.cn/large/006tNc79gy1ff4ublvcb2j30m00j4t96.jpg)
* 就能看到里面的代码