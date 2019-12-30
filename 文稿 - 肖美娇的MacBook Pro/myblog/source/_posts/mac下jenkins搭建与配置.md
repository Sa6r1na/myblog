---
title: mac下jenkins搭建与配置
date: 2019-05-29 14:50:38
tags:
---

## 一、前提

### 1. java环境

### 2. Apache
* mac系统自带

<!--more--->

## 二、安装Jenkins

### 1.下载安装Jenkins

### 2.启动Jenkins

#### 浏览器打开
*  localhost:8080，能正常进入Jenkins首页证明安装成功

#### 命令行

```
Java -jar jenkins.war
```

遇到
Error: Unable to access jarfile jenkins.war

## 三、配置Jenkins

### 1. 重启电脑
你会发现Jenkins给你的电脑新增了一个用户，名字就叫Jenkins（用原来的账户登录就可以）。重启后输入localhost:8080,进入重设初始密码页面，密码在密码在/Users/userName/.jenkins/secrets/initialAdminPassword**文件（权限不够的可能要sudo打开）把密码填入密码输入框中


### 2.建议安装配置
* 选择推荐插件安装就行
* 等Jenkins重启完成

### 3.创建管理员账号
* 用户名：LB
* 密码：*****
* 全名：****
* 邮箱：****@****.com

登录成功，进入Jenkins初始界面


### 4.系统设置
* 选择“系统管理”——“系统设置”，进入系统设置界面（可以管理全局属性、配置邮件通知）
全局属性下面，勾选Environment variables，增加一对键值对：
* LANG = zh_CN.UTF-8
* PATH = (终端中执行 echo $PATH 命令的输出，为一堆路径)


## 四、新建项目

### 


## 参考

[macOS Jenkins安装&配置](https://www.jianshu.com/p/9dc3b45fbbec)