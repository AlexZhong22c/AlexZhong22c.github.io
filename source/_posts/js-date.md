---
title: JavaScript Date对象回顾
date: 2017-05-07 20:38:10
categories: [JavaScript]
tags: [回顾,时间]
---

此文用于快速回顾，不适合用来入门。

Date 对象：涉及基于1970年1月1日(世界标准时间)起的毫秒数。

<!--more-->

## 构造函数

```
new Date();
// 依据系统设置的当前时间来创建一个Date对象
new Date(value);
// value 代表自1970年1月1日00:00:00 (世界标准时间) 起经过的毫秒数。表达式的结果为一个字符串。
new Date(dateString);
// new Date("05 October 2011 14:48 UTC");
new Date(year, month[, day[, hour[, minutes[, seconds[, milliseconds]]]]]);
// 注意：month 代表月份的整数值从0（1月）到11（12月）。
```

解释：

- 如果没有输入任何参数，则Date的构造器会依据系统设置的当前时间来创建一个Date对象。
- **JavaScript的Date对象为跨平台提供了统一的行为。** 时间属性可以在不同的系统中表示相同的时刻，而如果使用了本地时间对象，则反映当地的时间。
- JavaScript 的Date对象提供了数个UTC时间的方法，也相应提供了当地时间的方法。UTC，也就是我们所说的格林威治时间，指的是time中的世界时间标准。而当地时间则是指执行JavaScript的客户端电脑所设置的时间。


- **以一个函数的形式来调用JavaScript的Date对象（i.e., 不使用new操作符）会返回一个代表当前日期和时间的字符串。**

## 方法

```
Date.now()
// 返回自 1970-1-1 00:00:00  UTC (时间标准时间)至今所经过的毫秒数。也可以直接new Date()
Date.parse()
// 解析一个表示日期的字符串，并返回从 1970-1-1 00:00:00 所经过的毫秒数。IE9
Date.UTC()
// 接受和构造函数最长形式的参数相同的参数（从2到7），并返回从 1970-01-01 00:00:00 UTC 开始所经过的毫秒数。
```

## 实例方法

### Date.prototype.getMonth()

根据本地时间返回指定日期对象的月份（0-11）。（0表示一年中的第一月）

### Date.prototype.getTime()

```
new Date(1994, 1, 10)
// Thu Feb 10 1994 00:00:00 GMT+0800 (中国标准时间)
new Date(1994, 1, 10).getTime()
// 760809600000
```

#### 利用getTime()创建一个拥有相同时间值的日期对象：

```
var birthday = new Date(1994, 12, 10)
var copy = new Date()
copy.setTime(birthday.getTime())
```

### Date.prototype.toUTCString()

而Date.prototype.toISOString()其实也同理：

```
var today = new Date();
var UTCstring = today.toUTCString()
// Mon, 03 Jul 2006 21:44:38 GMT
```

> GMT和UTC：
>
> 从理论上说，GMT和UTC应该是两回事。
>
> 但是由于一开始设计者的失误，现在我们将错就错，在JavaScript Date对象的范畴里面，我们把GMT和UTC看做是同一回事。

### Date.prototype.toTimeString()

`toTimeString()` 方法以人类易读形式返回一个日期对象时间部分的字符串，该字符串以美式英语格式化。

Date 对象的实例引用一个具体的时间点。 调用 toString 方法以美式英语和人类易读的形式，返回日期对象的格式化字符串。

而`toDateString()`也同理：

```
var d = new Date(1993, 6, 28, 14, 39, 7)

console.log(d.toString());     // "Wed Jul 28 1993 14:39:07 GMT+0800 (中国标准时间)"
console.log(d.toTimeString()); // "14:39:07 GMT+0800 (中国标准时间)"

console.log(d.toString());     // "Wed Jul 28 1993 14:39:07 GMT+0800 (中国标准时间)"
console.log(d.toDateString()); // "Wed Jul 28 1993"
```

## 将ISO转UTC：

```
new Date("2017-05-05T12:59:16.373Z")
// d为"Fri May 05 2017 21:00:20 GMT+0800"
d.toUTCString()
// "Fri, 05 May 2017 13:00:20 GMT"
```

如果不想自己折腾的话，就使用别人的轮子吧，[moment](https://github.com/moment/moment)。