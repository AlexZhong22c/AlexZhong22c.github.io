---
title: yelee主题改bug总结
date: 2017-02-22 23:06:34
categories: [hexo]
tags: [hexo,yelee,theme]
---

从找一个喜欢的hexo主题到修改好bug发布到博客上面，整个过程花了我不少时间，下面是对这个改bug过程中发现的小问题做的总结。

此文无图。

<!--more-->

---

一开始我是在知乎上面找好看的主题，找了很长一段时间才找到一个我比较喜欢的主题，并且挑选了一个已经被大神们优化得不错的主题来借鉴借鉴。

我的hexo主题其实就是直接Fork了[ngudream](http://ngudream.com/2017/01/24/n-hexo-blog/)的主题，只不过该大神日常比较忙碌，我自己琢磨了一下代码，把一些报错的小bug给修复了，暂时还没有为这个主题添加什么特殊的功能。（原因是这个主题在各位大神的努力下，功能已经非常齐全炫酷了。）

直接参考ngudream的这篇文章就可以了，在此在此表示一万个感谢：

http://ngudream.com/2017/01/24/n-hexo-blog/

在这个过程中我发现了一些小问题：

## 左右搜索栏

一定要先根据这个来安装插件：

[Yilia主题添加本地站内搜索-高明飞](http://gaomf.cn/2016/10/10/为Hexo博客Yilia主题添加本地站内搜索功能/)

### 找不到content.json

- 这是因为左下角搜索栏找不到content.json


- 将`yelee\source`文件夹下的search文件夹剪切到 根目录的source文件夹里面
- 生成一次页面
- 再把刚刚的search文件夹剪切回`yelee\source`文件夹下即可

---

### cb-search.json 404 (Not Found)

- 是因为没有安装右下角搜索栏插件


- 如果安装插件之后语法报错，就把别人项目的文件代码复制过来就行了，省得去检查语法

---

### 百度分享因为混合内容报错

如果因为混合内容报错（即https网站引用了http的资源），你可以将百度分享的地址改为：`https://github.com/hrwhisper/baiduShare`；本来我想把static文件夹放在外面一点的，但是有bug，我现在只是做到不报错而已，具体的百度分享内容都没弄

---

### 百度站长要重新配置

- 查阅相关资料，依照资料放baidu_verify_QshFoK3ZRz.html在yelee的source文件夹下通过站长验证，放googleeff62ed1566e185e.html也是同理。

百度sitemap要另外安装：

```
npm install hexo-generator-baidu-sitemap --save 
```

- 如果想要给谷歌提交网站，只需要在[Search Console](https://www.google.com/webmasters/tools/home?hl=zh-CN)验证网站，并提交站点地图就可以了。谷歌真的好简单啊！谷歌的`sitemap.xml`不需要写到配置文件中，自动生效。
  - 有个问题是，Github禁止百度爬虫，所以提交的sitemap迟早会显示失败，成功几率非常小

---

## 温馨提示

- 多说也是会因为混合内容而报错，但是我只能改良，不能彻底解决这个问题
  - 将多说的`embed.js`本地化，	将这个文件的地址改动到`duoshuo.ejs`和`click2show.ejs `和layout的`after-footer.ejs`文件里面，但是依然报错
  - 见到http就给它加s
- 在Markdown文章头部的标注信息的冒号后面要加一个空格，这是语法要求


- 在hexo s调试下，百度站长push报错属于正常现象
- 在hexo s调试下，文章导航的特效会失灵，属于正常现象


- 发现大神每篇文章文件的名字都是英文，Markdown里面的标题才是中英随意的，不然isPost()函数会出错
  - 用cmd创文件名的时候英文全小写，空格用-表示，为了风格统一
- 插件这种东西最好不要复制，所以**在重新搭建博客的时候**我没有直接复制node_modules文件夹，这也容易令人忽略了大神自己在这个文件夹下改良的index.js和search.ejs文件

---

## 请不要Fork我的主题

去Fork大神ngudream的主题就可以了，因为我的个人改动比较私人化，所以Fork之后别人可能会看不懂。另外我的主题作了几个不好的改动：

- 为了避免报错，一开始我把一些if语句的判断条件直接改为false，原本它们的判断条件是xxx.on的


- 还有一个feed属性没研究，应该是订阅博客的功能，好像也被我粗暴地关了
- 报错`Cannot GET /plugins/css/special.css`，我直接把“字往下掉”动画关掉
- 然后就是折腾在显示主页时标签栏出现的undefined，一开始我不知道那个把三项文字的标签转为二项的js文件，所以一直研究ejs代码都没弄好。后来我直接给主页加一个英文名字blog就算了。总算不出现undefined
- 乱关乱开了一下博文最下方的分享栏，不知道会不会出问题，这个模块应该是百度分享
- 点击微信之后，那个左右滑动的栏目我暂时改不了代码，本来我想去掉qq的，但是只好把qq的二维码弄上
  - 还有就是去掉qq之后，点击微信，上面那个圆形地方就没有图案显示
- 发现search-result-list模块的文字被顶到后面
  - 把.col-3的CSS的marginbottom改为4px就行了

### 我没有完善的内容

- 代码压缩没搞
- 公益404没搞
- 右下角搜索栏搞了，但是利用的不是打分排名
- 谷歌分析到现在也不会，所以先不用，应该和百度站长是差不多的，没心思搞
- 好像就只有360浏览器看不到emoji表情，所以即便安装了插件，文章尽量不要用emoji

------

## 整个过程的心得

- 在这过程中学会了用HTML-beautify来美化sublime中的html代码排版
- 对ejs的代码写法有所了解
- 明白了代码中的partial是干嘛的
- 第一次发现一些私人的代码改动都是写在`after-footer.ejs`里面
- 发现dos的报错信息还是有点用的
- 令我困惑的是填yml文件中的url项，后来发现用来填绑定的域名，域名要自己出钱买
- 一开始遇到` Cannot read property 'on' of undefined`不会调，后来发现是yml文件填得不好，可能是不符合语法，导致错误。再比如yml文件中代码没有在适当的地方空空格。
- 如果在网上打开js文件发现中文变乱码，在谷歌浏览器打开查看就可以了，这是最不消耗脑力的办法