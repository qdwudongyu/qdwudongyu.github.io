---
title: Vue-cli
date: 2018-08-29 11:58:34
tags: Vue
---

# CLI
- 命令行工具
  - Vue 提供了一个官方的 CLI，为单页面应用快速搭建 (SPA) 繁杂的脚手架。它为现代前端工作流提供了 batteries-included 的构建设置。只需要几分钟的时间就可以运行起来并带有热重载、保存时 lint 校验，以及生产环境可用的构建版本。更多详情可查阅 [Vue CLI 的文档](https://cli.vuejs.org/)。
  - 安装步骤
    - cnpm install -g vue-cli--(全局安装vue-cli)
    - vue init list name path--(初始化 vue init list（模板类型-通过vue-list查看） name（项目名） path（不写，默认为当前路径）)
    - `vue init webpack `
  - 创建
    - ? Project name  输入项目名称

    - ? Project description 输入项目描述

    - ? Author 作者

    - ? Vue build 打包方式，回车就好了

    - ? Install vue-router?  选择  Y 使用 vue-router，输入 N 不使用

    - ? Use ESLint to lint your code? 代码规范，推荐 N

    - ? Setup unit tests with Karma + Mocha? 单元测试，推荐 N

    - ? Setup e2e tests with Nightwatch? E2E测试，N
  - 运行
    - 进入对应文件，路径
    - cnpm install--（安装所需组件）
    - npm start/npm run dev
  - 编写
    - sc--快捷生成template script style结构
  - 插件
    - Vetur
