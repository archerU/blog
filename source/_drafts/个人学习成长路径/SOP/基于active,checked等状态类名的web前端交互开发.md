---
title: 基于active,checked等状态类名的前端交互
data: 2016-11-14
tags: sop

---

## 前言

1. 此文是基于张鑫旭同学的[基于active,checked等状态类名的web前端交互开发](http://www.zhangxinxu.com/wordpress/2016/10/classname-active-checked-web-ux-develop/)，名字就不想换了，也想不出更好的什么鬼。

2. boostrap里面也有此设计：bootstrap的状态样式


## 准则
**.active .checked等JS交互类名自身绝对不能有CSS样式**

## 适用场景
**1.**

![图片](table-active.png)

**2.配合相邻兄弟元素选择器＋**

## 不适用场景


## 常用状态类名

状态类名的命名和应用场景可以和伪类相同。

* active
* disabled
* checked
* selected
* on
* in
* out
* open