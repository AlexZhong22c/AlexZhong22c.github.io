---
title: 搭建hexo博客个人总结
date: 2017-02-22 17:29:25
categories: [hexo]
tags: [hexo,心得,教程]
---

因为大神们在这个方面的文献已经很多了，所以我觉得我没有必要再写一个教程了。关于教程，可以推荐[sylujia的hexo搭建教程](http://blog.csdn.net/itjia_0203/article/details/52504837)来看看，写得很详细而且思路也很好，但是我记得这个教程有一两点步骤不太妥当，如果完全按照教程来搞会报错，但如果自身有一点基本知识的话，这点问题真的算不上是问题。

<!--more-->

我是按照[sylujia的hexo搭建教程](http://blog.csdn.net/itjia_0203/article/details/52504837)来搭建的，发现这个教程有几个不周全的地方。

## 这个教程的不周全之处

### 不周之处一

没有直接介绍如何在github仓库创建hexo分支，这个部分可以参考这段代码：

```
1.  在github上创建仓库，仓库名为your-user-name.github.io
2.  本地创建两个分支：master 与 hexo：
先让gitbash去到your-user-name.github.io文件夹，再输入以下命令
    touch README.md
    git init
    git add README.md
    git commit -m "first commit"
    git remote add origin https://github.com/your-user-name/your-user-name.github.io.git
    git push -u origin master

    在本地新建一个分支： 
        git branch hexo
    切换到你的新分支: 
        git checkout hexo
    将新分支发布在github上： 
        git push origin hexo
    至此分支创建完毕
3.  在github网站上的仓库设置hexo为默认分支
```

对于这段代码的解释可以参考原文[冷星1024的hexo搭建教程](http://www.cnblogs.com/ld1024/p/5913169.html) 。这一步应该在git与github建立联系之后，在安装hexo之前完成。

### 不周之处二

看到这一步：

在项目文件夹下执行以下命令：

```
$ git init #初始化为一个git目录
$ git remote add origin git@github.com:sylujia/sylujia.github.io.git #使用你自己的地址关联
$ git pull #pull一下你的远端库
```

执行之后命令行的位置应该是**不在**hexo分支下的，如果按照教程继续执行`$ git checkout hexo`应该会面临失败，而用`git clean  -d  -fx ""`来解决问题会删掉本地的文件这也是万万不可的。

比较合适的一个做法应该是改进它的下一步为：

```
$ git add . #添加所有文件到暂存区
$ git commit -m "提交信息"     #提交到本地仓库
$ git push -f origin hexo  #把本地库强制push到远端库的hexo分支
```

接着往下做就行了，一直到教程的**优化与部署**环节。不建议小白看**优化与部署**及之后的内容，只不过是把之前的内容重新过一遍而已，最后那段内容甚至可能涉及抄袭，有点敷衍，不看就行了。

## 原始文件和部署文件分离

选用这个教程的好处就是为了在搭建之后能很方便地备份和还原博客。其原理就是将原始文件和部署文件分离上传到仓库。这是这个教程没有明确说明的一个点。

在搭建好hexo博客之后，应该要按照以下过程管理博客：

### 日常修改

在本地对博客进行修改(添加新博文、修改样式等等)后，

1\. 先执行hexo clean(这是为了减少上传的原始文件的大小，也可以忽略这步，那么速度也会快一点点)

2.依次执行

```
git add .
git commit -m "..."
git push origin hexo
```

指令将改动 推送到github(此时当前分支应为hexo)

3\. 执行`hexo g -d`发布网站到master分支上。

### 如果本地资料丢失，之前所做的备份就能实现还原

重装电脑或者想在其他电脑上修改博客，可以使用下列步骤：

```
使用
git clone git@github.com:sylujia/sylujia.github.io.git
拷贝仓库（默认分支为hexo）
在本地新拷贝的sylujia.github.io文件夹下通过Git bash依次执行下列指令：
npm install hexo、npm install、npm install hexo-deployer-git
（注意：不需要hexo init这条指令）
```

## 理解过程和解决bug可能会用到的知识点

### Git与GitHub区别

理解Git与GitHub是两个不同的概念，这有利于理解搭建hexo博客的过程，万一报错了自己也能解决。

git是一个[版本控制](http://lib.csdn.net/base/git)的工具，而github有点类似于远程仓库，用于存放用git管理的各种项目。自行进一步理解git能够对搭建hexo博客的过程有理性的认识。

关于git的一些基本操作的含义可以看这里：[个人常用命令add,commit以及push-黄杉](http://blog.csdn.net/mchdba/article/details/12083965?utm_source=tuicool&utm_medium=referral)

### .gitignore文件

.gitignore顾名思义就是告诉git需要忽略的文件，这是一个很重要并且很实用的文件。

一般我们写完代码后会执行编译、调试等操作，这期间会产生很多中间文件和可执行文件，这些都不是代码文件，是不需要git来管理的。

我们在git status的时候会看到很多这样的文件，如果用git add -A来添加的话会把他们都加进去，而手动一个个添加的话也太麻烦了。

这时我们就需要.gitignore了。

### 强制push

如果`git push origin master`不行的话，是因为**检测到远程的仓库和你本地仓库里面的文件各不相同**所以不允许commit。

这时候你可以选择使用`git push -f origin master`强制地push，硬将你的内容推到github仓库上。

### 遇到不能切换分支问题

在本地切换分支的命令是`git checkout hexo`

如果报错说不能换分支，

使用`git clean  -d  -fx ""`把以前的git记录清除掉就行了，

但是这也会删掉本地的文件，不要乱用。

## hexo搭建过程咨询服务

以上文章内容已经提供了充足的资源来供一个小白自学如何搭建并且有能力自助解决搭建过程中出现的问题。但是我相信如果不亲自折腾一下hexo的话，是不会了解到其中的一些基本的原理，是不可能理解上述内容的，所以搭建过程是相当困难的。

如果按照一个比较完整的教程，**10小时**学会搭建一个hexo博客不是难事。

但是如果不懂得任何原理，按照教程来搭建，万一遇到报错或者问题会消耗大量的时间，我就是一个例子，经历了搭建好了一个hexo博客--换主题--修改主题的一些bug--重新搭建一个结构良好的hexo博客，我花了将近**两个星期**的时间。

在这两个星期的时间里面，因为遇到了一些有问题的教程，本来想请教大神，但总遭到大神们以忙为理由委婉拒绝，我只好花了大量时间来试错和研究和理解整个流程和原理。

可见，**选对教程**、**理解原理**能大大减少自我摸索过程中的痛苦。

一次偶然的机会，我收取了一个网友50元，在他整个搭建过程中向他提供问题咨询，包学包会。结果发现他在整个过程中能免除很多痛苦，而且节省了他大量的时间。两个星期的问题能够在三四天时间内轻松解决，其实这50元还真的挺值。

后来我陆续接了几单咨询来做，通过这个互利的过程，我对咨询和解决方案行业的态度发生的巨大的改观。我个人也欢迎联系付费咨询的合作！

## 本文补充

之前讲到的几个博文链接地址我都已经放上了，另外还有一篇原创的不错的文章，地址挂了，我把全文截图放在这里，可以右键另存为来看：

![](http://olqa2s510.bkt.clouddn.com/CrazyMilk-%20blog.png)

