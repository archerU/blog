-----

title: React学习笔记

data: 2016-11-29

tags: React

-----

## React开发环境

根据一下文档安装，以及修改的用新网址。

[SUBLIME TEXT 3搭建REACT.JS开发环境](http://hao.jser.com/archive/8322/)

**配置SublimeText插件**

1.babel-sublime

>支持ES6， React.js, jsx代码高亮

2.JSX 代码审查，实时提示语法错误, 帮助快速定位错误点.
sublimelinter-jsxhint
,sublimelinter-eslint

jsx中如果用es6的语法，jsxhint不能检查出错误。因此要用es6写jsx需要额外配置。

* 安装sublimelinter 
* 安装sublimelinter-eslint
* sudo npm install eslint -g
* npm init -y
* sudo npm install react --save
* sudo eslint --init  

![eslint-init-js](eslint-init-js.png)

* sudo npm install eslint-plugin-promise --save

![eslint-init](eslint-init.png)

* 寻找node安装目录问题 ：打开控制台输入 which node ，得到的输出结果就是node安装路径。

* 成功后 View->Show Console 可以在控制台看见错误提示

[Linting React/JSX and ES6 Javascript with Eslint in Sublime Text 3](http://cheng.logdown.com/posts/2015/09/15/linting-react-jsx-and-es6-javascript-with-eslint)

[Sublime Text 中配置 ESLint](http://www.jianshu.com/p/e826e13c67ec)

>检查jsx语法

3.修改Emmet兼容jsx文件

4.JsFormat格式化js代码

5.编译jsx

[Sublime Text 之运行 ES6 (基于babel)](http://www.cnblogs.com/52cik/p/sublime-text-run-es6.html)

6.sublime-react支持react语法

[sublime-react](https://github.com/facebookarchive/sublime-react)