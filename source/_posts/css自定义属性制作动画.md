-----

title: 自定义属性定义动画
data: 2017-7-7 08:20

-----

# 自定义属性定义动画

## css 自定义属性

CSS自定义属性最早称之为CSS变量，更官方一点的称谓是[CSS自定义属性级联变量](https://drafts.csswg.org/css-variables/)

#### css 变量

> 变量，是标识符和可以用任何常规值替代值之间的关联，使用var()函数表示法：var(- example-variable)返回--example-variable的值 。

#### 自定义属性

> 自定义属性，这是表单的特殊属性 --* 这里*表示变量名称。这些用于定义给定变量的值：--example-variable：20px; 是一个CSS声明，使用自定义 --*属性将CSS变量--example-variable的值设置为20px。


## 自定义属性使用方法

声明一个变量

 ```css
 :root { 
 	--primary-color: green; 
 }
 ```
 
 在需要使用的地方通过var()函数来调用
 
 ```css
 body {
 	background-color: var(--primary-color);
 }
 ```
 
## css 制作动画
 
- css 变量

```css
:root { 
--mouse-x: 0.1;
--mouse-y: 0.1; 
--rotate: 0.1; 
}
```

- 使用css变量，通过var()来调用

```css
.mustache { 
	... 
	left: var(--mouse-x); 
}
```

- css变量结合calc计算公式

```css
.mustache { 
... 
left: calc(1000px * var(--mouse-x)); 
}
```

- 我们可以借助 `setProperty() `方法重置`:root{}`中声明的变量

```css
function sway(xPos, yPos) { 
let wh = window.innerHeight / 2, 
ww = window.innerWidth / 2; 
document.body.style.setProperty("--mouse-x", (xPos - ww) / 25+"deg"); }
document.addEventListener("mousemove", function(e) { sway(e.clientX,e.clientY); })
```

通过 `mousemove`事件，改变了`--mouse-x`的值。这里需要特别注意了，我们给`--mouse-x`传了一个默认值`(xPos - ww) / 25+"deg"`。

实例：

[小胡子](https://codepen.io/airen/full/QpWNWz/)

## 关于兼容性



## 参考

[动画](https://img.w3ctech.com/slide/cssconf-wentin.pdf)

[cssicon](https://cssicon.space/#/icon/search)

[css的隐藏绘画功能和交互动画技巧](https://img.w3ctech.com/slide/cssconf-wentin.pdf)

[CSS自定义属性制作动画](https://www.w3cplus.com/css3/create-animation-with-css-variables.html)