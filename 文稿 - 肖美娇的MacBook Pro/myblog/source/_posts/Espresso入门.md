---
title: Espresso入门
date: 2019-04-04 11:25:02
tags:
---

### espresso 简介

* google官方开源的Android白盒测试框架（原理我就不讲了，因为讲也讲不透彻:joy: ） [官网地址](https://developer.android.google.cn/studio/test/espresso-test-recorder?hl=zh-cn)
* 可以通过录制生成代码和手写代码两种方式写测试用例。
* Espress有3个特点：

1. 第一个收录在Android Testing Supporting Library底下的测试框架
2. 模拟用户的操作
3. 自动等待，直到UI线程空闲，才会执行测试代码


<!--more--->

### why espresso

* 稳定，高效；和开发共建
* 最吸引人的一点不过就是他的稳定了，为什么这么说。一般的UI测试框架，都会通过sleep几秒，或者校验元素是否出现等等来提升稳定性。那espresso和其他的测试框架相比的一大优点就是：他会等着被测APP的UI线程执行完毕之后再去执行test APP的线程。（具体怎么实现的，看后续例子的IdlingResource）
* 为什么说是高效：他偏白盒，能直接打开被测的Activity，而不用想其他黑盒的框架一样要冷启动APP后一步步点击到具体的页面




### 经典api图
 ![](http://s1.wacdn.com/wis/525/70b3df66a963c180_1431x2000.png)
 
 
### before 
* 因为espresso是白盒的自动化测试框架，所以前提是你本地Android工程要能build过，正常打包。

* 关于build不过的各种报错以及解决办法这里不详细阐述。

### espresso应用
###  录制
* 工具栏   run-> record espresso test
* 在手写代码遇到瓶颈时，可以录制参考下。（录制的过程在我们APP上很卡、很慢，不推荐使用；但在小demo上还算快速高效，不清楚是否是记账APP工程庞大）

###  手写
#### 1. dependency
* 在应用模块的 build.gradle 文件中指定测试库依赖项

```
dependencies {
    // Required for local unit tests (JUnit 4 framework)
    testCompile 'junit:junit:4.12'

    // Required for instrumented tests
    androidTestCompile 'com.android.support:support-annotations:24.0.0'
    androidTestCompile 'com.android.support.test:runner:0.5'
}
```

* dependency添加好之后，sync一下

#### 2.demo举例
写UI自动化测试用例，归结起来就是3步：

1. 定位View控件

2. 操作View控件

3. 校验View控件的状态

对应Espresso，就是以下3个方法的调用：

onView(ViewMatcher)
  .perform(ViewAction)
  .check(ViewAssertion);
  
下面举一个的demo

```

import android.support.test.espresso.contrib.RecyclerViewActions;
import android.support.test.espresso.Espresso;
import android.support.test.rule.ActivityTestRule;
import android.support.test.runner.AndroidJUnit4;
import android.test.suitebuilder.annotation.LargeTest;
import org.junit.After;
import org.junit.Before;
import org.junit.Rule;
import org.junit.Test;
import org.junit.runner.RunWith;

import static android.support.test.espresso.Espresso.onView;
import static android.support.test.espresso.action.ViewActions.click;
import static android.support.test.espresso.action.ViewActions.scrollTo;
import static android.support.test.espresso.action.ViewActions.clearText;
import static android.support.test.espresso.action.ViewActions.typeText;
import static android.support.test.espresso.assertion.ViewAssertions.matches;
import static android.support.test.espresso.matcher.ViewMatchers.isDisplayed;
import static android.support.test.espresso.matcher.ViewMatchers.withId;

@RunWith(AndroidJUnit4.class)
@LargeTest
public class SettingCurrencyTest {

    @Rule
    public ActivityTestRule<SettingMgrV2> mActivityTestRule =
        new ActivityTestRule<>(SettingMgrV2.class);

    @Before
    public void registerIdlingResource() {
        Espresso.registerIdlingResources(EspressoIdlingResource.getIdlingResource());
    }

    /**
     * Unregister your Idling Resource so it can be garbage collected and does not leak any memory.
     */
    @After
    public void unregisterIdlingResource() {
        Espresso.unregisterIdlingResources(EspressoIdlingResource.getIdlingResource());
    }

    @Test
    public void toCurrencyPage() {
        onView(withId(R.id.money)).perform(scrollTo(), click());
        onView(withId(R.id.currency_view)).check(matches(isDisplayed()));
    }

    @Test
    public void selectCurrency() {
        toCurrencyPage();
        onView(withId(R.id.currency_view)).perform(RecyclerViewActions.actionOnItemAtPosition(4, click()));
        //不能用手机号的控件ID，因为上次如果是手机号密码登录会导致ID不是验证码方式的ID
        onView(withId(R.id.checkbox_agreement)).check(matches(isDisplayed()));
        //mockLogin(1, "XXXXX", "");
        mockLogin(2, "XXXXX", "123456");

    }
}

```

Activity

1. 先打开被测的Activity（Activity的类需要你熟悉代码找出）
2. test标签写执行的测试用例脚本（本例写了最简单点的view上找元素然后点击、输入等操作）

IdlingResource：

1. 测试用例启动，注册MyIdlingResource
2. 启动被测Activity
3. Activity初始化，启动数据加载过程
4. Activity数据加载完成，执行测试用例方toCurrencyPage()
5. 测试用例结束，反注册MyIdlingResource

#### 3.运行测试用例
* 手机要连着电脑或者模拟器
* 他会再手机上装两个APP，一个被测APP，一个test APP
* 测试结果会在控制台展示


### 总结
* 本篇写了espresso入门的知识，view上最基本的点击等操作，当然还有复杂一点的，比如被测控件是listview、CheckBox等等，后续学到了再给大家分享。
* 安利espresso因为对于了解客户端代码很有帮助。可以在写测试脚本中，熟悉Android工程。