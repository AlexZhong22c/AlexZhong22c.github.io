---
title: IIFE回顾
date: 2017-03-10 08:20:16
categories: [JavaScript]
tags: [回顾,IIFE,作用域,单例]
---

此文用于快速回顾，不适合用来入门。

<!--more-->

## 定义

IIFE: 意为立即调用的函数表达式，也就是说，**声明函数的同时立即调用这个函数。**

### 对比

如果不采用IIFE：

```
function foo(){
  var a = 10;
  console.log(a);
}

foo();
```

函数声明和执行是可以分离的。

------

如果采用IIFE：

```
(function foo(){
  var a = 10;
  console.log(a);
})();
```

JS编译器不再认为这是一个函数声明，而是一个IIFE，即需要立刻执行声明的函数。

两者达到的目的是相同的，都是声明了一个函数foo并且随后调用函数foo。

## 为什么需要IIFE

- 立即执行一个函数
- 需要用函数实现作用域隔离

在这两种情景下，使用IIFE就比较方便。

如果只是为了立即执行一个函数，显然IIFE所带来的好处有限。实际上，IIFE的出现是为了弥补JS在scope方面的缺陷：JS只有全局作用域（global scope）、函数作用域（function scope），从ES6开始才有块级作用域（block scope）。对比现在流行的其他面向对象的语言可以看出，JS在访问控制这方面是多么的脆弱！那么如何实现作用域的隔离呢？在JS中，只有function，只有function，**只有function才能实现作用域隔离，**因此如果要将一段代码中的变量、函数等的定义隔离出来，只能将这段代码封装到一个函数中。

在我们通常的理解中，将代码封装到函数中的目的是为了复用。在JS中，当然声明函数的目的在大多数情况下也是为了复用，但是JS迫于作用域控制手段的贫乏，我们也经常看到只使用一次的函数：这通常的目的是为了隔离作用域了！**既然只使用一次，那么立即执行好了！既然只使用一次，函数的名字也省掉了！这就是IIFE的由来。**

## IIFE的函数名和参数

```
var a = 2;
(function IIFE(global){
    var a = 3;
    console.log(a); // 3
    console.log(global.a); // 2
})(window);

console.log(a); // 2
```

## IIFE构造单例模式

JS的模块就是函数，最常见的模块定义如下：

```
function myModule(){
  var someThing = "123";
  var otherThing = "456";

  function doSomeThing(){
    console.log(someThing);
  }

  function doOtherThing(){
    console.log(otherThing);
  }

  return {
    doSomeThing:doSomeThing,
    doOtherThing:doOtherThing
  }
}

var foo = myModule();
foo.doSomeThing();
foo.doOtherThing();

var foo1 = myModule();
foo1.doSomeThing();
```

如果需要一个单例模式的模块，那么可以利用IIFE：

```
var myModule = (function module(){
  var someThing = "123";
  var otherThing = "456";

  function doSomeThing(){
    console.log(someThing);
  }

  function doOtherThing(){
    console.log(otherThing);
  }

  return {
    doSomeThing:doSomeThing,
    doOtherThing:doOtherThing
  }
})();

myModule.doSomeThing();
myModule.doOtherThing();
```



参考：[IIFE--subaochen](http://dz.sdut.edu.cn/blog/subaochen/2016/02/说一说js的iife/)