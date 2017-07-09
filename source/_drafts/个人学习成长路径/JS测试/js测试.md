------
title: JS单元测试&接口测试&e2e测试
	
data: 2016-11-2
	
tags: JS测试

------

#### 知识查找
[所有的测试框架](https://www.awesomes.cn/repos/Applications/testings?page=2&)
>[所有的测试框架](https://www.awesomes.cn/repos/Applications/testings?page=2&)很棒很棒的网址，有一定理念以后就可以直接从这里看官方文档，不用看其它的乱七八糟的博客和网站了。

[mocha](http://www.ruanyifeng.com/blog/2015/12/a-mocha-tutorial-of-examples.html)

[几款前端测试断言库(Assertions lib)的选型总结](http://blog.lvscar.info/post/tech/assertions_lib/)

[js单元测试断言框架chaijs](http://www.shaynegui.com/javascript-unit-test-chaijs/)

[JavaScript测试工具之Karma-Jasmine的安装和使用详解](http://www.jb51.net/article/75815.htm)

[jasmine/jasmine-npm****](https://github.com/jasmine/jasmine-npm)

#### 测试管理工具(karma)
> Karma是一个基于Node.js的JavaScript测试执行过程管理工具（Test Runner）

#### 测试框架
> 所谓"测试框架"，就是运行测试的工具。
> 类似的测试框架还有Jasmine、Tape等

```js
describe('加法函数的测试套件', function() {
  it('1 加 1 应该等于 2 的测试用例', function() {
    expect(add(1, 1)).to.be.equal(2);	//断言
  });
});
```

#### 断言库
> 所谓"断言库"，就是断定：输入预想内容后，输出的结果是不是和自己的预想结果一致。
> 类似的断言库有chai,assert

```js
expect(4 + 5).to.be.equal(9);
```

## JS单元测试（函数测试）

[karma](http://blog.fens.me/nodejs-karma-jasmine/) + [jasmine](http://blog.fens.me/nodejs-jasmine-bdd/) + [phantomJS](http://www.codesec.net/view/206245.html)

> [jasmine](http://blog.fens.me/nodejs-jasmine-bdd/)
> 这个网址解释了为什么jasmine要配合karma和phantomJs。karma提供了jasmine自动执行的环境，phantomJS是一个基于webkit的javascript API,基于webkit浏览器做的事情，它都能做到。phantomJS就相当于是一个无界面的浏览器。

> jasmine默认自带断言库,断言库语法跟chai不同。

chai的断言：

	expect(add(1, 1)).to.be.equal(2);	//断言

jasmine的断言

	expect(add(1, 1)).toEqual(2);	//断言

```js

describe('加法函数的测试套件', function() {
  it('1 加 1 应该等于 2 的测试用例', function() {
    expect(add(1, 1)).toEqual.equal(2);	//断言
  });
});

```

1.安装Karma + Jasmine

Karma、Jasmine、jasmine-core 这三个要全局安装。

```bash	
sudo npm install karma -g 
sudo npm install jasmine -g
sudo npm install jasmine-core -g	
```
2.安装插件

karma-chrome-launcher 用于启动谷歌浏览器。

karma-jasmine 用于启动jasmine。

```bash
sudo npm install karma-chrome-launcher --save-dev
sudo npm install karma-jasmine --save-dev
```
3.启动karma 测试是否安装成功

启动项目后效果：自动启动浏览器，并且控制台有输出，表明karma安装成功。

```bash
	karma start
```
![karma_install_success_chrome](karma_install_success_chrome.png)
![karma_install_success_bash](karma_install_success_bash.png)
4.配置karma.config.js

karma.config.js配置文件的参数，详细看下面的文章 

[手把手教你如何安装和使用Karma-Jasmine](http://www.tuicool.com/articles/aemI7b6)

5.启动karma 测试karma单元测试是否成功

单元测试失败

![karma_start_error](karma_start_error.png)

单元测试成功

![karma_start_success](karma_start_success.png)

6.phantomJS进行优化

每个测试用例都需要打开一个浏览器，非常麻烦。因此用一个无界面的浏览器代替。

phantomjs 无界面的浏览器

karma-phantomjs-launcher 用于启动无界面浏览器

```bash
sudo npm install phantomjs --save-dev
sudo npm install karma-phantomjs-launcher --save-dev
```
7.karma+jasmine+phantomjs 启动

单元测试失败

单元测试成功

8.总结

> karma、jasmine、jasmine-core、phantomjs karma-phantomjs-launcher需要安装全局。jasmine和phantomjs都是被karma调用的，估计着应该是调用了其中的命令，所以要安装在全局。

> karma-jasmine、karma-chrome-launcher 安装在开发目录中。karma-chrome-launcher像这样带launcher的应该是谷歌浏览器的驱动，没有这个，打不开浏览器，看不见启动karma就出现浏览器自动弹出的情景。

package.json

> 这里面安装了其它多余的依赖，如果按照上面安装的，启动karma start 可以启动并且测试成功。但是如果用npm的script脚本启动，npm test那么就会报错。因此如下多余依赖是为了能用npm的script脚本启动karma。有一些即使全局配置了，在package里面也要写是为了能够更清晰的展示依赖项，毕竟你扔给别人的时候，别人未必配置了全局。那么最佳实践可以为，dependencies里面的写全局配置项。devdependencies里面的写局部配置项。

![karma_jasmine_package](karma_jasmine_package.png)

9.开发套路

* 1.先搜索下有没有全局安装，karma、jasmine、jasmine-core、phantomjs,karma-phantomjs-launcher没装的装上。

```	bash
sudo npm install karma jasmine jasmine-core phantomjs -g  
```

* 2.建立package.json,npm init大家都懂的。不过都开始写测试了，这个应该早就装了。那么就是安装，karma-jasmine、karma-phantomjs-launcher

```bash
sudo npm install karma-jasmine karma-phantomjs-launcher --save-dev
```

* 3.建test文件夹，最好建在根目录下，一眼就看见有个测试的文件夹了。建各种 xxx.spec.js的单元测试文件。通常测试脚本与所要测试的源码脚本同名，但是后缀名为.test.js（表示测试）或者.spec.js（表示规格）。

* 4.简单写好一个测试文件后，配置karma.config.js

* 5.之后就是运行karma start,看测试文件是否正确。然后擦擦擦写完所有的测试，运行，搞定。


## JS接口测试

[mocha](http://mochajs.org) + supertest + chai

[带你入门带你飞Ⅱ 使用Mocha + Chai + SuperTest测试Restful API in node.js](http://www.tuicool.com/articles/juA7zie)

>mocha chai supertest 都是基于node。

>mocha 适合做异步测试，为什么这么说，官网： making asynchronous testing simple and fun.

>supertest是一个轻量级 HTTP AJAX 请求库。

>chai是断言库。

```js
describe('定义一个Service的测试套件',function(){
	it('输出Hello World的测试用例',function(done){
		request
			.get("/")
			.expect(200)
			.expect('Hello World',done);
	});
});	
```

1.安装mocha

原理是一样的，需要在dos界面里敲命令行，都安装全局。

```bash
sudo npm install mocha -g
```
其它不需要敲命令行的就可以安装在开发目录中

```bash
sudo npm install supertest --save-dev
sudp npm install chai --save-dev
```

2.建test文件夹，在下面建测试文件。

示例基于koa

![mocha_warning1](mocha_warning1.png)
![mocha_warning2](mocha_warning2.png)

3.mocha启动测试文件

需要手动启动

```bash
mocha app.spec.js
```

## JS端对端测试

> 也叫e2e测试，用户真实性测试

>selenium-webdriver 基于node。

1.安装selenium-webdriver + chromedriver驱动

```
sudo npm install selenium-webdriver --save-dev
```


```js
var webdriver = require('selenium-webdriver'),
    By = webdriver.By,
    until = webdriver.until;

var driver = new webdriver.Builder()
    .forBrowser('chrome')
    .build();

driver.get('http://www.baidu.com/');
driver.findElement(By.id('kw')).sendKeys('hehe');
driver.findElement(By.id('su')).click();
driver.wait(until.titleIs('hehe_百度搜索'), 1000);
driver.quit();

```

2.node启动e2e测试文件

```
node e2e.js
```


> 如果浏览器指定chrome,注意下载 chrome-driver 32x或者64x。 博主的mac是64x,装了32x报错，就改成64x吧。



## Q&A

1.安装phantomjs

![phantomjs_error](phantomjs_error.png)

>解决方案：全局安装 karma-phantomjs-launcher
	
	sudo npm install karma-phantomjs-launcher -g


## 参考
[phantomjs官网](http://phantomjs.org/)



