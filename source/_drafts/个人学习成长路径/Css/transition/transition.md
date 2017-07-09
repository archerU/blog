---
title: transition(过渡)
---

[W3C官网－英文文档阅读最佳](https://www.w3.org)

## 快捷属性

|  属性  | 描述  |
| ----- | ------|
| transition | 简写属性，用于在一个属性中设置四个过渡属性|
| transition-property | 过渡的css(属性)名称 |
| transition-duration | 过渡效果开始到结束的(持续)时间,默认是0|
| transition-timing-function | 过渡效果的时间曲线(贝塞尔曲线),默认是"ease" |
| transition-delay | 过渡效果(延迟)开始时间,默认是0 |

> transition ： [<'transition-property'> || <'transition-duration'> || <'transition-timing-function'> || <'transition-delay'>]

## 属性详解
#### [大漠整理transition](http://www.w3cplus.com/content/css3-transition)
### 1.transition-property
[w3c官网－transtion支持属性查看](https://www.w3.org/TR/css3-transitions/#properties-from-css-)

```
 transition-property ： none | all | [ <IDENT> ] [ ',' <IDENT> ]*
```
> none(没有属性改变)；all（所有属性改变）这个也是其默认值；indent（元素属性名）

### 2.transition-duration

```
 transition-duration ： <time> [, <time>]* 
```
> time为数值，单位为s（秒）或者ms(毫秒),可以作用于所有元素，包括:before和:after伪元素。其默认值是0，也就是变换时是即时的。

### 3.transition-timing-function

[贝塞尔曲线工具](http://cubic-bezier.com)

```
 transition-timing-function ： ease | linear | ease-in | ease-out | ease-in-out | cubic-bezier(<number>, <number>, <number>, <number>) [, ease | linear | ease-in | ease-out | ease-in-out | cubic-bezier(<number>, <number>, <number>, <number>)]* 

```
1、ease：（逐渐变慢）默认值，ease函数等同于贝塞尔曲线(0.25, 0.1, 0.25, 1.0).

2、linear：（匀速），linear 函数等同于贝塞尔曲线(0.0, 0.0, 1.0, 1.0).

3、ease-in：(加速)，ease-in 函数等同于贝塞尔曲线(0.42, 0, 1.0, 1.0).

4、ease-out：（减速），ease-out 函数等同于贝塞尔曲线(0, 0, 0.58, 1.0).

5、ease-in-out：（加速然后减速），ease-in-out 函数等同于贝塞尔曲线(0.42, 0, 0.58, 1.0)

6、cubic-bezier：（该值允许你去自定义一个时间曲线）， 特定的cubic-bezier曲线。 (x1, y1, x2, y2)四个值特定于曲线上点P1和点P2。所有值需在[0, 1]区域内，否则无效。

### 4.transition-delay

```
  transition-delay ： <time> [, <time>]* 
```
> time为数值，单位为s（秒）或者ms(毫秒),可以作用于所有元素，包括:before和:after伪元素。其默认值是0，也就是变换时是即时的。


### 补充

有时我们不只改变一个css效果的属性,而是想改变两个或者多个css属性的transition效果，那么我们只要把几个transition的声明串在一起，用逗号（“，”）隔开，然后各自可以有各自不同的延续时间和其时间的速率变换方式。但需要值得注意的一点：transition-delay与transition-duration的值都是时间，所以要区分它们在连写中的位置，一般浏览器会根据先后顺序决定，第一个可以解析为时间的怭值为transition-duration第二个为transition-delay。

```
  a {
    -moz-transition: background 0.5s ease-in,color 0.3s ease-out;
    -webkit-transition: background 0.5s ease-in,color 0.3s ease-out;
    -o-transition: background 0.5s ease-in,color 0.3s ease-out;
    transition: background 0.5s ease-in,color 0.3s ease-out;
  }
```
### 写法
```
//Mozilla内核
   -moz-transition ： [<'transition-property'> || <'transition-duration'> || <'transition-timing-function'> || <'transition-delay'> [, [<'transition-property'> || <'transition-duration'> || <'transition-timing-function'> || <'transition-delay'>]]* 
//Webkit内核
   -webkit-transition ： [<'transition-property'> || <'transition-duration'> || <'transition-timing-function'> || <'transition-delay'> [, [<'transition-property'> || <'transition-duration'> || <'transition-timing-function'> || <'transition-delay'>]]* 
//Opera
   -o-transition ： [<'transition-property'> || <'transition-duration'> || <'transition-timing-function'> || <'transition-delay'> [, [<'transition-property'> || <'transition-duration'> || <'transition-timing-function'> || <'transition-delay'>]]* 
//W3C 标准
   transition ： [<'transition-property'> || <'transition-duration'> || <'transition-timing-function'> || <'transition-delay'> [, [<'transition-property'> || <'transition-duration'> || <'transition-timing-function'> || <'transition-delay'>]]* 
```