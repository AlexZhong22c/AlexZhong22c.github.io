---
title: 内容分类--谈谈H5标签
date: 2017-01-25 21:38:38
categories: [HTML]
tags: [H5]
---

对内容作了调整，方便自己理解，详情请参考MDN：

https://developer.mozilla.org/zh-CN/docs/Web/Guide/HTML/Content_categories

每一个HTML元素都必须遵循定义了它可以包含哪一类内容的规则。

以下是三种类型的内容分类：

<!--more-->

- 主内容类，描述了很多元素共享的内容规范；
- 表单相关的内容类，描述了表单相关元素共有的内容规范；
- 特殊内容类，描述了仅仅在某些特殊元素上才需要遵守的内容规范，通常这些元素都有特殊的上下文关系。

![Content_categories_venn](http://olqa2s510.bkt.clouddn.com/Content_categories_venn.png)

## 元数据内容模型

此类元素 修改文档其余部分的陈述或者行为，建立与其他文档的链接，或者传达其他外带信息。

 属于这一类的元素有：link 、meta、noscript、script、style、title等等 

## 分节内容模型

在当前的大纲中创建一个[分节](https://developer.mozilla.org/en-US/docs/Sections_and_Outlines_of_an_HTML5_document)，此分节将定义[`header`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/header)元素、[`footer`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/footer) 元素和标题元素（[heading content](https://developer.mozilla.org/zh-CN/docs/Web/Guide/HTML/Content_categories#Heading_content)）的范围。

### article元素

`<article>`元素表示文档、页面、应用或网站中的**独立结构**，其意在成为**可独立分配的或可复用的结构**，如在发布中，它可能是论坛帖子、杂志或新闻文章、博客、用户提交的评论、交互式组件，或者其他独立的内容项目。

用时要特别注意内容的独立性：一般独立完整的内容才使用article元素，如果只是一段内容的话应该是用section元素。

> 使用说明：
>
> - 当`<article>`元素嵌套使用时，则该元素代表与外层元素有关的文章。例如，代表博客评论的`<article>`元素可嵌套在代表博客文章的`<article>`元素中。
> - `<article>`元素的作者信息可通过[``](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/address)元素提供，但是不适用于嵌套的`<article>`元素。
> - `<article>`元素的发布日期和时间可通过[``](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/time)元素的`pubdate`属性表示。

### section元素

- 用于定义文章中的章节(通常应该有标题和段落内容)


- 用来定义文档中特定的内容区块，可视为一个区域分组元素。


- 用一句话来概括它的作用就是：给内容分段，给页面分区


- 注意它与div的区别，div强调在形式上的独立性，section强调的是内容上的独立性，注意它的语义。

> article和section对比：
>
> 1\. 语义不同：
>
> - article元素是独立完整的内容，section元素页面内容分块
>
> 2\. 相同点：
>
> 本质上都是带有语义的div块元素 　　　　
>
> 分别可以看做`<div id="section">`和`<div id="article">`

### aside元素

- aside元素通常用来设置侧边栏
- 用于定义article元素之外的内容，前提是这些内容与article元素内的内容相关。
- 同时也可嵌套在article元素内部使用，作为主要内容的附属信息。比如与内容有关的参考资料，名词解释等。

### nav元素

- 用来定义目录、导航栏
- 并非所有的超链接都放在nav元素中，通常只把一个文档中的主导航栏放在nav中。

## 标题内容模型

定义了分节的标题，而这个分节可能由一个明确的分节内容元素直接标记，也可能由标题本身隐式地定义。

属于此分类的元素有：h1到h6和 [`hground`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/hgroup)

> 注意：尽管[`header`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/header)可能包含一些标题内容，但[`header`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/header)并不是标题内容本身。

## 表单相关内容模型

拥有表单父节点（exposed by a **form** attribute）的元素。

一个表单父节点可以是form元素，也可以是其id在表单属性中被指定了的元素。

## 其他比较常用的元素

### header元素

`<header>`元素表示一组引导性的帮助，可能包含标题元素，也可以包含其他元素，像logo、分节头部、搜索表单等。

### footer元素

**HTML `<footer> `元素**表示最近一个[章节内容](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/Sections_and_Outlines_of_an_HTML5_document#Defining_Sections_in_HTML5)或者[根节点](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/Sections_and_Outlines_of_an_HTML5_document#Sectioning_root)（sectioning root ）元素的页脚。一个页脚通常包含该章节作者、版权数据或者与文档相关的链接等信息。

> - `<footer>`元素内的作者信息应包含在[``](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/address) 元素中。
> - `<footer>`元素不是章节内容，因此在[outline](https://developer.mozilla.org/en-US/docs/Sections_and_Outlines_of_an_HTML5_document)中不能包含新的章节。

------

### time元素

- time元素代表24小时中的某个时刻或某个日期，表示时刻允许出现时差。它可以定义很多格式的日期和时间
  - datetime属性。代表中日期和时间之间要用“T”文字分隔，“T”表示时间，请注意倒数第二行，时间加上Z文字表示给机器编码时使用UTC标准时间，表示向机器编码另一地区时间，如果是编码本地时间，则不需要添加时差。
  - pubdate属性是个可选标签。加上它搜索引擎/浏览器就可以很方便的识别出那个日期是文章、新闻的发表日期。

```
<time datetime="2015-10-22">2015年10月12日</time>
<time datetime="2015-10-22T20:00">2015年10月12日晚上8点</time>
<time datetime="2015-10-22T20:00Z">2015年10月12日晚上8点</time>
<time datetime="2015-10-22T20:00+09:00">美国时间2015年10月12日8点</time>
```

### address元素

- 通常用来说明作者的联系信息，例如名字、E-mail、电话、地址等。
- address元素中的内容会以斜体显示。

------

### figure元素

figure元素是一个媒体组合元素，也就是对其他的媒体元素进行组合，比如：图像、图标等等。

### figcaptio元素

用来给figure元素定义标题。

### video元素

- src属性：音频地址
- loop属性：是否重复播放
- autoplay属性：是否自动播放
- controls属性：添加控制
- poster属性：在视频加载完成前显示什么
- 当然这个元素对于个别浏览器会有些隐性的小问题