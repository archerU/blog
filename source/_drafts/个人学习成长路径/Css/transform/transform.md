---
title: transform(转换)
---

[W3C官网－英文文档阅读最佳](https://www.w3.org)

## 快捷属性

| 属性 | 描述 |
| --- | --- |
| transform | 向元素应用 2D 或 3D 转换 |
| transform-origin | 允许你改变被转换元素的基点 |
| transform-style | 规定被嵌套元素如何在 3D 空间中显示 |
| perspective | 规定 3D 元素的透视效果 |
| perspective-origin | 规定 3D 元素的底部位置 |
| backface-visibility | 定义元素在不面对屏幕时是否可见 |

>transform ： none | <'transform-function'> [ <'transform-function'> ]* 

>transform: rotate | scale | skew | translate | matrix;

## 属性详解
#### [大漠整理transform](http://www.w3cplus.com/content/css3-transform)
### 1.rotate(旋转)

```
rotate(<angle>)
```
>angle是指旋转角度(deg)，正数－－顺时针旋转，负数－－逆时针旋转。基点默认为元素 中心点

### 2.translate(变形)

```
translate(x,y)
translate(<translation-value>[, <translation-value>])
translateX(<translation-value>)
translateY(<translation-value>)
```
>translate(x,y) 负数－－反方向移动物体，其基点默认为元素 中心点，也可以根据transform-origin进行改变基点。

>通过矢量[tx, ty]指定一个2D translation，tx 是第一个过渡值参数，ty 是第二个过渡值参数选项。如果 未被提供，则ty以 0 作为其值

### 3.scale(缩放)

```
scale(<number>[, <number>])
scaleX(<number>)
scaleY(<number>)
```
>其中心点就是元素的中心位置，缩放基数为1，大于1元素就放大；小于1，元素缩小

>提供执行[sx,sy]缩放矢量的两个参数指定一个2D scale（2D缩放）。如果第二个参数未提供，则取与第一个参数一样的值。

### 4.skew(扭曲)

```
skew(<angle> [, <angle>])
skewX(<angle>)
skewY(<angle>)
```
>其中第二个参数是可选参数，如果没有设置第二个参数，那么Y轴为0deg。同样是以元素中心为基点。

### 5.matrix(矩阵)

```
matrix(<number>, <number>, <number>, <number>, <number>, <number>) 
```

### 1.transform-origin(原点)
```
transform-origin(X,Y)
```
>默认点是元素的中心点。其中X和Y的值可以是百分值,em,px。

| 原点 | 原点 | 原点 | 原点 |
| --- | --- | --- | --- |
| center | 50% | center | 50% |
| top | 0% | left | 0% |
| bottom | 100% | right | 100% |







