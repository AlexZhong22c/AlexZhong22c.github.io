---
title: @font-face--CSS3
date: 2017-01-25 21:50:09
categories: [CSS]
tags: [CSS3,font-face,字体,特殊]
---

@font-face是一个css命令，用来导入服务器端字体，将该字体文件存放到 web 服务器上，它会在需要时被自动下载到用户的计算机上。因此本地浏览器浏览网页时，不需要设置字体，就可以自动看到@font-face设置的任何字体。

如果你看到一些英文网站或blog看到一些很漂亮的自定义Web字体，比如说首页的Logo，Tags以及页面中的手写英文体，这些都是**@font-face**实现的。

<!--more-->

## @font-face在css中使用

```
@font-face {
　　font-family: <YourWebFontName>;
　　src: <source> [<format>][,<source> [<format>]]*;
　　[font-weight: <weight>];
　　[font-style: <style>];
}
```

取值说明：

1. YourWebFontName:你自定义的字体名称，最好是使用你下载的默认字体名（下载回来的叫什么字体，这里就填什么字体名），他将被引用到你的Web元素中的font-family。如“font-family:"YourWebFontName";”
2. source:此值指的是自定义的字体的存放路径，可以是相对路径也可以是绝路径；
3. format：此值指的是自定义的字体的格式，主要用来帮助浏览器识别，其值主要有以下几种类型：truetype,opentype,truetype-aat,embedded-opentype,avg等；
4. weight和style:这两个值大家一定很熟悉，weight定义字体是否为粗体，style主要定义字体样式，如斜体。

## 兼容浏览器

说到浏览器对@font-face的兼容问题，这里涉及到一个字体format的问题，因为不同的浏览器对字体格式支持是不一致的，这样大家有必要了解一下，各种版本的浏览器支持什么样的字体：

> **一、TureTpe(.ttf)格式：**
>
> .ttf字体是Windows和Mac的最常见的字体，是一种RAW格式，因此他不为网站优化,支持这种字体的浏览器有【IE9+,Firefox3.5+,Chrome4+,Safari3+,Opera10+,iOS Mobile Safari4.2+】；
>
> **二、OpenType(.otf)格式：**
>
> .otf字体被认为是一种原始的字体格式，其内置在TureType的基础上，所以也提供了更多的功能,支持这种字体的浏览器有【Firefox3.5+,Chrome4.0+,Safari3.1+,Opera10.0+,iOS Mobile Safari4.2+】；
>
> **三、Web Open Font Format(.woff)格式：**
>
> **.woff字体是Web字体中最佳格式**，他是一个开放的TrueType/OpenType的压缩版本，同时也支持元数据包的分离,支持这种字体的浏览器有【IE9+,Firefox3.5+,Chrome6+,Safari3.6+,Opera11.1+】；
>
> **四、Embedded Open Type(.eot)格式：**
>
> .eot字体是**IE专用字体**，可以从TrueType创建此格式字体,支持这种字体的浏览器有【IE4+】；
>
> **五、SVG(.svg)格式：**
>
> .svg字体是基于SVG字体渲染的一种格式,支持这种字体的浏览器有【Chrome4+,Safari3.1+,Opera10.0+,iOS Mobile Safari3.2+】。

**这就意味着在@font-face中我们至少需要.woff,.eot两种格式字体**，**甚至还需要.svg等字体达到更多种浏览版本的支持。**

------

为了使@font-face达到更多的浏览器支持，[Paul Irish](http://paulirish.com/)写了一个独特的@font-face语法叫[Bulletproof @font-face](http://paulirish.com/2009/bulletproof-font-face-implementation-syntax/):

```
  @font-face {
	font-family: 'YourWebFontName';
	src: url('YourWebFontName.eot?#iefix') format('eot');/*IE*/
	src:url('YourWebFontName.woff') format('woff'), url('YourWebFontName.ttf') format('truetype');/*non-IE*/
   }
```

但为了让各多的浏览器支持，你也可以写成：

```
  @font-face {
	font-family: 'YourWebFontName';
	src: url('YourWebFontName.eot'); /* IE9 Compat Modes */
	src: url('YourWebFontName.eot?#iefix') format('embedded-opentype'), /* IE6-IE8 */
             url('YourWebFontName.woff') format('woff'), /* Modern Browsers */
             url('YourWebFontName.ttf')  format('truetype'), /* Safari, Android, iOS */
             url('YourWebFontName.svg#YourWebFontName') format('svg'); /* Legacy iOS */
   }
```

直接改改``YourWebFontName``就行了。

然后就在CSS 里面引用给对应的元素：

```
p {
	font-family: 'YourWebFontName'
}
```

------

## 获取特殊字体

我平时都是到Google Web Fonts和Dafont.com寻找自己需要的字体，当然网上也还有别的下载字体的地方,如：[Webfonts](http://webfonts.fonts.com/),[Typekit](http://typekit.com/),[Kernest](http://kernest.com/),[Google Web Fonts](http://www.google.com/webfonts),[Kernest](http://kernest.com/licenses),[Dafont](http://www.dafont.com/),[Niec Web Type](http://nicewebtype.com/fonts/),不然你点[这里](http://www.google.com/search?q=webfonts)将有更多的免费字体。前面几个链接是帮助你获取一些优美的怪异的特殊字体!

### 获取@font-face所需字体格式：

特殊字体已经在你的电脑中了，现在我们需要想办法获得@font-face所需的.eot,.woff,.ttf,.svg字体格式。要获取这些字体格式，我们同样是需要第三方工具或者软件来实现，下面我给大家推荐一款我常用的一个工具[fontsquirrel](http://www.fontsquirrel.com/fontface/generator), 链接：[http://www.fontsquirrel.com/tools/webfont-generator](http://www.fontsquirrel.com/tools/webfont-generator)

使用这个在线字体格式生成工具，我们只需要上传我们下载回来的一种字体格式，就能生成其它的.eot,.woff,.ttf,.svg字体格式，很方便地说！这款工具的具体使用方法，可参考原文：

[http://www.cnblogs.com/rubylouvre/archive/2011/06/19/2084875.html](http://www.cnblogs.com/rubylouvre/archive/2011/06/19/2084875.html) ，本文也是转载该站 的内容 ，在此表示 感谢 ！

或者这个在线字体格式转换地址：https://cloudconvert.com/ 也是可以的，有其它比较实用方便的网址，欢迎留言提供，方便大家。

------

推荐给body写：

```
font-family: -apple-system-font,"Helvetica Neue","PingFang SC","Open Sans","Hiragino Sans GB","Microsoft YaHei","WenQuanYi Micro Hei",sans-serif;
```



