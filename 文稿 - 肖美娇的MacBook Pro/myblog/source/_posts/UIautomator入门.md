---
 title: UIautomator入门
 
 date: 2018-12-11 13:34:01
 tags:
 
---

## 小感想

* 想学点UI自动化测试的脚本，试着琢磨琢磨了UIAutomator。网上相关的一些小资料都比较过时了，一些积累的小经验在这里做个总结。还不清楚这个uiautomator的流行程度，以及有没有必要深入研究，有这方面的大神可以交流下，指点迷津。

### 1.安装&环境准备

* jdk环境
* ant工具（mac用户brew install 没有问题；完事试一下ant -version）
* Android-sdk 必备
* idea (目前比较流行的IDE，但是相关的uiautomator介绍真是少啊）

<!--more-->

### 2.建立测试工程

* 用idea新建个java工程，选择command line app类型。
![](https://ww1.sinaimg.cn/large/006y8lVajw1fc1xaocqb8j31kw0z3jw1.jpg)

* 添加junit.jar 和 android.jar uiAutomator.jar:
模块里面junit可以通过添加maven的依赖方式添加；另外两个直接添加就可以，目录在Android sdk目录下。/usr/local/Cellar/android-sdk/24.4.1_1/platforms/android-25/ 具体目录取决于你配置的Android-sdk的api目录。
![](https://ww1.sinaimg.cn/large/006y8lVajw1fc1xdmh1j5j31kw1780y7.jpg)

![](https://ww4.sinaimg.cn/large/006y8lVajw1fc1xic5txpj31280s243s.jpg)


* 在测试工程src目录下新建package，命名随意。然后代码写上
![](https://ww3.sinaimg.cn/large/006y8lVajw1fc1xkrue3xj31kw0usamt.jpg)

### 3.查看Android版本sdk的ID值

* 在\Android-sdk\tools\目录下，输入android list.找到项目配置的android api 例如：我的api是25 id是3.
![](https://ww3.sinaimg.cn/large/006tNbRwjw1fc1ybz3q0mj31ea0x67hg.jpg)

### 4.生成build.xml文件
仍然当前目录（Android-sdk\tools\）运行命令 android create uitest-project -n name -t android-sdk-ID -p project_path
例如： `android create uitest-project -n myUIautomator -t 3 -p /Users/sabrina/Documents/repository/myUIautomator`

name 是生成jar包的名字可以自己定义；-t android-sdk的id刚才通过命令android list 查看到的；-p后面加路径，项目的路径。运行命令后，将会在工程的根目录下生成build.xml文件。

### 5.ant配置build.xml文件

* 刚开始被这个坑了好久，xml文件里面ant.properties位置是红色的，确一直没有找到原因，猜测一定是ant没有配置什么。百度了下idea配置ant。如下图，点击ant build.把刚才的build.xml文件添加上去。点击运行能成功运行证明添加没有什么问题。

![](https://ww3.sinaimg.cn/large/006tNbRwjw1fc1y026evtj30ko15mdie.jpg)

### 6.ant build生成
* 进入工程目录，执行ant build。不出意外会提示成功，会在工程的bin目录下生成jar文件。

![](https://ww1.sinaimg.cn/large/006tNbRwjw1fc1y4lueqmj31ea0x6qkl.jpg)

### 7.将jar文件push到手机data/local/tmp目录

* `adb push <jar文件路径> /data/local/tmp`
* `adb shell uiautomator runtest <jar文件名> -c <工程中的类名（包含包名）>`

例：`adb shell uiautomator runtest /data/local/tmpmyUIautomator.jar -c com.sabrina.CheckSize` 

手机便会执行脚本了，算是能跑，小白入门啦。
![](https://ww2.sinaimg.cn/large/006tNbRwgy1fcgvlc9kcfj30na026749.jpg)

![](https://ww4.sinaimg.cn/large/006tNbRwgy1fcgvn76wnpj317u0260sq.jpg)

![](https://ww2.sinaimg.cn/large/006tNbRwgy1fcgvnjmeglj31d80t6dil.jpg)