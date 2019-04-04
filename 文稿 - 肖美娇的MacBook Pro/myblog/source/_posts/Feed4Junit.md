---
title: Feed4Junit
date: 2019-04-03 12:55:28
tags:
---


## 简介
* 是数据与代码分离的一个单测框架
* 在Junit测试框架上进行了扩展
* 支持csv和Excel文件数据源头，甚至支持直接连接数据库

<!--more-->
## idea引用
* maven工程增加依赖

```java
<!-- https://mvnrepository.com/artifact/org.databene/feed4junit -->
<dependency>
    <groupId>org.databene</groupId>
    <artifactId>feed4junit</artifactId>
    <version>1.1.5</version>
</dependency>

```

* 引包 import org.databene.feed4junit.Feeder;

## 参考文档

* [使用 Feed4JUnit 进行数据与代码分离的 Java 单元测试](https://www.ibm.com/developerworks/cn/java/j-lo-feed4junit/index.html)


## 采坑
1. 数据文件一定要放到工程根目录下，不是src目录。否则引不到。
2. 运行单个case带有@Test标签的报错：


```java
java.lang.Exception: No tests found matching Method testAccessCheck_CSV(sample.test.Feed4JfromFile) from org.junit.internal.requests.ClassRequest@2aa5fe93

	at org.junit.internal.requests.FilterRequest.getRunner(FilterRequest.java:37)
	at com.intellij.junit4.JUnit4IdeaTestRunner.startRunnerWithArgs(JUnit4IdeaTestRunner.java:49)
	at com.intellij.rt.execution.junit.IdeaTestRunner$Repeater.startRunnerWithArgs(IdeaTestRunner.java:47)
	at com.intellij.rt.execution.junit.JUnitStarter.prepareStreamsAndStart(JUnitStarter.java:242)
	at com.intellij.rt.execution.junit.JUnitStarter.main(JUnitStarter.java:70)
	
```

没有找到合适的解决办法，网上查了下直接运行整个Test类就不会报错，试了下确实是这样。


