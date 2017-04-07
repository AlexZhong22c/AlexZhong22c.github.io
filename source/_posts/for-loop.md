---
title: js的for循环回顾
date: 2017-03-09 09:16:34
categories: [JavaScript]
tags: [回顾]
---

非常经典，还分析了老的几个浏览器：[es5新增数组方法和兼容性问题](http://www.zhangxinxu.com/wordpress/2013/04/es5新增数组方法/)

ES5 中分别有三种 for 循环：

- 简单的for循环
- for in
- for each

ES6 新增了for of

因为for循环和Array关系非常密切，所以先谈谈Array。

<!--more-->

## Array的本质

Javascript 中的 Array 并不像大部分其他语言的数组。

- Javascript 中的 Array 在内存上并不连续
- Array 的索引并不是指偏移量
- Array 的索引也不是 Number 类型，而是 String 类型的
  - 我们可以正确使用如 arr[0] 的写法的原因是语言可以自动将 Number 类型的 0 转换成 String 类型的 "0" 

有趣的是，每个 Array 对象都有一个 length 的属性，导致其表现地更像其他语言的数组。但为什么在遍历 Array 对象的时候没有输出 length 这一条属性呢？那是因为 for-in 只能遍历“可枚举的属性”， length 属于不可枚举属性，实际上， Array 对象还有许多其他不可枚举的属性。

## 简单 for 循环

最常见的写法是：

```
const arr = [1, 2, 3];
for(let i = 0;i < arr.length; i++) {
  console.log(arr[i]);
}
```

当数组长度在循环过程中不会改变时，我们最好将数组长度用变量存储起来，这样会获得更好的效率：

```
const arr = [1, 2, 3];
for(let i = 0,len=arr.length; i < len; i++) {
  console.log(arr[i]);
}
```

## for in

for-in 一般情况下只用于遍历稀疏数组，这样的好处大大的：

```
let key;
const arr = [];
arr[0] = "a";
arr[100] = "b";
arr[10000] = "c";
for(key in arr) {
    if(arr.hasOwnProperty(key)  &&    
        /^0$|^[1-9]\d*$/.test(key) &&    
        key <= 4294967294               
        ) {
        console.log(arr[key]);
    }
}
```

for-in 只会遍历存在的实体，上面的例子中， for-in 遍历了3次（遍历属性分别为”0″、 “100″、 “10000″的元素，普通 for 循环则会遍历 10001 次）。

为了避免重复劳动，我们可以包装一下上面的代码：

```
function arrayHasOwnIndex(array, prop) {
    return array.hasOwnProperty(prop) &&
        /^0$|^[1-9]\d*$/.test(prop) &&
        prop <= 4294967294; // 2^32 - 2
}
```

使用示例如下：

```
for (let key in arr) {
    if (arrayHasOwnIndex(arr, key)) {
        console.log(arr[key]);
    }
}
```

### 为什么上面代码要加那么多条件判断

for-in 循环遍历的是对象的属性，而不是数组的索引。因此， for-in 遍历的对象便不局限于数组，还可以遍历对象。

```
const person = {
    fname: "san",
    lname: "zhang",
    age: 99
};
let info;
for(info in person) {
    console.log("person[" + info + "] = " + person[info]);
}
```

结果如下：

```
person[fname] = san
person[lname] = zhang
person[age] = 99
```

需要注意的是， for-in 遍历属性的顺序并不确定，即输出的结果顺序与属性在对象中的顺序无关，也与属性的字母顺序无关，与其他任何顺序也无关。

因为期望的是对象，所以**不应该用for in来循环遍历数组**：如果采用prototype扩展原生的Array，这些属性也会被for in遍历出来，这样就有可能出乎程序员的意料：

```
// Somewhere deep in your JavaScript library...
Array.prototype.foo = 1;

// Now you have no idea what the below code will do.
var a = [1, 2, 3, 4, 5];
for (var x in a){
  // Now foo is a part of EVERY array and 
  // will show up here as a value of 'x'.
  console.log(x);
}

/**
 * 输出:
 * 0
 * 1
 * 2
 * 3
 * 4
 * foo
 */
```

### 注意

MDN：[for...in--MDN](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/for...in)：

> `for...in` 循环以任意序迭代一个对象的属性。 
>
> 如果一个属性在一次迭代中被修改，在稍后被访问，其在循环中的值是其在稍后时间的值。正常。
>
> 一个在被访问之前已经被删除的属性将不会在之后被访问。正常。
>
> 在迭代进行时被添加到对象的属性，可能在之后的迭代被访问，也可能被忽略。不正常。
>
> **通常，在迭代过程中最好不要在对象上进行添加属性的值、修改或者删除属性的操作，除非是对当前正在被访问的属性。**
>
> 因为一个被添加的属性在迭代过程中可能会不被访问到。如果不是当前正在被访问的元素：一个修改后的属性可能会在修改前或者修改后被访问 并且 一个被删除的属性可能会在它被删除之前被访问。

通俗来讲就是：要改的话就只能改当前循环访问到的属性，而其他**没有被访问的**或者**还未被当前循环访问到的**属性就不能改。

### for in 性能

正如上面所说，每次迭代操作会同时搜索实例或者原型属性， for-in 循环的每次迭代都会产生更多开销，因此要比其他循环类型慢，一般速度为其他类型循环的 1/7。因此，除非明确需要迭代一个属性数量未知的对象，否则应避免使用 for-in 循环。如果需要遍历一个数量有限的已知属性列表，使用其他循环会更快，比如下面的例子：

```
const obj = {
    "prop1": "value1",
    "prop2": "value2"
};

const props = ["prop1", "prop2"];
for(let i = 0; i < props.length; i++) {
    console.log(obj[props[i]]);
}
```

上面代码中，将对象的属性都存入一个数组中，相对于 `for-in` 查找每一个属性，该代码只关注**给定的**属性，节省了循环的开销和时间。

## forEach

forEach只支持IE9及以上。forEach把数组对象的引索当做是number类型。本文章的最后有它的polyfill。

`forEach` 可以当做是`for(let i = 0; i < len; i++)`的简写，但是不能完成 `i + n` 这种循环，同时也不支持 `continue`和 `break`，只能通过 `return` 来控制循环。另外，使用`forEach`的话，是不能退出循环本身的。

forEach 方法为数组中含有有效值的每一项执行一次 callback 函数，那些已删除（使用 delete 方法等情况）或者从未赋值的项将被跳过（不包括那些值为 undefined 或 null 的项）。 callback 函数会被依次传入三个参数：

- 数组当前项的值；
- 数组当前项的索引；
- 数组对象本身；

需要注意的是，forEach 遍历的范围在第一次调用 callback 前就会确定。调用forEach 后添加到数组中的项不会被 callback 访问到。如果已经存在的值被改变，则传递给 callback 的值是 forEach 遍历到他们那一刻的值。已删除的项不会被遍历到。

```
const arr = [];
arr[0] = "a";
arr[3] = "b";
arr[10] = "c";
arr.name = "Hello world";
arr.forEach((data, index, array) => {
    console.log(data, index, array);
});
```

运行结果：

```
a 0 ["a", 3: "b", 10: "c", name: "Hello world"]
b 3 ["a", 3: "b", 10: "c", name: "Hello world"]
c 10 ["a", 3: "b", 10: "c", name: "Hello world"]
```

这里的 index 是 Number 类型，并且也不会像 for-in 一样遍历原型链上的属性。

所以，使用 forEach 时，我们不需要专门地声明 index 和遍历的元素，因为这些都作为回调函数的参数。

另外，forEach 将会遍历数组中的所有元素，但是 ES5 定义了一些其他有用的方法，下面是一部分：

- every: 循环在第一次 return false 后返回
- some: 循环在第一次 return true 后返回
- filter: 返回一个新的数组，该数组内的元素满足回调函数
- map: 将原数组中的元素处理后再返回
- reduce: 对数组中的元素依次处理，将上次处理结果作为下次处理的输入，最后得到最终结果。

### forEach的性能

大家可以看 jsPerf ，在不同浏览器下测试的结果都是 forEach 的速度不如 for。如果大家把测试代码放在控制台的话，可能会得到不一样的结果，主要原因是控制台的执行环境与真实的代码执行环境有所区别。

## for of

```
const arr = ['a', 'b', 'c'];
for(let data of arr) {
    console.log(data);
}
```

运行结果是：

```
a
b
c
```

### 为什么要引进 for-of？

要回答这个问题，我们先来看看ES6之前的 3 种 for 循环有什么缺陷：

- forEach 不能 break 和 return；
- for-in 缺点更加明显，它不仅遍历数组中的元素，还会遍历自定义的属性，甚至原型链上的属性都被访问到。而且，遍历数组元素的顺序可能是随机的。

所以，鉴于以上种种缺陷，我们需要改进原先的 for 循环。但 ES6 不会破坏你已经写好的 JS 代码。目前，成千上万的 Web 网站依赖 for-in 循环，其中一些网站甚至将其用于数组遍历。如果想通过修正 for-in 循环增加数组遍历支持会让这一切变得更加混乱，因此，标准委员会在 ES6 中增加了一种新的循环语法来解决目前的问题，即 for-of 。

那 for-of 到底可以干什么呢？

- 跟 forEach 相比，可以正确响应 break, continue, return。
- for-of 循环不仅支持数组，还支持大多数类数组对象，例如 DOM nodelist 对象。
- for-of 循环也支持字符串遍历，它将字符串视为一系列 Unicode 字符来进行遍历。
- for-of 也支持 Map 和 Set （两者均为 ES6 中新增的类型）对象遍历。

总结一下，for-of 循环有以下几个特征：

- 这是最简洁、最直接的遍历数组元素的语法。
- 这个方法避开了 for-in 循环的所有缺陷。
- 与 forEach 不同的是，它可以正确响应 break、continue 和 return 语句。
- 其不仅可以遍历数组，还可以遍历类数组对象和其他可迭代对象。

但需要注意的是，for-of循环不支持普通对象，但如果你想迭代一个对象的属性，你可以用

for-in 循环（这也是它的本职工作）。

最后要说的是，ES6 引进的另一个方式也能实现遍历数组的值，那就是 Iterator。上个例子：

```
const arr = ['a', 'b', 'c'];
const iter = arr[Symbol.iterator]();

iter.next() // { value: 'a', done: false }
iter.next() // { value: 'b', done: false }
iter.next() // { value: 'c', done: false }
iter.next() // { value: undefined, done: true }
```

Iterator 要另外再介绍。

## 补充forEach的polyfill

```
// Production steps of ECMA-262, Edition 5, 15.4.4.18
// Reference: http://es5.github.io/#x15.4.4.18
if (!Array.prototype.forEach) {
  Array.prototype.forEach = function(callback, thisArg) {
    var T, k;
    if (this == null) {
      throw new TypeError(' this is null or not defined');
    }
    // 1. Let O be the result of calling toObject() passing the
    // |this| value as the argument.
    var O = Object(this);
    // 2. Let lenValue be the result of calling the Get() internal
    // method of O with the argument "length".
    // 3. Let len be toUint32(lenValue).
    var len = O.length >>> 0;
    // 4. If isCallable(callback) is false, throw a TypeError exception. 
    // See: http://es5.github.com/#x9.11
    if (typeof callback !== "function") {
      throw new TypeError(callback + ' is not a function');
    }
    // 5. If thisArg was supplied, let T be thisArg; else let
    // T be undefined.
    if (arguments.length > 1) {
      T = thisArg;
    }
    // 6. Let k be 0
    k = 0;
    // 7. Repeat, while k < len
    while (k < len) {
      var kValue;
      // a. Let Pk be ToString(k).
      //    This is implicit for LHS operands of the in operator
      // b. Let kPresent be the result of calling the HasProperty
      //    internal method of O with argument Pk.
      //    This step can be combined with c
      // c. If kPresent is true, then
      if (k in O) {
        // i. Let kValue be the result of calling the Get internal
        // method of O with argument Pk.
        kValue = O[k];
        // ii. Call the Call internal method of callback with T as
        // the this value and argument list containing kValue, k, and O.
        callback.call(T, kValue, k, O);
      }
      // d. Increase k by 1.
      k++;
    }
    // 8. return undefined
  };
}
```

