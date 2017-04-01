---
title: 闭合浮动和BFC
date: 2017-04-01 22:24:37
categories: [CSS]
tags: [清除浮动,BFC,伪元素]
---

本文参考 [那些年我们一起清除过的浮动](http://www.iyunlu.com/view/css-xhtml/55.html) ，但是 一丝冰凉 的这篇文章有很多地方我都不认同，取其精华去其糟粕，所以本文并没有包含那些我所不认同的内容。

<!--more-->

## 区分 清除浮动 和 闭合浮动

- 清除浮动：清除对应的英文单词是 clear，对应CSS中的属性是 clear：left | right | both | none；
- 闭合浮动：更确切的含义是使浮动元素闭合，从而减少浮动带来的影响。

两者的区别 [请看Demo](http://www.iyunlu.com/demo/enclosing-float-and-clearing-float/index.html)

闭合浮动主要用来解决**因为子元素浮动导致父元素高度塌陷**的问题。

## 闭合浮动的一些老方法：

1. 在子元素们的最后追加一个`style="clear:both"`的空标签，这个不好
2. 在子元素们的最后追加一个br标签，使用br标签的`clear="all | left | right | none"` 属性，因为一般不建议在HTML中使用br，这个也不好
3. 通过设置父元素overflow值设置为hidden；在IE6中还需要触发 hasLayout ，例如 zoom：1；因为最终还是有补不了的bug被大家弃用
4. 通过设置父元素overflow值设置为auto，同样也有bug
5. 父元素也设置浮动，缺点是**使得与父元素相邻的元素的布局会受到影响**，不可能一直浮动到body，不推荐使用
6. 父元素设置display:table，盒模型属性已经改变，由此造成的一系列问题，得不偿失，不推荐使用。文章最后还会再介绍到给伪元素设置display:table。

### 7\. 使用`：after`伪元素

> 需要注意的是 :after是伪元素，不是伪类（某些CSS手册里面称之为“伪对象”，不太对）。

由于IE6-7不支持:after，使用 zoom:1触发 hasLayout。

- 优点：浏览器支持好，不容易出现怪问题（目前：大型网站都有使用，如：腾迅，网易，新浪等等）
- 缺点：复用方式不当会造成代码量增加
- 建议：定义公共类，以减少CSS代码

### 不要使用方案3和4

方案3、4通过overflow闭合浮动，实际上已经创建了新的 块级格式化上下文，这将导致其布局和相对于浮动的行为等发生一系列的变化，闭合浮动只不过是一系列变化中的一个作用而已。所以为了闭合浮动去改变全局特性，这是不明智的，带来的风险就是一系列的bug，比如firefox 早期版本产生 focus，截断绝对定位的层等等。始终要明白，如果单单只是需要闭合浮动，overflow就不要使用，而不是某些文章所说的“慎用”。

### 父级div定义height的方法

- 父级div定义height，这样就**不必闭合浮动**了
- 不推荐使用，只建议高度固定的布局时使用

## 小结

通过对比，我们不难发现，其实以上列举的方法，无非有两类：

其一，通过在浮动元素的末尾添加一个空的元素

其二，通过设置父元素 overflow 或者display：table 属性来闭合浮动，原理就是BFC，下面探讨一下：

## BFC知识

[Block formatting contexts ](http://www.w3.org/TR/CSS21/visuren.html#block-formatting)（块级格式化上下文），以下简称 BFC。在CSS3里面改动后称之为flow root。

### BFC的特性

一丝冰凉 对于BFC的特征的解释非常模糊，甚至不正确。我认为她这部分内容所解释的现象只适用到IE7

通俗地来说就是：

- 创建了 BFC的元素就是一个独立的盒子，里面的子元素不会在布局上影响外面的元素，反过来外面的元素也不影响里面的元素
- 同时BFC仍然属于文档中的普通流

### 如何触发BFC

- float 除了none以外的值 
- overflow 除了visible 以外的值（hidden，auto，scroll ） 
- display (table-cell，table-caption，inline-block) 
- position（absolute，fixed） 
- fieldset元素

> 需要注意的是，display:table 本身并不会创建BFC，但是它会产生匿名框(anonymous boxes)，而匿名框中的display:table-cell可以创建新的BFC，换句话说，触发块级格式化上下文的是匿名框，而不是display:table。所以通过display:table和display:table-cell创建的BFC效果是不一样的。
>
>  fieldset 元素在www.w3.org里目前没有任何有关这个触发行为的信息，直到HTML5标准里才出现。有些浏览器bugs（Webkit，Mozilla）提到过这个触发行为，但是没有任何官方声明。实际上，即使fieldset在大多数的浏览器上都能创建新的块级格式化上下文，开发者也不应该把这当做是理所当然的。CSS 2.1没有定义哪种属性适用于表单控件，也没有定义如何使用CSS来给它们添加样式。用户代理可能会给这些属性应用CSS属性，建议开发者们把这种支持当做实验性质的，更高版本的CSS可能会进一步规范这个。

**由于浏览器的差异：**

- 在支持BFC的浏览器（IE8+，firefox，chrome，safari）通过创建新的BFC闭合浮动；
- 在不支持 BFC的浏览器 （IE6-7），通过触发 hasLayout 闭合浮动。IE6-7的hasLayout 可以等同于 BFC。

## 闭合浮动的精益求精

上面已经列举了7种闭合浮动的方法，通过第三节分析的原理，我们发现其实更多的：display：table-cell，display：inline-block等只要触发了BFC的属性值都可以闭合浮动。从各个方面比较，**方案7**：after伪元素闭合浮动无疑是相对比较好的解决方案了，下面详细说说该方法：

```
.clearfix:after {content:"."; display:block; height:0; visibility:hidden; clear:both; }
.clearfix { *zoom:1; }
```

1) display:block 使生成的元素以块级元素显示,占满剩余空间;

2) height:0 避免生成内容破坏原有布局的高度。

3) visibility:hidden 使生成的内容不可见，并允许可能被生成内容盖住的内容可以进行点击和交互;

4）通过 content:"."生成内容作为最后一个元素

**通过分析发现，除了clear：both用来闭合浮动的，其他代码无非都是为了隐藏掉content生成的内容，这也就是其他版本的闭合浮动为什么会有font-size：0，line-height：0。**

**更重要的是，我认为这个方法根本就没产生 BFC 。**

> 不建议将content设置为空字符串""，在firefox 7里面会看到它会产生空隙

### 创新方案：零宽度空格

相对于空标签闭合浮动的方法代码似乎还是有些冗余，通过查询发现Unicode字符里有一个“零宽度空格”，也就是[U+200B ](http://www.fileformat.info/info/unicode/char/200b/index.htm)，这个字符本身是不可见的，所以我们完全可以省略掉 visibility:hidden了

```
.clearfix:after {content:"200B"; display:block; height:0; clear:both; }
.clearfix { *zoom:1; }
```

在实际开发中，由于存在Unicode字符不适合内嵌CSS的GB2312编码的页面，使用方案7完全可以解决我们的需求了。