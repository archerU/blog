---
title: weui是如何通过gulp构建的
---

## 预备知识掌握

[npm模块管理器](http://javascript.ruanyifeng.com/nodejs/npm.html)

[Gulp入门指南](http://wiki.jikexueyuan.com/project/gulp-book/chapter7.html)

[gulp进阶构建项目由浅入深](http://www.cnblogs.com/tugenhua0707/p/5562548.html#_labe2_8)

[浏览器同步测试工具](http://www.browsersync.cn/)

[node 命令行框架 yargs](https://github.com/yargs/yargs)

## gulpfile.js 分析

[gulp API 文档](http://www.gulpjs.com.cn/docs/api/)

| gulp Api | 说明  |
| ----- 	| ---- |
| gulp.src(globs[,options]) | 读文件(个人理解) |
| gulp.dest(path[,options]) | 写文件(个人理解) |
| gulp.task(name[,deps],fn) | 定义任务 (个人理解) |
| gulp.watch(glob[,opts],tasks | 监控文件	 (个人理解) |

| gulp 插件	| 说明	|
| ------ |	----- |
| gulp-less |	 编译less |
| gulp-header | 给文本文件头部追加内容 |
| gulp-tap  | 	将 buffer 变为 stream (内存中的内容) |
| gulp-cssnano | css压缩 |
| [gulp-postcss](http://www.tuicool.com/articles/nIR3eqi) | PostCSS一种更优雅、更简单的书写CSS方式 |
| [gulp-autoprefixer](https://github.com/postcss/autoprefixer)	| autoprefixer 解析 CSS 文件并且添加浏览器前缀到CSS规则里 |
| gulp-rename		|	重命名文件流中的文件	|
| gulp-sourcemaps	|	js压缩前和压缩后比较 |


| node模块	 | 说明 |
|	---- | ---- |
| [npm](http://javascript.ruanyifeng.com/nodejs/npm.html)	| 模块管理器 |
| [gulp](http://www.gulpjs.com.cn/) | node gulp模块 	|
| path | node path模块	|
| fs 	| node 文件操作模块fs(File System) |
| [yargs](https://github.com/yargs/yargs) | node 命令行框架 yargs |
| [browser-sync](http://www.browsersync.cn/) | 浏览器同步测试工具	|

## gulpfile.js 解析

> 源码 1～18 引入文件

``` js
var path = require('path');
var fs = require('fs');
var yargs = require('yargs').argv;
var gulp = require('gulp');
var less = require('gulp-less');
var header = require('gulp-header');
var tap = require('gulp-tap');
var nano = require('gulp-cssnano');
var postcss = require('gulp-postcss');
var autoprefixer = require('autoprefixer');
var rename = require('gulp-rename');
var sourcemaps = require('gulp-sourcemaps');
var browserSync = require('browser-sync');
var pkg = require('./package.json');

var option = {base: 'src'};
var dist = __dirname + '/dist';
```

> 源码 19～46 针对样式weui.less的编译，增加头，压缩，重命名

``` js
gulp.task('build:style', function (){
    var banner = [
        '/*!',
        ' * WeUI v<%= pkg.version %> (<%= pkg.homepage %>)',
        ' * Copyright <%= new Date().getFullYear() %> Tencent, Inc.',
        ' * Licensed under the <%= pkg.license %> license',
        ' */',
        ''].join('\n');	
    gulp.src('src/style/weui.less', option)
        .pipe(sourcemaps.init())
        .pipe(less().on('error', function (e) {
            console.error(e.message);
            this.emit('end');
        }))
        .pipe(postcss([autoprefixer(['iOS >= 7', 'Android >= 4.1'])]))
        .pipe(header(banner, { pkg : pkg } ))
        .pipe(sourcemaps.write())
        .pipe(gulp.dest(dist))
        .pipe(browserSync.reload({stream: true}))
        .pipe(nano({
            zindex: false,
            autoprefixer: false
        }))
        .pipe(rename(function (path) {
            path.basename += '.min';
        }))
        .pipe(gulp.dest(dist));
});

```
> * .pipe(sourcemaps.init())
>  .pipe(sourcemaps.write()) 是js压缩前和压缩后的比较，所以包裹着整个压缩过程
> * .pipe(less().on('error', function (e) {console.error(e.message);this.emit('end');})) 编译less       
> * .pipe(postcss([autoprefixer(['iOS >= 7', 'Android >= 4.1'])])) 加上自动的浏览器私有前缀
> * .pipe(header(banner, { pkg : pkg } )) 往文件头部追加的内容为banner数组中的内容
> * .pipe(gulp.dest(dist)) 写出,到这里整个编译流程算是结束了。
> * .pipe(browserSync.reload({stream: true}))
> * .pipe(nano({zindex: false,autoprefixer: false})) 压缩css
> * .pipe(rename(function (path) {path.basename += '.min';}))  压缩后的css加上min
> * .pipe(gulp.dest(dist)) 写出，到这里整个编译less，压缩css流程结束        

> 源码：48～52 将src/example中的文件拷贝到dist下

```js
gulp.task('build:example:assets', function (){
    gulp.src('src/example/**/*.?(png|jpg|gif|js)', option)
        .pipe(gulp.dest(dist))
        .pipe(browserSync.reload({stream: true}));
});
```
> 源码：54～67 examples.less文件编译，压缩

```js
gulp.task('build:example:style', function (){
    gulp.src('src/example/example.less', option)
        .pipe(less().on('error', function (e){
            console.error(e.message);
            this.emit('end');
        }))
        .pipe(postcss([autoprefixer(['iOS >= 7', 'Android >= 4.1'])]))
        .pipe(nano({
            zindex: false,
            autoprefixer: false
        }))
        .pipe(gulp.dest(dist))
        .pipe(browserSync.reload({stream: true}));
});
```

> 源码：69～84 html

```js
gulp.task('build:example:html', function (){
    gulp.src('src/example/index.html', option)
        .pipe(tap(function (file){
            var dir = path.dirname(file.path);
            var contents = file.contents.toString();
            contents = contents.replace(/<link\s+rel="import"\s+href="(.*)">/gi, function (match, $1){
                var filename = path.join(dir, $1);
                var id = path.basename(filename, '.html');
                var content = fs.readFileSync(filename, 'utf-8');
                return '<script type="text/html" id="tpl_'+ id +'">\n'+ content +'\n</script>';
            });
            file.contents = new Buffer(contents);
        }))
        .pipe(gulp.dest(dist))
        .pipe(browserSync.reload({stream: true}));
});
```
> 源码：86～95 监控各文件变化

```js
gulp.task('build:example', ['build:example:assets', 'build:example:style', 'build:example:html']);

gulp.task('release', ['build:style', 'build:example']);

gulp.task('watch', ['release'], function () {
    gulp.watch('src/style/**/*', ['build:style']);
    gulp.watch('src/example/example.less', ['build:example:style']);
    gulp.watch('src/example/**/*.?(png|jpg|gif|js)', ['build:example:assets']);
    gulp.watch('src/**/*.html', ['build:example:html']);
});
```
> 源码：97～112 启动浏览器同步测试工具

```js
gulp.task('server', function () {    
    yargs.p = yargs.p || 8080;
    browserSync.init({
        server: {
            baseDir: "./dist"
        },
        ui: {
            port: yargs.p + 1,
            weinre: {
                port: yargs.p + 2
            }
        },
        port: yargs.p,
        startPath: '/example'
    });
});
```

> 源码：114～126 用命令行快速启动

```js
// 参数说明
//  -w: 实时监听
//  -s: 启动服务器
//  -p: 服务器启动端口，默认8080
gulp.task('default', ['release'], function () {            
    if (yargs.s) {
        gulp.start('server');
    }

    if (yargs.w) {
        gulp.start('watch');
    }
});
```




