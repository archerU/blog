---
title: sublime3
tags: 使用指南

---

# 替换图标
[Sublime Text 2 入门及技巧](http://lucifr.com/2011/08/31/sublime-text-2-tricks-and-tips/) Lucifr 推荐了 Nate Beaty 的一个用于替换的图标 

[更多 Sublime Text 2 替换图标](http://lucifr.com/2012/01/14/more-sublime-text-2-replacement-icons/)

更多图标下载 [图标设计网址](https://dribbble.com)

# 插件安装

1.打开sublime text3后按快捷键control+`后下面会出来东西，然后输入如下命令

```bash
import urllib.request,os; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); open(os.path.join(ipp, pf), 'wb').write(urllib.request.urlopen( 'http://sublime.wbond.net/' + pf.replace(' ','%20')).read())

```

2.快捷键command+shift+p后会出来列表，找到Package Control:Install Package。呆一会会出来插件列表，这个地方搜索你要找的插件名称。

# Emmet (前身为 Zen Coding) 

* 快速编写html／css神器

# JSDoc插件	(自动生成注释模版)

```bash
/** 然后按下回车 JSDoc会根据函数定义生成注释模版
```

* Command + shift + p
* 输入 install package
* 输入 DocBlockr 

# JSFormat	(格式化代码)

```bash
	Control + alt + f 
```

# SideBarEnhancements (侧边栏按目录显示)

```bash
	Command + k + b
```