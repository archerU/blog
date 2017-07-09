---
 title: node入门
 
 data: 2016-10-10
 
 tags: Node
 
---
## Node管理工具(n)
n是Node的一个模块，作者是TJ Holowaychuk（鼎鼎大名的Express框架作者）

```bash
$ sudo npm install -g n
```
>安装完成之后，直接输入n后输出当前已经安装的node版本以及正在使用的版本（前面有一个o），你可以通过移动上下方向键来选择要使用的版本，最后按回车生效。

```bash
$ n
    0.10.1 
    0.10.15 
o   0.10.21 
    0.11.8
```

如果你要安装其他的版本（比如0.11.12），那么如下:

```bash
$ n 0.11.12
install : 0.11.12
   mkdir : /usr/local/n/versions/0.11.12
   fetch : http://nodejs.org/dist/v0.11.12/node-v0.11.12-darwin-x64.tar.gz
####                                                     5.9%
```

1.安装最新的版本

```bash
$ sudo n latest
```
2.安装稳定版本

```bash
$ sudo n stable
```
3.删除某个版本

```
$ sudo n rm 0.10.1 
```
4.以指定的版本来执行脚本

```
$ n use 0.10.21 some.js
```
