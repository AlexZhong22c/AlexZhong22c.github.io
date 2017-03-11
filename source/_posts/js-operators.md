---
title: 操作符回顾
date: 2017-02-11 13:12:40
categories: [JavaScript]
tags: [回顾,操作符]
---

ECMAScript 操作符的与众不同之处在于，它们能适用于很多种基本数据类型的值，例如字符串、数字值、布尔值、甚至对象。

不过，在应用于对象时，响应的操作符通常都会调用对象的valueOf()和（或）toString()方法，以便取得可以操作的值。

<!--more-->

## 一元操作符

自增和自减直接借鉴了C语言

自增、自减、加、减这些一元操作符可以用于转换数据类型。

## 位操作符

这是借鉴了一些底层的语言，在特殊情况下才会用到，一般情况下已经很少用了

## 布尔操作符

### 逻辑非

返回的是布尔值

### 逻辑与和逻辑或

如果操作数不只有布尔值：

#### &&

如果第一个操作数是 Boolean 类型，而且值为 false ，那么直接返回 false。 
如果第一个操作数是 Boolean 类型，而且值为 true，另外一个操作数是 object 类型，那么将返回这个对象。 
如果两个操作数都是 object 类型，那么，返回第二个对象。 
如果任何一个操作数是 null，那么，返回 null。 
如果任何一个操作数是 NaN，那么返回 NaN。 
如果任何一个操作数是 undefinded，那么返回 undefined。 

#### ||

如果第一个操作数是 boolean 类型，而且值为 true， 那么，直接返回 true。 
如果第一个操作数是 Boolean 类型，而且值为 false ，第二个操作数为 object，那么返回 object 对象。 
如果两个操作数都是 object 类型，那么返回第一个对象。 
如果两个操作数都是 null，那么，返回 null。 
如果两个操作数都是 NaN，那么返回 NaN。 
如果两个操作数都是 undefined，那么，返回 undefined。

#### 不用搞得这么复杂 推荐大家看这部分的说明

a && b : 将a, b转换为Boolean类型, 再执行逻辑与, true返回b, false返回a 
a || b : 将a, b转换为Boolean类型, 再执行逻辑或, true返回a, false返回b 
转换规则: 
对象为true 
非零数字为true 
非空字符串为true 
其他为false

------

我们可以利用 逻辑或 这一行为来避免为变量赋值 null 或 undefined 值：

```
var myObject = preferredObject || backupObject;
```

变量 preferredObject 的值优先赋给 myObject ，变量 backupObject 的值作为后备。

## 乘性操作符

Infinity 和 -Infinity 表示无穷大和负无穷大

### 乘法

- 如果有一个是NaN，则结果是NaN
- Infinity * 0 ==> NaN

### 除法

- 如果有一个是NaN，则结果是NaN
- Infinity / Infinity ==> NaN
- 0 / 0 ==> NaN

### 求模

a % b：

如果a有限大，而b无限大，结果为a

如果a为0， 结果为0

其他特殊情况一般为NaN

## 加性操作符

### 加法

- 如果只有一个操作数是字符串，则将另一个操作数转换为字符串，然后拼接字符串
  - 如果有一个操作数是对象、数值或布尔值，则调用它们的toString() 方法
  - 对于undefined 和 null ，调用String()函数取得字符串"undefined"和"null"

### 减法

略

## 关系操作符

- 如果两个操作符都是字符串，则比较两个字符串对应的字符编码值
  - 大写字母的字符编码 全部小于 小写字母的字符编码

## 相等操作符

见另外一篇文章