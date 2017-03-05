---
title: 桌面端和移动端图标的引入
date: 2017-02-27 17:28:51
categories: [HTML]
tags: [图标,meta标签,link标签]
---

> 本文翻译自[All About Favicons-bitsofcode](https://bitsofco.de/all-about-favicons-and-touch-icons/) ：

这星期我决定找到一些合适的方式来使用网站的favicon（另外还包括移动端的touch icon）。我想总结一下我自己的观点并且通过简明的语言来表述清楚：

<!--more-->

## 一些基础的知识

 favicon 是浏览器展示web网页时用到的一种图片。最典型的就是16x16像素大小，不过现在通常需要更多更大的尺寸以供不同的用途使用：

- 地址栏
- 链接栏
- 书签
- 标签
- 桌面图标

如果没有指明favicon的位置，所有主流的浏览器（甚至包括IE5时代的浏览器）都会默认去网站根目录找一个叫"favicon.ico"的文件。从技术层面来讲，这意味着我们不需要用作任何声明就能在网站中使用图标。

然而，这种情况下图标的格式需要受到限制。另外还不支持带透明的图标，这并不是一个最优的办法。因为现在我们能使用更多格式的图标：[png](http://caniuse.com/#feat=link-icon-png), gif, jpeg，在某些情况下还有[svg](http://caniuse.com/#feat=link-icon-svg) 。

## favicon声明和link标签

你可以用link标签设置你喜欢的图标：

```JavaScript
<link rel="" type="" sizes="" href="">  
```

### rel属性

用于声明链接目标和html文档的关系。通常用来引入css样式表。如果是图标，比较官方的写法应该是：

```JavaScript
<link rel="icon">
```

曾经你可能见过这种写法：

```JavaScript
 <link rel="shortcut icon">
```

这是因为某些老浏览器（IE8或者更早）需要这么写，否则浏览器会忽略这整个link标签。因此，即便`rel="shortcut icon"`不在HTML5标准里面，它依然在现代浏览器中有效。然而后面我们会讲到，在实际中你可能只需要使用`<link rel="icon">` 这一种写法即可。

### type属性

用来	指定链接目标的[MIME type format](http://www.iana.org/assignments/media-types/media-types.xhtml#image)。比如，指定一个图标文件是`image/x-icon` 类型还一个png文件 `image/png`。

根据W3C，指定type类型仅仅只是一个建议。但除此之外，IE9和IE10需要指定type属性。在这些版本的浏览器里面，虽然不必指定`rel="shortcut icon"`，作为替代，它们需要指定媒体文件的type为 `image/x-icon` 。

幸运的是，IE11和其他现代浏览器不需要指定媒体文件的type。

### sizes属性

 用于声明特定被链接的文件的大小，不同大小用于不同用途。你能为每种用途提供各自最优的文件。这对使用png图片的情景尤为重要，因为png是不能拓展的。这是一张很好的[备忘单](https://github.com/audreyr/favicon-cheat-sheet),它会告诉你应该使用的文件的大小和用途。

### href属性

不必多说，这是用来指定图标的位置和地址的。

## 做个小结

| Browser        | Link “rel”/ “type”                       | Accepted Formats                         |
| -------------- | ---------------------------------------- | ---------------------------------------- |
| IE 8 and below | link rel=”shortcut icon”                 | ico                                      |
| IE 9, IE 10    | link rel=”icon” type=”image/x-icon” or link rel=”shortcut icon” | ico                                      |
| IE 11          | link rel=”icon”                          | ico, png, gif                            |
| Chrome         | link rel=”icon”                          | ico, png, gif                            |
| Firefox        | link rel=”icon”                          | ico, png, gif, [svg*](http://caniuse.com/#feat=link-icon-svg) |
| Safari         | link rel=”icon”                          | ico, png, gif                            |
| Opera          | link rel=”icon”                          | ico, png, gif                            |

看上去，最好的方案应该是声明两个版本，用现代浏览器的方法引用png，IE8的方法引用ico文件。

然而，如果ico和png同时被引用，现代浏览器会不论标签顺序的先后，只选择ico。这意味着，如果我们要兼容老浏览器，现代浏览器可能会被提供一个错误的图片文件的格式。

### 当只引入ico时

```html
<link rel="icon" href="favicon.ico" type="image/x-icon" />
<link rel="shortcut icon" href="favicon.ico" type="image/x-icon" />
```

### 当需要引入ico和png

最佳的方案应该是**只声明引入png，让老浏览器使用默认的方式引入ico**，这样最稳妥。(但实际上，把ico文件放在根目录时，某些现代浏览器可能并不会引入它)

```JavaScript
<!-- For IE 10 and below -->  
<!--  No link, just place a file called favicon.ico in the root directory -->

<!-- For IE 11, Chrome, Firefox, Safari, Opera -->  
<link rel="icon" href="path/to/favicon-16.png" sizes="16x16" type="image/png">  
<link rel="icon" href="path/to/favicon-32.png" sizes="32x32" type="image/png">  
<link rel="icon" href="path/to/favicon-48.png" sizes="48x48" type="image/png">  
<link rel="icon" href="path/to/favicon-62.png" sizes="62x62" type="image/png">  
```

## 移动设备的touch Icon

一些移动设备允许用户自定义浏览器主页书签。像原生app图标一样，在这种情景下，我们应该提供专门的图标。

怎么指定这个图标由浏览器/移动设备决定：

| Device / Browser    | Link “rel”                               | Sizes                                    |
| ------------------- | ---------------------------------------- | ---------------------------------------- |
| Apple / Safari      | link rel=”apple-touch-icon” or link rel=”apple-touch-icon-precomposed” | 76x76 - iPad 2 and iPad mini ;120x120 - iPhone 4s, 5, 6 ;152x152 - iPad (retina) ;180x180 - iPhone 6 Plus |
| Apple / Opera Coast | link rel=”icon” ([Will also accept Safari and Windows formats](https://dev.opera.com/articles/opera-coast/)) | 228x228                                  |
| Android / Chrome    | link rel=”icon” ([Will, for a limited time, also accept Safari format](https://developer.chrome.com/multidevice/android/installtohomescreen)) | 192x192                                  |

对于Windows，这些图标应该用meta标签指定。

For Windows 8 / IE 10 -

```html
<meta name="msapplication-TileImage" content="pinned-tile.png">  
<meta name="msapplication-TileColor" content="#009900">  
```

For Windows 8.1 / IE 11 -

```html
<!-- In <head> -->  
<meta name="msapplication-config" content="ieconfig.xml" />

<!--  In ieconfig.xml -->  
<?xml version="1.0" encoding="utf-8"?>  
<browserconfig>  
  <msapplication>
    <tile>
      <square70x70logo src="images/smalltile.png"/>
      <square150x150logo src="images/mediumtile.png"/>
      <wide310x150logo src="images/widetile.png"/>
      <square310x310logo src="images/largetile.png"/>
      <TileColor>#009900</TileColor>
    </tile>
  </msapplication>
</browserconfig>  
```

就是这样，用到 favicon的地方还挺多的。如果是一个很基础的网站，我可能只会使用ico图标	。期待 SVG favicon 时代的到来。

另可参考：https://github.com/audreyr/favicon-cheat-sheet