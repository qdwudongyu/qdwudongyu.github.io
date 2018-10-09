---
title: hexo-博客搭建及主题
date: 2018-08-29 11:58:34
tags: hexo 
---


##
git克隆github项目 

[简单使用git和github来管理代码----配置与使用](https://www.cnblogs.com/nelson-hu/p/6395770.html
) 
##  hexo
- 前提
  - Node.js
  - Git
- 安装
  - cnpm install -g hexo-cli
  - hexo init blog  ----初始化blog文件夹
  - cd blog         ----进入新建的blog文件夹
  - cnpm install
  - hexo server
- 配置
  - _config.yml
    - 大部分配置信息，您可以在此配置大部分的参数。
  - package.json
    - 应用程序的信息EJS、Stylus和Markdown renderer默认安装
  - scaffolds
    - 模板文件夹新建文章时，Hexo 会根据 scaffold 来建立文件。
    - Hexo的模板是指在新建的markdown文件中默认填充的内容。例如，如果您修改scaffold/post.md中的Front-matter内容，那么每次新建一篇文章时都会包含这个修改。
  - source--资源文件夹，除_posts文件夹外，开头命名为_（下划线的文件） / 文件夹和隐藏的文件将会被忽略。Markdown 和 HTML 文件会被解析并放到 public 文件夹，而其他文件会被拷贝过去。
  - themes
    - 主题 文件夹。Hexo 会根据主题来生成静态页面。
- 命令
  - hexo g   
    - 生成静态页面
  - hexo s
    - 启动本地服务，进行文章的预览调试
    - 成功启动本地服务，浏览器输入：http://localhost:4000 查看
- 文档
  - [HEXO文档](https://hexo.io/zh-cn/)
  - [码云(gitee.com)帮助文档](http://git.mydoc.io/?t=154714)
  - [Hexo+OSChina+git静态blog博客网站教程](https://my.oschina.net/ruowu/blog/1492038)
  - [github-help](https://help.github.com/categories/github-pages-basics/)
- [使用Hexo+Github一步步搭建属于自己的博客（基础）](https://www.cnblogs.com/fengxiongZz/p/7707219.html)
- SSH秘钥
  - C:\Users\Administrator\.ssh--默认存储路径
- 主题
  - [BlueLake](http://chaoo.oschina.io/2016/12/29/BlueLake%E5%8D%9A%E5%AE%A2%E4%B8%BB%E9%A2%98%E7%9A%84%E8%AF%A6%E7%BB%86%E9%85%8D%E7%BD%AE.html)


- 转移hexo文件
  - cnpm install-重新下载相关组件
  - npm install hexo-deployer-git --save