---
layout: default
title:  "Android动画"
date:   2016-02-12 17:50:00
categories: main
---

View Animation;  Drawable Animation; Property Animation

1.View Animation:
支持简单的缩放、平移、旋转、透明度基本的动画
Interpolator :用于修改一个动画过程中的速率，可以定义各种各样的非线性变化函数，比如加速、减速等。
View Animation不足
只能为view添加动画；
功能简单，不支持背景颜色的动画
只改变view的绘制效果，view的属性保持不变，比如缩放后，可点击区域还是原来的位置和大小。

View Animation的使用：
{% highlight ruby %}
final Animation buttonAnimation = AnimationUtils.loadAnimation(
				this.getContext(), R.anim.animation);
{% endhighlight %}

其中animation的配置文件为

{% highlight ruby %}
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android">
	<scale android:fromXScale="1.0" android:toXScale="1.5" android:interpolator="@android:anim/accelerate_decelerate_interpolator"
		android:fromYScale="1.0" android:toYScale="1.5" android:pivotX="50%"
		android:pivotY="50%" android:fillAfter="true" android:duration="5000" />
	<set>
		<alpha xmlns:android="http://schemas.android.com/apk/res/android"
			android:fromAlpha="0.2" android:toAlpha="1.0" android:duration="3000" />
		<rotate android:fromDegrees="0" android:toDegrees="360"
			android:toYScale="0.0" android:pivotX="50%" android:pivotY="50%"
			android:startOffset="700" android:duration="4000" />
		<translate android:fromXDelta="100%" android:toXDelta="00%"
			android:fromYDelta="60%" android:toYDelta="00%" android:duration="3000"
			android:zAdjustment="bottom" />
	</set>
</set>
{% endhighlight %}

2.Property animation:
很强劲的动画框架，几乎可以为所有的事物加上动画效果;一个属性动画在某一个时间段，改变的是一个对象的一个属性值


2.1 object animation:
提供了ofInt、ofFloat、ofObject，这几个方法都是设置动画作用的元素、作用的属性、动画开始、结束、以及中间的任意个属性值。当对于属性值，只设置一个的时候，会认为当然对象该属性的值为开始（getPropName反射获取），然后设置的值为终点。如果设置两个，则一个为开始、一个为结束
动画更新的过程中，会不断调用setPropName更新元素的属性，所有使用ObjectAnimator更新某个属性，必须得有getter（设置一个属性值的时候）和setter方法
如果操作对象的该属性方法里面，比如上例的setRotationX如果内部没有调用view的重绘，则你需要自己按照下面方式手动调用。
2.2 Value animator
ValueAnimator并没有在属性上做操作, 不需要操作的对象的属性一定要有getter和setter方法，可以自己根据当前动画的计算值，来操作任何属性

Check out the [Jekyll docs][jekyll] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll's GitHub repo][jekyll-gh].

[jekyll-gh]: https://github.com/mojombo/jekyll
[jekyll]:    http://jekyllrb.com