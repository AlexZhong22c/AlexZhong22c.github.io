---
title: js事件绑定基础回顾
date: 2017-01-29 23:51:06
categories: [JavaScript]
tags: [回顾,事件,基础]
---

此文用于快速回顾，不适合用来入门。

<!--more-->

## 绑定事件监听

在 JavaScript 中，有三种常用的绑定事件的方法：

1. HTML 内联属性（避免使用）
2. DOM 属性绑定
3. 使用事件监听函数

### HTML 内联属性（避免使用）

```
<button onclick="alert('你点击了这个按钮');">点击这个按钮</button>
```

使用这种方法，JavaScript 代码与 HTML 代码耦合在了一起，不便于维护和开发。所以除非在必须使用的情况（例如统计链接点击数据）下，尽量避免使用这种方法。

### 在JavaScript代码中绑定

```
element.onclick = function(event){
    alert('你点击了这个按钮');
};

```

缺陷是：因为直接赋值给对应属性，如果你在后面代码中再次为 `element` 绑定一个回调函数，会覆盖掉之前回调函数的内容。

虽然也可以用一些方法实现多个绑定，但还是推荐下面的标准事件监听函数。

### 绑定事件监听函数

```
var btn = document.getElementsByTagName('button');
btn[0].addEventListener('click', function() {
    alert('你点击了这个按钮');
}, false);

```

最后一个参数表示该事件监听是在“捕获”阶段中监听（设置为 true）还是在“冒泡”阶段中监听（设置为 false）。

但一般使用时我们往往传递 false，这是因为 IE 浏览器不支持在捕获阶段监听事件，毕竟 IE 浏览器的份额是不可忽略的。

## 移除事件监听

需要注意的是，绑定事件时的回调函数不能是匿名函数，必须是一个声明的函数，因为解除事件绑定时需要传递这个回调函数的引用，才可以断开绑定。例如：

```
var fun = function() {
    // function logic
};

element.addEventListener('click', fun, false);
element.removeEventListener('click', fun, false);

```

## 事件触发过程

1. 捕获阶段（Capture Phase）

2. 目标阶段（Target Phase）

3. 冒泡阶段（Bubbling Phase）

## 使用事件代理（Event Delegate）提升性能

使用事件代理主要有两个优势：

1. 减少事件绑定，提升性能。之前你需要绑定一堆子节点，而现在你只需要绑定一个父节点即可。减少了绑定事件监听函数的数量。
2. 动态变化的 DOM 结构，仍然可以监听。以前，当一个 DOM 动态创建之后，不会带有任何事件监听，除非你重新执行事件监听函数；而使用事件监听无须担忧这个问题。

如果使用原生的方式实现事件代理，需要注意过滤非目标节点，可以通过 id、class 或者 tagname 等等，例如：

```
element.addEventListener('click', function(event) {
    // 判断是否是 a 节点
    if ( event.target.tagName == 'A' ) {
        // a 的一些交互操作
    }
}, false);
```

## 停止事件冒泡（stopPropagation）

```
element.addEventListener('click', function(event) {
    event.stopPropagation();
}, false);

```

## 事件的 Event 对象

事件对象包括很多有用的信息，比如事件触发时，鼠标在屏幕上的坐标、被触发的 DOM 详细信息、以及上图最下面继承过来的停止冒泡方法（stopPropagation）。下面介绍一下比较常用的几个属性和方法：

### `type`(string)

事件的名称，比如 “click”。

### `target`(node)

事件要触发的目标节点。

### `bubbles` (boolean)

表明该事件是否是在冒泡阶段触发的。

### `preventDefault` (function)

这个方法可以禁止一切默认的行为，例如点击 `a` 标签时，会打开一个新页面，如果为 `a` 标签监听事件 `click` 同时调用该方法，则不会打开新页面。

### `stopPropagation` (function)

停止冒泡，上面有提到，不再赘述。

### `stopImmediatePropagation` (function)

与 `stopPropagation` 类似，就是阻止触发其他监听函数。但是与 `stopPropagation` 不同的是，它更加 “强力”，阻止除了目标之外的事件触发，甚至阻止针对同一个目标节点的相同事件。

## jQuery 中的事件

如果你在写文章或者 Demo，为了简单，你当然可以用上面的事件监听函数，以及那些事件对象提供的方法等。**但在实际中，有一些方法和属性是有兼容性问题的，所以我们会使用 jQuery 来消除兼容性问题。 \**

### 绑定事件和事件代理

```
$( "#dataTable tbody tr" ).on( "click", function() {
  console.log( $( this ).text() );
});

```

### 处理过兼容性的事件对象（Event Object）

事件对象有些方法等也有兼容性差异，jQuery 将其封装处理，并提供跟标准一直的命名。

如果你想在 jQuery 事件回调函数中访问原来的事件对象，需要使用 `event.originalEvent`，它指向原生的事件对象。

### 触发事件 `trigger` 方法

点击某个绑定了 `click` 事件的节点，自然会触发该节点的 `click` 事件，从而执行对应回调函数。

`trigger` 方法可以模拟触发事件，我们单击另一个节点 elementB，可以使用：

```
$(elementB).on('click', function(){
    $(elementA).trigger( "click" );
});

```

来触发 elementA 节点的单击监听回调函数。详情请看文档 [.trigger()](http://api.jquery.com/trigger/)。

## 原生js事件绑定兼容

Dean Edward 所写的 addEvent() 函数：

```
function addEvent(element, type, handler) {
    if (!handler.$$guid) handler.$$guid = addEvent.guid++;
    if (!element.events) element.events = {};
        var handlers = element.events[type];
    if (!handlers) {
        handlers = element.events[type] = {};
        if (element["on" + type]) {
            handlers[0] = element["on" + type];
        }
    }
    handlers[handler.$$guid] = handler;
    element["on" + type] = handleEvent;
}

addEvent.guid = 1;
    
function removeEvent(element, type, handler) {
    if (element.events && element.events[type]) {
        delete element.events[type][handler.$$guid];
    }
}
function handleEvent(event) {
    var returnValue = true;
    event = event || fixEvent(window.event);
    var handlers = this.events[event.type];
    for (var i in handlers) {
        this.$$handleEvent = handlers[i];
        if (this.$$handleEvent(event) === false) {
            returnValue = false;
        }
    }
    return returnValue;
};
    
function fixEvent(event) {
    event.preventDefault = fixEvent.preventDefault;
    event.stopPropagation = fixEvent.stopPropagation;
    return event;
};
fixEvent.preventDefault = function() {
    this.returnValue = false;
};
fixEvent.stopPropagation = function() {
    this.cancelBubble = true;
};
```

eslint版：

```
function addEvent (element, type, handler) {
  if (!handler.$$guid) handler.$$guid = addEvent.guid++
  if (!element.events) element.events = {}
  let handlers = element.events[type]
  if (!handlers) {
    handlers = element.events[type] = {}
    if (element['on' + type]) {
      handlers[0] = element['on' + type]
    }
  }
  handlers[handler.$$guid] = handler
  element['on' + type] = handleEvent
}
addEvent.guid = 1

function removeEvent (element, type, handler) {
  if (element.events && element.events[type]) {
    delete element.events[type][handler.$$guid]
  }
}

function handleEvent (event) {
  var returnValue = true
  event = event || fixEvent(window.event)
  var handlers = this.events[event.type]
  for (var i in handlers) {
    this.$$handleEvent = handlers[i]
    if (this.$$handleEvent(event) === false) {
      returnValue = false
    }
  }
  return returnValue
}

function fixEvent (event) {
  event.preventDefault = fixEvent.preventDefault
  event.stopPropagation = fixEvent.stopPropagation
  return event
}
fixEvent.preventDefault = function () {
  this.returnValue = false
}
fixEvent.stopPropagation = function () {
  this.cancelBubble = true
}
```

