---
title: gulp的入门和一些简单使用
date: 2017-03-02 10:51:41
categories: [gulp]
tags: [工程]
---

总结gulp的入门和一些简单使用，以便于快速上手。

<!--more-->

---

建议参考 [gulp详细入门教程-一点](http://www.ydcss.com/archives/18)

大概的过程为

1. 安装nodejs
2. 安装npm
3. 全局安装gulp
4. 新建package.json文件
5. 本地安装gulp插件
6. 新建gulpfile.js文件
7. 运行gulp

## 某些过程的详细介绍

### 全局安装gulp

命令行执行`npm install gulp -g`或者`cnpm install gulp -g`

查看是否正确安装：命令提示符执行`gulp -v`，出现版本号即为正确安装。

### 应不应该共用node_modules文件夹

共用node_modules有好处也有不便之处。npm的设计之初就不考虑共用node_modules的问题，所以如果硬要多个项目共用同一个node_modules会有许多不便之处。应该为每一个项目创建一个node_modules。

在提交项目的时候在.gitignore文件中设置不提交node_modules文件夹即可。

或者使用

```
rm -rf node_modules
```

PS：不要直接删除本地插件包

删除node_modules文件夹再提交项目，下载项目的时候用`npm install`就能下载回来在 package.json 中记录的插件。

### 安装参数--save-dev

当你为你的模块安装一个依赖模块时，正常情况下你得先安装他们（在模块根目录下`npm install module-name`），然后连同版本号手动将他们添加到模块配置文件package.json中的依赖里（`dependencies`）。

`-save`和`save-dev`可以省掉你手动修改package.json文件的步骤。
`spm install module-name -save` 自动把模块和版本号添加到dependencies部分
`spm install module-name -save-dve` 自动把模块和版本号添加到devdependencies部分

至于配置文件区分这俩部分， 是用于区别开发依赖模块和产品依赖模块， 以我见过的情况来看 `devDepandencies`主要是配置测试框架， 例如jshint、mocha。

>再做一个试验就懂得了区别：删除node_modules目录，然后执行 npm install --production，可以看到，npm只帮我们自动安装package.json中dependencies部分的模块；如果执行npm install ，则package.json中指定的dependencies和devDependencies都会被自动安装进来。

### 本地安装gulp插件

```
npm install gulp --save-dev
```

全局安装可以通过命令行在任何地方调用它，本地安装将安装在定位目录的node_modules文件夹下，通过require()调用

### 安装组件

[Gulp安装及配合组件构建前端开发一体化](http://www.dbpoo.com/getting-started-with-gulp/)

---

入门和进阶视频教程：

[ninghao.net](https://ninghao.net/video/2003)

一些比较细致介绍和问题的解决：

[gulp使用小结(一)](http://web.jobbole.com/86025/)

[[Gulp探究折腾之路(I)](http://jeffjade.com/2015/11/25/2015-11-25-toss-gulp/)](http://jeffjade.com/2015/11/25/2015-11-25-toss-gulp/)

