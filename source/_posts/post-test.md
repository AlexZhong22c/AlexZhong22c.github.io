---
title: post-test
date: 2017-02-20 23:12:32
categories: [小笔记]
tags: [tag1]
---

我这里就写写摘要，字数不多，就是为了充个数。我这里就写写摘要，字数不多，就是为了充个数。我这里就写写摘要，字数不多，就是为了充个数。我这里就写写摘要，字数不多，就是为了充个数。我这里就写写摘要，字数不多，就是为了充个数。我这里就写写摘要，字数不多，就是为了充个数。

---
<!--more-->
下面要介绍的是函数表达式，看一下博文的样式怎么样。​:blush:​​:blush:​​:blush:​

## 函数表达式

- 将函数赋值给变量

```
// function variable
var add = function(a, b) {
    // body...
};
```

- 立即执行函数，把匿名函数​:blush:​用括号括起来，再直接调用。

```
// IEF(Immediately Executed Function)
(function() {
    // body...
})();

```

- 函数对象作为返回值

```
return function() {
    // body...
};
```

- 命名式函数表达式

```
//NFE(Named Function Expression)
var add = function foo(a, b) {
    // body...
};
```

这里大家肯定会好奇，这个函数怎么调用？到底用哪个名字呢？

做一个测试：

```
var func = function nfe() {};
console.log(func === nfe);
// 在 IE6~8，得到 false
// 在 IE9+ 及现代浏览器中 Uncaught ReferenceError: nfe is not defined
```

那么命名函数表达式有什么使用场景呢？

- 一般用于调试方便，如果使用匿名函数，执行的时候看不到函数名，命名函数表达式是可以看到函数名的。
- 或者在递归时，使用名字调用自己。

但是这两种用法都不常见。

### Function 构造器

除了函数声明、函数表达式。还有一种创建函数对象的方式，[google](www.baidu.com)是使用函数构造器。

````
var func = new Function('a','b','console.log(a+b);');
func(1,2);//3

var func2 = Function('a','b','console.log(a+b);');
func2(1,2);//3
````

Function 中前面的参数为后面函数体的形参，最后一个参数为函数体。可以看到传入的都是字符串，这样的创建函数对象的方法是不安全的。

还有一点，Function 构造器的得到的函数对象，拿不到外层函数的变量，但是可以拿到全局变量。它的作用域与众不同，这也是很少使用的原因之一。

---

### // 三种方法的对比:

水电费的说法水电费水电费水电费。水电费的说法水电费水电费水电费。水电费的说法水电费水电费水电费。水电费的说法水电费水电费水电费。水电费的说法水电费水电费水电费。水电费的说法水电费水电费水电费。水电费的说法水电费水电费水电费。水电费的说法水电费水电费水电费。

---

## 变量 & 函数的声明前置

举两个例子

例1，函数声明：

````
var num = add(1,2);
console.log(num);

function add(a, b) {
    return a + b;
}
````

例2，函数表达式：

````JavaScript
function findSequence(goal) {
  function find(start, history) {
    if (start == goal)
      return history;
    else if (start > goal)
      return null;
    else
      return find(start + 5, "(" + history + " + 5)") ||
             find(start * 3, "(" + history + " * 3)");
  }
  return find(1, "1");
}
````

例1中得到的结果是 3，而例2中是 ``Uncaught TypeError: add is not a function``。

因为函数和变量在声明的时候，会被前置到当前作用域的顶端。例1将函数声明``function add(a, b)``前置到作用域前端，例2将声明``var add``前置到其作用域的前端了，并没有赋值。**赋值的过程是在函数执行到响应位置的时候才进行的。**

---

## 调用方式

- 直接调用

```
foo();
```

- 对象方法

```
o.method();
```

- 构造器

```
new Foo();
```

- call/apply/bind

```
func.call(o);
```

------

## 函数属性

### arguments属性

函数的arguments属性使函数可以处理可变数量的参数。 **arguments** 对象的 **length** 属性包含了传递给函数的参数数目。 **arguments** 对象中包含的各个参数的访问方式与数组元素的访问方式相同。

````
function ArgTest(arg1, arg2){
   var s = "";
   s += "The individual arguments are: "
   for (n = 0; n < arguments.length; n++){
      s += ArgTest.arguments[n];
      s += " ";
   }
   return(s);
}
console.log(ArgTest(1, 2, "hello"));
// Output: The individual arguments are: 1 2 hello
````

可以可以可以可以可以可以可以可以可以可以可以可以

1. 这个是有序雷利啊的撒打算 自己来的
2. 水电费惊世毒妃历史的快捷方式水电费 范德萨ds
3. 3热热热但是范德萨但是第三方第三方但是非

可以可以可以可以可以可以可以可以可以可以可以可以

1\. 这个是有序雷利啊的撒打算 自己来的

2\. 水电费惊世毒妃历史的快捷方式水电费 范德萨ds

### caller属性

>functionName.caller

*functionName* 对象是任何正在执行的函数的名称。

**caller** 属性只有当函数正在执行时才被定义。  如果函数是从 JavaScript 程序的顶层调用的，则 **caller** 包含 **null**。  

如果在字符串上下文中使用 **caller** 属性，则其结果和 *functionName*.**toString** 相同，也就是说，将显示函数的反编译文本。

下面的示例阐释了 **caller** 属性的用法：

````
function CallLevel(){
   if (CallLevel.caller == null)
      return("CallLevel was called from the top level.");
   else
      return("CallLevel was called by another function.");
}

console.log(CallLevel());
// Output: CallLevel was called from the top level.
````

---

### apply属性(方法)

> 调用函数，并用指定对象替换函数的 **this** 值，同时用指定数组替换函数的参数。
>
> apply([thisObj[,argArray]])
>
> ``thisObj``：可选。要用作 this 对象的对象。即调用这个函数的对象。
>
> ``argArray``：可选。要传递到函数的一组参数。

---

### call属性(方法)

apply 后面的参数为数组，而call 为扁平化传参

````
function foo(x, y) {
    console.log(x, y, this);
}

foo.call(100, 1, 2); //1 2 Number {[[PrimitiveValue]]: 100}
foo.apply(true, [3, 4]); //3 4 Boolean {[[PrimitiveValue]]: true}
foo.apply(null); //undefined undefined Window
foo.apply(undefined); //undefined undefined Window
````

传入 null/undefined 时，实际为 Window 对象
在严格模式下：上述代码最后两行分别输出 null, undefined

---

### bind属性(方法)

1. 下面的代码演示如何使用 **bind** 方法。

````
// Define the original function.
var checkNumericRange = function (value) {
    if (typeof value !== 'number')
        return false;
    else
        return value >= this.minimum && value <= this.maximum;
}

// The range object will become the this value in the callback function.
var range = { minimum: 10, maximum: 20 };

// Bind the checkNumericRange function.
var boundCheckNumericRange = checkNumericRange.bind(range);

// Use the new function to check whether 12 is in the numeric range.
var result = boundCheckNumericRange (12);
document.write(result);
console.log(result);	// true
````

2. 在下面的示例中，thisArg 对象与包含原始方法的对象不同。

````
// Create an object that contains the original function.
// Offer the range: [50,100]
var originalObject = {
    minimum: 50,
    maximum: 100,
    checkNumericRange: function (value) {
        if (typeof value !== 'number')
            return false;
        else
            return value >= this.minimum && value <= this.maximum;
    }
}

// Check whether 10 is in the numeric range.
var result = originalObject.checkNumericRange(10);
console.log(result + " ");
// Output: false

// The range object supplies the range for the bound function.
// Offer the range: [10,20]
var range = { minimum: 10, maximum: 20 };

// Create a new version of the checkNumericRange function that uses range.
var boundObjectWithRange = originalObject.checkNumericRange.bind(range);

// Check whether 10 is in the numeric range.
var result = boundObjectWithRange(10);
console.log(result);
// Output: true
````

显然后者更加灵活一点。

再来一个例子：

````
this.x = 9;
var module = {
    x: 81,
    getX: function() {
        return console.log(this.x);
    }
};

module.getX(); //81
// 函数的调用者为module，函数的this指向module


var getX = module.getX;
getX(); //9
// var getX = module.getX; 将这个方法赋值给一个全局变量，这时 this 指向了 window
// 函数的调用者为window，函数的this指向window

var boundGetX = getX.bind(module);
boundGetX(); //81
// 应用bind,函数的调用者为window，函数的this指向module
````

一般情况下，谁调用函数，函数的this就指向谁。

`bind` 主要用于改变函数中的 `this`

- `module.getX(); `直接通过对象调用自己的方法，结果是 81
- `var getX = module.getX;` 将这个方法赋值给一个全局变量，这时 this 指向了 window，所以结果为 9
- `var boundGetX = getX.bind(module);` 使用 bind 绑定了自己的对象，这样 this 仍然指向 module 对象，所以结果为 81



3. 以下代码演示如何使用 *arg1[,arg2[,argN]]]* 参数。绑定函数将 **bind** 方法中指定的参数用作第一个参数和第二个参数。在调用绑定函数时指定的任何参数将用作第三个、第四个参数（依此类推）。

````
// Define the original function with four parameters.
var displayArgs = function (val1, val2, val3, val4) {
    console.log(val1 + " " + val2 + " " + val3 + " " + val4);
}

var emptyObject = {};

// Create a new function that uses the 12 and "a" parameters
// as the first and second parameters.
var displayArgs2 = displayArgs.bind(emptyObject, 12, "a");

// Call the new function. The "b" and "c" parameters are used
// as the third and fourth parameters.
displayArgs2("b", "c");
// Output: 12 a b c 
````

---

#### bind 与 currying

bind 可以使函数柯里化，那么什么是柯里化？

>在计算机科学中，柯里化（Currying）是把接受多个参数的函数变换成接受一个单一参数(最初函数的第一个参数)的函数，并且返回 **接受**余下的参数且**返回**结果的新函数 的技术。这个技术由 Christopher Strachey 以逻辑学家 Haskell Curry 命名的，尽管它是 Moses Schnfinkel 和 Gottlob Frege 发明的。


````javascript
function add(a, b, c) {
    return a + b + c;
}

var func = add.bind(undefined, 100);
func(1, 2); //103

var func2 = func.bind(undefined, 200);
func2(10); //310
````

add 函数拥有 3 个参数。我们想先传入一个参数，再去传其他参数。

``var func = add.bind(undefined, 100); ``add 函数对象调用 bind 方法，由于不需要将 this 指向原来的 add 函数对象，所以第一个参数写为 undefined 或 null。第二个参数 100 传给了 add 函数中的形参 a，并赋值给一个新的函数对象 func。

这时，``func(1, 2)`` 即相当于传入后两个参数，所以结果为 103。

同理，基于 func 可以创造一个函数 func2。它只用传最后一个参数。

---

#### bind 与 new

````
function foo() {
    this.b = 100;
    return this.a;
}

console.log(foo()); //undefined

var func = foo.bind({
    a: 1
});

console.log(func()); //1
console.log(new func()); //foo {b: 100}
````

对于使用了 `new func()` 这种方式创建对象，其返回值``应为一个对象。``

而原函数 foo 的返回值不是对象，所以会直接忽视这个 return 方法。而是变为 `return this;`。并且 this 会被初始化为一个空对象，这个空对象的原型指向 foo.prototype。所以后面的 bind 是不起作用的。

这里面这个 this 对象包含一个属性 `b = 100`。所以返回的是对象 `{b: 100}`。

mdn有提到，bind不要和构造函数一起用，各浏览器可能结果不一样。mdn建议不要这样用。
