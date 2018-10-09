---
title: NodeJs、gulp
date: 2018-08-29 11:58:34
tags: NodeJs gulp
---

# scripts #
- package.json中存在scripts（通过初始化得来的模块清单才有）
- test，start二者为关键任务名 可以不使用npm run xxx（可以直接使用npm test/start）
- scripts的存在可以直接执行指定代码（或者为较长代码去一个别名）
- 通过npm init（生成package.json）-》下载所需模块-》在package.json的scripts中添加a:node+js文件（当在cmd命令中输入npm run a时，就将执行对应的js文件）

# 操作本地文件 #
- nodejs可以操作用户电脑（本地）中的文件
- readFile("路径"，function(err,data){if(err) return      console.log(data.toString())})(xxx.toString()->正常显示文本)

# nodejsmodule.js #
- nodejs遵循commonjs模块化规范
- 模块分为三种
  1.  原生模块->var 变量名=require("原生模块名")  //不需要提前安装
  2.  第三方模块-》先安装对应模块，如果没有安装，则会报错
      1.  Cannot find module "模块名"  只要安装即可解决
      2.  有时候报的模块名很奇怪，安装过对应包后，有提示另一个包错误，**可删除node_modules，重新npm install即可**（重新安装对应模块）
  3.  自定义模块（任何值都可以被当做模块导出）
      1. module.exports=值，如果使用module.exports导出，则接收时，得到的变量就是对应值
      2. exports.xx=xx,如果使用exports导出，则接收到的变量是exports对象的一个副本，对象中包含了xxx，module.exports可以模拟exports
  4.  **自定义模块可以将需要使用的变量封装成模块输出，应用的时候不会造成代码的冗杂**

# Gulp （将前端一些重复的、机械化的、简单的操作，自动执行）（基于nodejs）#
1.  全局安装，只需安装一次即可
  1.  创建项目目录
  2.  初始化目录
  3.  安装gulp本地安装
  4.  在项目根目录创建gulpfile.js
2.  gulp命令
  1.  gulp（直接执行默认default任务）
  2.  gulp 任务名，执行对应的任务
  3.  **任务的声明于fulpfile.js中完成**
3.  api接口
  -  gulp.task("任务名"，function（）{}) 》当执行gulp 任务名 》执行该命令时，会自动执行对应的任务中所写的function中的代码
  -  **gulp.tast("任务名"，["其他任务名1","其他任务名2"]，function（）{})** 》 执行对应任务时，先执行其他任务（任务1——》任务2——》当前任务）（如果要按照顺序执行任务，首先要把顺序前边的任务实现（否则报错））
  -  **gulp.src("路径")** 将原料获取并放入生产线（将要操作的文件）
  -  .pipe(功能) 下载插件并在中间使用即可（置于gulp.src之后，.pipe(gulp.dest("输出路径"))之前）
  -  .pipe(gulp.dest("输出路径"))（将处理完成后的文件输出到指定路径下）
  -  监听文件
    -  gulp.watch("路径"，[任务名])-》尽量将watch单独放在一个任务中，命名规范——》watch：任务名
    -  gulp.task("watch:需要监听的任务名"，["先执行的任务"]，function(){gulp.watch("路径"，[执行的任务])})---》（将watch单独放在一个任务中，在执行监听任务之前先执行对应的监听文件-》然后设置监听-》当被监听文件修改后-》执行对应文件）
4.  完整流程
  1.  gulp.task("任务名",["任务名1"，"任务名2"],function(){gulp.src("路径")  .pipe(功能操作1)  .pipe(功能操作2)   .pipe(功能操作3)  .pipe(功能操作n)   .pipe(gulp.dest("输出到指定路径"))})

5.  **所需插件可根据功能网上自行百度-》下载插件-》安装-》引入-》根据api文档使用即可**
6.  已知插件及其功能
  1.  gulp-autoprefixer(自动添加前缀以兼容浏览器)-+-gulp-sourcemaps(根据源文件生成对应添加前缀后的文件，使浏览器报错等显示源文件行号（便于修改）（存在监听时，会在修改后自动执行相关流程）)   [https://www.npmjs.com/package/gulp-autoprefixer](https://www.npmjs.com/package/gulp-autoprefixer "自动添加前缀")
  2.  gulp-babel（es6 装 es5）  [https://www.npmjs.com/package/gulp-babel](https://www.npmjs.com/package/gulp-babel "es6 转 es5")
  3.  sourcemaps（编写内联源映射）[https://www.npmjs.com/package/gulp-sourcemaps](https://www.npmjs.com/package/gulp-sourcemaps "内联源映射")
  4.  gulp-zip（压缩文件。zip）[https://www.npmjs.com/package/gulp-zip](https://www.npmjs.com/package/gulp-zip "压缩文件.zip")
  5.  css/* **/* *->css/星号 星号/星号（css文件下所有文件下的所有文件）
  6.  gulp-htmlmin (压缩html代码)[https://www.npmjs.com/package/gulp-htmlmin](https://www.npmjs.com/package/gulp-htmlmin "压缩html代码")
  7.  gulp-uglify (压缩js代码) [https://www.npmjs.com/package/gulp-uglify](https://www.npmjs.com/package/gulp-uglify "压缩js代码")
  8.  gulp-Sass (压缩css代码) [https://www.npmjs.com/package/gulp-sass](https://www.npmjs.com/package/gulp-sass "压缩css代码")
  9.  gulp-imagemin (压缩图片) [https://www.npmjs.com/package/gulp-imagemin](https://www.npmjs.com/package/gulp-imagemin "压缩图片")
  10.  Browsersync (浏览器同步测试工具) [http://www.browsersync.cn/](http://www.browsersync.cn/ "浏览器同步测试工具")
  11.  gulp-clean-css （压缩css） [https://www.npmjs.com/package/gulp-clean-css](https://www.npmjs.com/package/gulp-clean-css "压缩css")
  12.  pump(泵，分支) [https://www.npmjs.com/package/pump](https://www.npmjs.com/package/pump "pump(泵，分支)")
  13.  Browsersync + Gulp.js [http://www.browsersync.cn/docs/gulp/](http://www.browsersync.cn/docs/gulp/ "监听修改刷新服务器")
  14. [Gulp中文网](https://www.gulpjs.com.cn/ "Gulp")

# 注 #
- •JavaScript没有模块系统。没有原生的支持密闭作用域或依赖管理。
- •JavaScript没有标准库。除了一些核心库外，没有文件系统的API，没有IO流API等。
- •JavaScript没有标准接口。没有如Web Server或者数据库的统一接口。
- •JavaScript没有包管理系统。不能自动加载和安装依赖。
- 于是便有了CommonJS（http://www.commonjs.org）规范的出现，其目标是为了构建JavaScript在包括Web服务器，桌面，命令行工具，及浏览器方面的生态系统。
- CommonJS制定了解决这些问题的一些规范，而Node.js就是这些规范的一种实现。Node.js自身实现了require方法作为其引入模块的方法，同时NPM也基于CommonJS定义的包规范，实现了依赖管理和模块自动安装等功能。


# 判断代码是否执行完毕 #
- 当代码执行完毕后将自动跳转至当前路径等待下一步操作
- ctrl+c ctrl+c  连续两次跳出当前环境



# VSCode插件 #
## Node Exec ##

- f8 用nodejs执行代码