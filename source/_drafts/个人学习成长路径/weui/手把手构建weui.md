---
title: 手把手搭建weui

---

WeUI 是由微信官方设计团队专为微信移动 Web 应用设计的 UI 库

## 安装

安装之前需要先安装gulp

博主是mac电脑的重度使用者，以下以mac电脑安装为例

### 1.安装gulp

```bash
sudo npm install gulp -g

```

### 2.下载weui

```bash
git clone https://github.com/weui/weui.git

```

### 3.安装本地gulp和gulp插件

```bash
cd weui
npm install

```

### 4.运行weui

```
gulp -ws
```

> 运行gulp -ws命令，会监听src目录下所有文件的变更，并且默认会在8080端口启动服务器，然后在浏览器打开 http://localhost:8080/example。

### 手机预览

![](http://ww2.sinaimg.cn/mw690/997884acgw1f6wignzkcuj207s07s0si.jpg)

[weui网页链接](http://weui.github.io/weui/)