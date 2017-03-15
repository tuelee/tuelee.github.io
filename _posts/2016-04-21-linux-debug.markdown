---
layout: default
title:  "Linux 学习"
date:   2016-04-21 17:50:00
categories: main
---

# Linux 学习
## 1. View Animation:
  

## 2.Property animation:


### 2.1 object animation:

### 2.2 Value animator

典型情况下Activity的生命周期
针对一个特定的Activity,第一次启动，回调如下：onCreate->onStart->onResume
当用户打开新的Activity或切换到桌面的时候，回调如下：onPause->onStop。有一种特殊情况，如果新的Activity采用了透明主题，那么当前Activity不会调用onStop
当用户再次回到原来Activity时，回调如下:onRestart->onStart->onResume
当用户按back键回退时，回调如下：onPause->onStop->onDestroy
当Activity被系统回收后再次打开，生命周期方法回调过程和第一种情况一样，注意只是生命周期方法一样，不代表所有过程都一样。
onCreate和onDestroy标识着Activity的创建和销毁；onStart和onStop标识Activity是否可见，onResume和onPause标志Activity是否在前台

异常情况下生命周期分析
资源相关的系统配置发生改变导致Activity被杀死并重新创建，比如屏幕旋转
onSaveInstanceState和onRestoreInstanceState，系统自己为我们做了一定的恢复工作。
系统只有在Activity异常终止的时候才会调用onSaveInstanceState和onRestoreInstanceState来保存和恢复数据，其他情况下不会触发这个过程
资源内存不足导致优先级低的Activity被杀死

Activity的启动模式
standard标准模式，创建多个实例并一一入栈
SingleTop如果Activity已经位于任务栈的栈顶，那么此Activity不会被重新创建，同时它的onNewIntent方法会被回调，通过此方法的参数我们可以取出当前请求的信息。
SingleTask只要Activity在一个栈中存在，具有ClearTop属性
S1中ABC，D属于S2, 
D和S2都不存在，先创建S2，后创建D放入s2
S1中ABC, D属于S1
直接创建D放入S1
S1中ADBC，D属于S1
BC出栈，AD

Check out the [Jekyll docs][jekyll] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll's GitHub repo][jekyll-gh].

[jekyll-gh]: https://github.com/mojombo/jekyll
[jekyll]:    http://jekyllrb.com