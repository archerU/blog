---
title: animation(动画)
<!--date: 2015-09-01 20:33:26      #用命令会自动生成，也可以自己写，所以文章时间可以改-->
<!--categories: css3 #文章的分类，这个可以自己定义-->
<!--tags: css3 #tag，为文章添加标签，方便搜索-->
---

[W3C官网－英文文档阅读最佳](https://www.w3.org)

## 快捷属性

| 属性 | 描述 |
| ---  | ---- |
| @keyframes | 规定动画 |
| animation | 所有动画属性的简写属性，除了 animation-play-state 属性 |
| animation-name | 规定 @keyframes 动画的名称 |
| animation-duration | 规定动画完成一个周期所花费的秒或毫秒。默认是 0 |
| animation-timing-function | 规定动画的速度曲线。默认是 "ease" |
| animation-delay | 过渡效果(延迟)开始时间,默认是0 |
| animation-iteration-count | 规定动画被播放的次数。默认是 1 |
| animation-direction | 规定动画播放方向，默认是 "normal" |
| animation-play-state | 规定动画是否正在运行或暂停。默认是 "running" |
| animation-fill-mode | 规定对象动画时间之外的状态 |

## 属性详解
#### [大漠整理animation](http://www.w3cplus.com/content/css3-animation)
### 1.animation-name

```
  animation-name: none | IDENT[,none | IDENT]*;
```
>IDENT是由Keyframes创建的动画名。

>none为默认值，当值为none时，将没有任何动画效果。

>可以同时附几个animation给一个元素，我们只需要用逗号“，”隔开。

### 2.animation-durtion

```
  animation-duration: <time>[,<time>]*
```
> time为数值，单位为s （秒.）其默认值为“0”。

### 3.animation-timing-function

[贝塞尔曲线工具](http://cubic-bezier.com)

```
animation-timing-function:ease | linear | ease-in | ease-out | ease-in-out | cubic-bezier(<number>, <number>, <number>, <number>) [, ease | linear | ease-in | ease-out | ease-in-out | cubic-bezier(<number>, <number>, <number>, <number>)]* 
```
1、ease：（逐渐变慢）默认值，ease函数等同于贝塞尔曲线(0.25, 0.1, 0.25, 1.0).

2、linear：（匀速），linear 函数等同于贝塞尔曲线(0.0, 0.0, 1.0, 1.0).

3、ease-in：(加速)，ease-in 函数等同于贝塞尔曲线(0.42, 0, 1.0, 1.0).

4、ease-out：（减速），ease-out 函数等同于贝塞尔曲线(0, 0, 0.58, 1.0).

5、ease-in-out：（加速然后减速），ease-in-out 函数等同于贝塞尔曲线(0.42, 0, 0.58, 1.0)

6、cubic-bezier：（该值允许你去自定义一个时间曲线）， 特定的cubic-bezier曲线。 (x1, y1, x2, y2)四个值特定于曲线上点P1和点P2。所有值需在[0, 1]区域内，否则无效。

### 4.animation-delay

```
 animation-delay: <time>[,<time>]*
```
> time为数值，单位为s(秒)，其默认值也是0。

### 5.animation-iteration-count

```
  animation-iteration-count:infinite | <number> [, infinite | <number>]* 
```
> number为数字，其默认值为“1”；infinite为无限次数循环。

### 6.animation-direction

```
  animation-direction: normal | alternate [, normal | alternate]* 
```
>animation-direction是用来指定元素动画播放的方向，其只有两个值，默认值为normal，如果设置为normal时，动画的每次循环都是向前播放；另一个值是alternate，他的作用是，动画播放在第偶数次向前播放，第奇数次向反方向播放。

### 7.animation-play-state

```
animation-play-state:running | paused [, running | paused]* 
```
>animation-play-state主要是用来控制元素动画的播放状态。其主要有两个值，running和paused其中running为默认值。他们的作用就类似于我们的音乐播放器一样，可以通过paused将正在播放的动画停下了，也可以通过running将暂停的动画重新播放，我们这里的重新播放不一定是从元素动画的开始播放，而是从你暂停的那个位置开始播放。另外如果暂时了动画的播放，元素的样式将回到最原始设置状态。这个属性目前很少内核支持，所以只是稍微提一下。




