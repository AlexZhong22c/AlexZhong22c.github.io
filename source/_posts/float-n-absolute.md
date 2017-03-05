---
title: float和绝对定位比较
date: 2017-03-04 10:58:27
categories: [CSS]
tags: [float,绝对定位]
---

因为float实现的效果和绝对定位比较类似，稍后会对它们进行比较。

<!--more-->

## float

- 在浮动一张图片或者其他元素时，是在要求浏览器把它往上方推，直到它碰到父元素的内边界。
- 浮动非图片元素时，要给它设定宽度。
- 默认情况下浮动元素的位置一般要受到父元素位置的限制，而且改变浮动元素在html文档中的次序，有可能会影响float的实现效果。

## position

- static 静态定位，每个元素都处于常规文档流中
- relative 相对的是它原来在文档流中的位置（或者默认位置） 。
  - 这个元素原来占据的空间没有动，其他元素也没动。
  - top right bottom left(可以给top left属性设定负值，把元素向上向左移动)
- absolute 绝对定位会把元素彻底从文档流中拿出来，再相对其他元素定位。
- fixed 固定定位元素的定位上下文是视口，因此它不会随页面滚动而移动。

## float和绝对定位比较

我最常见的一个问题就是在一些布局中不知道用float好还是用绝对定位好，因为他们有一些相似的作用。

float 的诞生本来就是为了让文字环绕图片。

`position: absolute`会导致元素脱离文档流，被定位的元素等于在文档中不占据任何位置，在另一个层呈现，可以设置z-index。PS的图层效果就是position: absolute。

float也会导致元素脱离文档流，但还在文档或容器中占据位置(不会跑到父元素的外面去)，把文档流和其它float元素向左或向右挤，并可能导致换行。图片的文字环绕布局效果就是float：

```html
<p>
This is some text. This is some text. This is some text.
This is some text. This is some text. This is some text.
This is some text. This is some text. This is some text.
This is some text. This is some text. This is some text.
<img src="/i/eg_cute.gif" />
This is some text. This is some text. This is some text.
This is some text. This is some text. This is some text.
This is some text. This is some text. This is some text.
This is some text. This is some text. This is some text.
This is some text. This is some text. This is some text.
This is some text. This is some text. This is some text.
</p>
```

CSS：

```css
img 
{
float:right
}
```

## left 和 top属性

float和绝对定位可以一起用在同一个元素，但是效果不好。
**left和top等属性应该用于position的定位，**但是我经常见到有些老手也会把它们用到float的元素上，这就很尴尬地滥用了，一般情况下这是因为对基础知识掌握不牢固所导致的。

## 用到float的三栏布局所带来的启发

需要说明的是，浮动布局依然遵循常规文档流，所以与绝对定位相比，浮动定位时HTML源文件中元素声明的位置显得格外重要。所以，在用到float实现的三栏布局中，交换左栏和右栏的声明次序会有很大影响，也有方法不用交换各栏的次序也可以实现同样的布局，但是，这就要用到一种比较晦涩的使用负边距值的方法。一般情况下，人们十有八九会选择交换源文件中左中两栏的声明次序。

