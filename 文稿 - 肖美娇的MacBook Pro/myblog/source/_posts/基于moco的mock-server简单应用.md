---
title: 基于moco的mock server简单应用
date: 2018-04-04 13:41:25
tags:
---


**提起mock大家应该就知道是干嘛用的了，再次再介绍一种简单的方式，基于moco的mock server。步骤很简单：**

**1.** 首先，要 [下载个moco的jar](/uploads/files/1482402665143-moco-runner-0.10.2-standalone.jar)  到桌面

**2.** 在桌面建一个json文件，例如： 

      [{ "request" : { "uri" : "/hello" }, "response" : { "text" : "Hello  World !!"  } ]
      

清晰易懂，把你的请求和结果返回写上。

<!--more-->

**3.** 在桌面的路径执行命令（cmd和mac终端都可以,以管理员模式运行）：

     java -jar moco-runner-0.10.2-standalone.jar start -p 5638 -c data.json

**注意**：执行命令的时候要在这个jar的文件目录下，尽量json文件和jar文件放到一起；
-p 表示端口号  可以自定义 -c 后面加json文件名

**4.** 如图就启动成功了
![alt text](http://s1.wacdn.com/wis/53/515d4c2949c3f6be_646x204.png)

**5.** 在浏览器访问 http://localhost:5638/hello  就能得到结果
![alt text](http://s1.wacdn.com/wis/53/2e6e2b2012c995a8_361x125.png)


是不是很简单！