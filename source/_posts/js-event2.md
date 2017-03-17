---
title: 事件进阶话题
date: 2017-03-05 23:51:06
categories: [JavaScript]
tags: [进阶,事件]
---

此文内容深度其实不大，个人还需要进一步学习。

<!--more-->

## 常用事件和技巧

用户的操作有很多种，所以有很多事件。为了开发方便，浏览器又提供了一些事件，所以有很多很多的事件。这里只介绍几种常用的事件和使用技巧。

#### load

`load` 事件在资源加载完成时触发。这个资源可以是图片、CSS 文件、JS 文件、视频、document 和 window 等等。

比较常用的就是监听 window 的 `load` 事件，当页面内所有资源全部加载完成之后就会触发。比如用 JS 对图片以及其他资源处理，我们在 `load` 事件中触发，可以保证 JS 不会在资源未加载完成就开始处理资源导致报错。

同样的，也可以监听图片等其他资源加载情况。

#### beforeunload

当浏览者在页面上的输入框输入一些内容时，未保存、误操作关掉网页可能会导致输入信息丢失。

当浏览者输入信息但未保存时关掉网页，我们就可以开始监听这个事件，例如：

```
window.addEventListener("beforeunload", function( event ) {
    event.returnValue = "放弃当前未保存内容而关闭页面？";
});
```

这时候试图关闭网页的时候，会弹窗阻止操作，点击确认之后才会关闭。当然，如果没有必要，就不要监听，不要以为使用它可以为你留住浏览者。

#### resize

当节点尺寸发生变化时，触发这个事件。通常用在 window 上，这样可以监听浏览器窗口的变化。通常用在复杂布局和响应式上。

常见的视差滚动效果网站以及同类比较复杂的布局网站，往往使用 JavaScript 来计算尺寸、位置。如果用户调整浏览器大小，尺寸、位置不随着改变则会出现错位情况。在 window 上监听该事件，触发时调用计算尺寸、位置的函数，可以根据浏览器的大小来重新计算。

但需要注意一点，当浏览器发生任意变化都会触发 `resize` 事件，哪怕是缩小 1px 的浏览器宽度，这样调整浏览器时会触发大量的 `resize` 事件，你的回调函数就会被大量的执行，导致变卡、崩溃等。

你可以使用函数 throttle 或者 debounce 技巧来进行优化，throttle 方法大体思路就是在某一段时间内无论多次调用，只执行一次函数，到达时间就执行；debounce 方法大体思路就是在某一段时间内等待是否还会重复调用，如果不会再调用，就执行函数，如果还有重复调用，则不执行继续等待。关于它们更详细的信息，我后面会介绍一下发表在我的博客上，这里不再赘述。

#### error

当我们加载资源失败或者加载成功但是只加载一部分而无法使用时，就会触发 `error` 事件，我们可以通过监听该事件来提示一个友好的报错或者进行其他处理。比如 JS 资源加载失败，则提示尝试刷新；图片资源加载失败，在图片下面提示图片加载失败等。该事件不会冒泡。因为子节点加载失败，并不意味着父节点加载失败，所以你的处理函数必须精确绑定到目标节点。

需要注意的是，对于该事件，你可以使用 `addEventListener` 等进行监听，但是有时候会出现失效情况（看[这个例子](http://jsbin.com/esimAWA/2/quiet)），这是因为 `error` 事件都触发过了，你的 JS 监听处理代码还没有加载进来执行。为了避免这种情况，用内联法更好一些：

```
<img src="not-found.jpg" onerror="doSomething" />
```
如果还有其他常用事件，欢迎留言补充。
<br>

## 事件回调函数的作用域问题

与事件绑定在一起的回调函数作用域会有问题，我们来看个例子：

```html
<!DOCTYPE html>
<html>
<head>
<meta charset=utf-8 />
  <title>Events in JavaScript: Removing event listeners</title>
</head>
<body>
  <button id="element">Click Me</button>
</body>
</html>
```

JavaScript代码：

```javascript
var element = document.getElementById('element');

var user = {
 firstname: 'Bob',
 greeting: function(){
   alert('My name is ' + this.firstname);
 }
};

// Attach user.greeting as a callback
element.addEventListener('click', user.greeting);
```

回调函数调用的 `user.greeting` 函数作用域应该是在 `user` 下的，本期望输出 `My name is Bob` 结果却输出了 `My name is undefined`。这是因为事件绑定函数时，该函数会以当前元素为作用域执行。为了证明这一点，我们可以为当前 `element` 添加属性：

```
element.firstname = 'jiangshui';
```

再次点击，可以正确弹出 `My name is jiangshui`。那么我们来解决一下这个问题：

### 使用匿名函数——办法一

将JavaScript代码修改为：

```
var element = document.getElementById('element');

var user = {
 firstname: 'Bob',
 greeting: function(){
   alert('My name is ' + this.firstname);
 }
};

// Call the method with the correct
// context inside an anonymouse function
element.addEventListener('click', function() {
  user.greeting();
});
```

包裹之后，虽然匿名函数的作用域被指向事件触发元素，但执行的内容就像直接调用一样，不会影响其作用域。

### 使用 bind 方法

使用匿名函数是有缺陷的，每次调用都包裹进匿名函数里面，增加了冗余代码等，此外如果想使用`removeEventListener` 解除绑定，还需要再创建一个函数引用。`Function` 类型提供了 `bind` 方法，可以为函数绑定作用域，无论函数在哪里调用，都不会改变它的作用域。通过如下语句绑定作用域：

```
user.greeting = user.greeting.bind(user);
```

这样我们就可以直接使用：

```
element.addEventListener('click', user.greeting);
```

## IE 浏览器的差异和兼容性问题

IE 浏览器就是特立独行，它对于事件的操作与标准有一些差异。不过 IE 浏览器现在也开始慢慢努力改造，让浏览器变得更加标准。

### IE 下绑定事件

在 IE 下面绑定一个事件监听，在 IE9- 无法使用标准的 `addEventListener` 函数，而是使用自家的 `attachEvent`，具体用法：

```
element.attachEvent(<event-name>, <callback>);
```

其中 `` 参数需要注意，它需要为事件名称添加 `on` 前缀，比如有个事件叫 `click`，标准事件监听函数监听 `click`，IE 这里需要监听 `onclick`。

另一个，它没有第三个参数，也就是说它只支持监听在冒泡阶段触发的事件，所以为了统一，在使用标准事件监听函数的时候，第三参数传递 false。

当然，这个方法在 IE9 已经被抛弃，在 IE11 已经被移除了，IE 也在慢慢变好。

### IE 中 Event 对象需要注意的地方

IE 中往回调函数中传递的事件对象与标准也有一些差异，你需要使用 `window.event` 来获取事件对象。所以你通常会写出下面代码来获取事件对象：

```
event = event || window.event
```

此外还有一些事件属性有差别，比如比较常用的 `event.target` 属性，IE 中没有，而是使用 `event.srcElement` 来代替。如果你的回调函数需要处理触发事件的节点，那么需要写：

```
node = event.srcElement || event.target;
```

常见的就是这点，更细节的不再多说。在概念学习中，我们没必要为不标准的东西支付学习成本；在实际应用中，类库已经帮我们封装好这些兼容性问题。可喜的是 IE 浏览器现在也开始不断向标准进步。





摘自：[于江水](http://yujiangshui.com/javascript-event/#事件进阶话题)