----
title: 初试微信小程序

date: 2016-10-24 11:35 

tags: 微信

----

## 创建项目
根据官网 [简易教程](https://mp.weixin.qq.com/debug/wxadoc/dev/?t=1476197491244) 创建一个项目。
>项目目录选择的本地文件夹是个空文件夹,则会生成一个简单的 demo



## Q&A
1.找不到所要替换的文件

> 问题原因：开发工具版本不正确，老版本不支持

>解决方案：确保下载的程序版本在0.9.092100以上

2.Failed to load resource: net::ERR_NAME_NOT_RESOLVED (http://1709827360.appservice.open.weixin.qq.com/appservice)

>问题原因：通常是由于系统设置了代理如Shadowsocks等。

>解决方案：关闭代理，或者依次点击工具栏“动作”-"设置"，选择“不使用任何代理，勾选后直连网络”。

3.修复asdebug.js报错

>问题原因：TypeError: Cannot read property 'MaxRequestConcurrent' of undefined

>解决方案：替换 /Resources/app.nw/app/dist/weapp/appservice/asdebug.js

4.扫码登录失败

>问题原因：please bind your wechat account to the appid first

>解决方案：先使用0.7版本的进行扫码登陆，登陆成功后，再用0.9的版本打开就直接进入了。
0.7版本地址：http://dldir1.qq.com/WechatWebDev/release/0.7.0/wechat_web_devtools_0.7.0.dmg
