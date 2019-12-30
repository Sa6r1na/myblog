---
title: Mac下zsh环境变量踩坑经验
date: 2019-12-30 11:17:21
tags:
---

### 一、配置bash_profile

/Library/Java/JavaVirtualMachines/jdk1.8.0_211.jdk/Contents/Home 打开终端，进入当前用户的home目录：

```
cd ~/
```

打开.bash_profile并编辑：

```
open .bash_profile
```

<!--more--->

在文件的末尾加入这一行语句：

```
export JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk1.8.0_211.jdk/Contents/Home
```

编辑后保存.bash_profile：

```
source .bash_profile
```



按照上述的修改之后，发现环境变量依然没有生效。



### 二、配置zshrc

按照如上修改了~/.bash_profile文件发现无效，并且提示 zsh: command not found 那么肯定是安装了zsh的缘故，因为安装zsh，~/.bash_profile就不会被执行，解决办法如下：

1.打开vim ~/.zshrc 将你要配置到环境变量配置到该文件中即可

2.打开vim ~/.zshrc 添加source ~/.bash_profile ，这样~/.bash_profile配置的环境变量同样有效



### 三、配置文件优先级

1）/etc/profile/ ---> 2) /etc/paths ---> 3) /etc/bashrc ---> 4) ~/.bash_profile 或  ~/.bashrc ---> 5) ~/.bash_login ---> 6) ~/.bash_profile 

其中，/etc/profile, /etc/paths,  /etc/bashrc 是系统级别配置文件，系统启动就会加载，后面几个是当前用户级的环境变量。后面3个按照从前往后的顺序读取，如果~/.bash_profile文件存在，则后面的几个文件就会被忽略不读了，如果~/.bash_profile文件不存在，才会以此类推读取后面的文件。~/.bashrc没有上述规则，它是bash shell打开的时候载入的。对此，修改前2个，需要ROOT权限。而且修改是全局的。一般不建议修改/etc/profile和/etc/bashrc 文件，而去修改/etc/paths文件



### 参考

作者：程序员雨晨https://www.jianshu.com/p/a85658902f26来源：简书著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。

作者：顾顾314链接：https://www.jianshu.com/p/27faa48acdd1来源：简书著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。

作者：TangFly
链接：https://www.jianshu.com/p/acc248904bdb
来源：简书
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。