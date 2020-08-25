[个人技术博客2017~2020](https://alexzhong22c.github.io/)

由于历史原因，分类不是很合理，且还有一些老旧的话题，但是划分得还是挺清晰的：

## ｜01 浏览器 

- [02-跨域通信和跨tab通信](https://alexzhong22c.github.io/2020/05/22/cross-origin-cross-tab/)&nbsp;&nbsp;|&nbsp;&nbsp;2020-05-22&nbsp;&nbsp;|&nbsp;&nbsp;标签：[跨域](https://alexzhong22c.github.io/tags/跨域/) [面试题](https://alexzhong22c.github.io/tags/面试题/) [笔记副本](https://alexzhong22c.github.io/tags/笔记副本/) [跨tab](https://alexzhong22c.github.io/tags/跨tab/)
  - <p>上一篇文章介绍了什么是“跨域”和“跨站”。可知，“同站”通信也是“跨域”的一种途径。</p>
  - <p>这次列举一下跨域通信的方法，同时对跨tab通信有启发性价值。</p>
  - <p>因为前人总结得实在是太齐全了！这里只是做到基本列举齐全，然后做一些小小的补充。</p>
- [01-跨域和跨站的基本概念](https://alexzhong22c.github.io/2020/05/22/cross-origin-cross-site/)&nbsp;&nbsp;|&nbsp;&nbsp;2020-05-22&nbsp;&nbsp;|&nbsp;&nbsp;标签：[跨域](https://alexzhong22c.github.io/tags/跨域/) [跨站](https://alexzhong22c.github.io/tags/跨站/) [Cookie](https://alexzhong22c.github.io/tags/Cookie/) [面试题](https://alexzhong22c.github.io/tags/面试题/) [笔记副本](https://alexzhong22c.github.io/tags/笔记副本/)
  - <p>介绍一下跨域和跨站的基本概念、以及简要解释第三方cookie的原理。</p>
- [Web前端性能优化概述](https://alexzhong22c.github.io/2018/02/04/performance-optimized-summary/)&nbsp;&nbsp;|&nbsp;&nbsp;2018-02-04&nbsp;&nbsp;|&nbsp;&nbsp;标签：[面试题](https://alexzhong22c.github.io/tags/面试题/) [笔记副本](https://alexzhong22c.github.io/tags/笔记副本/) [回顾](https://alexzhong22c.github.io/tags/回顾/) [性能优化](https://alexzhong22c.github.io/tags/性能优化/)
  - <p>此文用于快速回顾，不适合用来入门。如果想做一个系统性的归纳总结、以便查询，可以参考以下概述。</p>
- [浏览器事件冒泡或者捕获相关](https://alexzhong22c.github.io/2017/07/02/js-event4/)&nbsp;&nbsp;|&nbsp;&nbsp;2017-07-02&nbsp;&nbsp;|&nbsp;&nbsp;标签：[笔记副本](https://alexzhong22c.github.io/tags/笔记副本/) [回顾](https://alexzhong22c.github.io/tags/回顾/) [基础](https://alexzhong22c.github.io/tags/基础/) [事件](https://alexzhong22c.github.io/tags/事件/)
  - <p>此文用于快速回顾，不适合用来入门。</p>
- [js四种事件处理程序](https://alexzhong22c.github.io/2017/07/01/js-event3/)&nbsp;&nbsp;|&nbsp;&nbsp;2017-07-01&nbsp;&nbsp;|&nbsp;&nbsp;标签：[回顾](https://alexzhong22c.github.io/tags/回顾/) [基础](https://alexzhong22c.github.io/tags/基础/) [事件](https://alexzhong22c.github.io/tags/事件/)
  - <p>随着W3C不断推进DOM事件模型和IE浏览器事件模型的历史变化，为了方便理解，程序员们中逐渐形成 四种事件处理程序 的概念划分。</p>
- [js取消默认事件行为](https://alexzhong22c.github.io/2017/07/01/js-pv-default/)&nbsp;&nbsp;|&nbsp;&nbsp;2017-07-01&nbsp;&nbsp;|&nbsp;&nbsp;标签：[回顾](https://alexzhong22c.github.io/tags/回顾/) [基础](https://alexzhong22c.github.io/tags/基础/) [事件](https://alexzhong22c.github.io/tags/事件/)
  - <p>常见的默认行为有，点击链接后，浏览器跳转到指定页面；再比如<code>&lt;form&gt;</code>表单元素的&quot;submit&quot;事件，当我们触发表单的提交事件时，就可以提交当前表单。</p>

## ｜02 CSS 

- [深入理解文字高度和行高的设置](https://alexzhong22c.github.io/2019/02/06/height-calculate/)&nbsp;&nbsp;|&nbsp;&nbsp;2019-02-06&nbsp;&nbsp;|&nbsp;&nbsp;标签：[进阶](https://alexzhong22c.github.io/tags/进阶/) [居中](https://alexzhong22c.github.io/tags/居中/) [line-height](https://alexzhong22c.github.io/tags/line-height/) [font-size](https://alexzhong22c.github.io/tags/font-size/)
  - <p>font-size设置的是什么?line-height设置的是什么?各种行高是怎么计算出来的?你真的知道吗?</p>
- [vertical-align:middle近似居中和完美居中](https://alexzhong22c.github.io/2019/02/05/vertical-align-middle/)&nbsp;&nbsp;|&nbsp;&nbsp;2019-02-05&nbsp;&nbsp;|&nbsp;&nbsp;标签：[进阶](https://alexzhong22c.github.io/tags/进阶/) [vertical-align](https://alexzhong22c.github.io/tags/vertical-align/) [居中](https://alexzhong22c.github.io/tags/居中/)
  - <p>很多人想要垂直居中的时候，第一时间就想到了<code>vertical-align:middle</code>，用完之后，疑惑它怎么会无效呢?</p>
  - <p>——原来<code>vertical-align</code> 是有适用范围的限制的。</p>
  - <p>因为水平垂直居中直接就包括了垂直居中，本文直接给出水平垂直居中的例子，并说明其中垂直居中的原理。</p>
- [总结：使单一对象水平/垂直居中](https://alexzhong22c.github.io/2019/02/05/centralize-one-ele/)&nbsp;&nbsp;|&nbsp;&nbsp;2019-02-05&nbsp;&nbsp;|&nbsp;&nbsp;标签：[进阶](https://alexzhong22c.github.io/tags/进阶/) [vertical-align](https://alexzhong22c.github.io/tags/vertical-align/) [居中](https://alexzhong22c.github.io/tags/居中/)
  - <p>明白单一对象的水平/垂直居中的写法和原理，有助于我们构造更加复杂的居中布局。</p>
  - <p>我们按照居中的“里面的内容”来分类，展开全文：</p>
- [三栏式布局--IFE2017-CSS-task03笔记](https://alexzhong22c.github.io/2017/09/17/ife-css-task03/)&nbsp;&nbsp;|&nbsp;&nbsp;2017-09-17&nbsp;&nbsp;|&nbsp;&nbsp;标签：[IFE](https://alexzhong22c.github.io/tags/IFE/) [圣杯布局](https://alexzhong22c.github.io/tags/圣杯布局/) [双飞翼布局](https://alexzhong22c.github.io/tags/双飞翼布局/)
  - <p>对应代码的github仓库的地址：<a href="https://github.com/AlexZhong22c/IFE-CSS-learning" target="_blank" rel="noopener">https://github.com/AlexZhong22c/IFE-CSS-learning</a></p>
- [border-radius属性](https://alexzhong22c.github.io/2017/09/07/css-border1/)&nbsp;&nbsp;|&nbsp;&nbsp;2017-09-07&nbsp;&nbsp;|&nbsp;&nbsp;标签：[radius](https://alexzhong22c.github.io/tags/radius/) [边框](https://alexzhong22c.github.io/tags/边框/) [回顾](https://alexzhong22c.github.io/tags/回顾/)
  - <p>border-radius，作为CSS3中经常被用及的属性，我们用一篇文章做一下总结。</p>
- [闭合浮动和BFC和阻止上下外边距的合并](https://alexzhong22c.github.io/2017/04/01/clearfix-n-bfc/)&nbsp;&nbsp;|&nbsp;&nbsp;2017-04-01&nbsp;&nbsp;|&nbsp;&nbsp;标签：[清除浮动](https://alexzhong22c.github.io/tags/清除浮动/) [BFC](https://alexzhong22c.github.io/tags/BFC/) [伪元素](https://alexzhong22c.github.io/tags/伪元素/) [阻止上下外边距合并](https://alexzhong22c.github.io/tags/阻止上下外边距合并/)
  - <p>本文部分内容参考 <a href="http://www.iyunlu.com/view/css-xhtml/55.html" target="_blank" rel="noopener">那些年我们一起清除过的浮动</a> ，但是 一丝冰凉 的这篇文章有很多地方我都不认同，取其精华去其糟粕，所以本文并没有包含那些我所不认同的内容。</p>
- [IFE2017-CSS-task02笔记](https://alexzhong22c.github.io/2017/04/01/ife-css-task02/)&nbsp;&nbsp;|&nbsp;&nbsp;2017-04-01&nbsp;&nbsp;|&nbsp;&nbsp;标签：[IFE](https://alexzhong22c.github.io/tags/IFE/) [list-style](https://alexzhong22c.github.io/tags/list-style/) [文字](https://alexzhong22c.github.io/tags/文字/)
  - <p>对应代码的github仓库的地址：<a href="https://github.com/AlexZhong22c/IFE-CSS-learning" target="_blank" rel="noopener">https://github.com/AlexZhong22c/IFE-CSS-learning</a></p>
  - <p>这篇文章的内容基本没有用在 <a href="https://alexzhong22c.github.io/IFE-CSS-learning/task02.html">demo</a> 中，这只是一番拓展性总结。</p>
- [CSS选择器优先级](https://alexzhong22c.github.io/2017/03/31/css-selectors-specificity/)&nbsp;&nbsp;|&nbsp;&nbsp;2017-03-31&nbsp;&nbsp;|&nbsp;&nbsp;标签：[CSS选择器](https://alexzhong22c.github.io/tags/CSS选择器/) [优先级](https://alexzhong22c.github.io/tags/优先级/) [权重](https://alexzhong22c.github.io/tags/权重/)
  - <p>CSS优先级计算的快速回顾，最后附上一些应用知识的实例。</p>
- [float和绝对定位比较](https://alexzhong22c.github.io/2017/03/04/float-n-absolute/)&nbsp;&nbsp;|&nbsp;&nbsp;2017-03-04&nbsp;&nbsp;|&nbsp;&nbsp;标签：[float](https://alexzhong22c.github.io/tags/float/) [绝对定位](https://alexzhong22c.github.io/tags/绝对定位/)
  - <p>因为float实现的效果和绝对定位比较类似，稍后会对它们进行比较。</p>
- [font-face--CSS3](https://alexzhong22c.github.io/2017/01/25/font-face/)&nbsp;&nbsp;|&nbsp;&nbsp;2017-01-25&nbsp;&nbsp;|&nbsp;&nbsp;标签：[CSS3](https://alexzhong22c.github.io/tags/CSS3/) [font-face](https://alexzhong22c.github.io/tags/font-face/) [字体](https://alexzhong22c.github.io/tags/字体/) [特殊](https://alexzhong22c.github.io/tags/特殊/)
  - <p><code>@font-face</code>是一个css命令，用来导入服务器端字体，将该字体文件存放到 web 服务器上，它会在需要时被自动下载到用户的计算机上。因此本地浏览器浏览网页时，不需要设置字体，就可以自动看到@font-face设置的任何字体。</p>
  - <p>如果你看到一些英文网站或blog看到一些很漂亮的自定义Web字体，比如说首页的Logo，Tags以及页面中的手写英文体，这些都是**@font-face**实现的。</p>

## ｜03 JavaScript 

- [面试题：改造代码，使之隔秒输出0 - 9](https://alexzhong22c.github.io/2020/04/02/settimeout-0-to-9/)&nbsp;&nbsp;|&nbsp;&nbsp;2020-04-02&nbsp;&nbsp;|&nbsp;&nbsp;标签：[面试题](https://alexzhong22c.github.io/tags/面试题/) [笔记副本](https://alexzhong22c.github.io/tags/笔记副本/) [回顾](https://alexzhong22c.github.io/tags/回顾/) [作用域](https://alexzhong22c.github.io/tags/作用域/) [闭包](https://alexzhong22c.github.io/tags/闭包/)
  - <p>通过一道面试题，文末总结一下js【变量快照】和【缓存变量值】的手法。原题考察的是对js作用域和对setTimeout api的理解，在本文主要给出5种解法。</p>
- [到底什么是函数式编程 精简总结](https://alexzhong22c.github.io/2018/02/05/js-functional-intro/)&nbsp;&nbsp;|&nbsp;&nbsp;2018-02-05&nbsp;&nbsp;|&nbsp;&nbsp;标签：[笔记副本](https://alexzhong22c.github.io/tags/笔记副本/) [回顾](https://alexzhong22c.github.io/tags/回顾/) [函数式编程](https://alexzhong22c.github.io/tags/函数式编程/)
  - <p>此文用于快速回顾，不适合用来入门。</p>
  - <p>到底什么是函数式编程？我将分别用一段话来总结其 特点 和 作用。</p>
- [对象属性的操作](https://alexzhong22c.github.io/2017/09/03/js-obj-prop1/)&nbsp;&nbsp;|&nbsp;&nbsp;2017-09-03&nbsp;&nbsp;|&nbsp;&nbsp;标签：[回顾](https://alexzhong22c.github.io/tags/回顾/) [对象属性](https://alexzhong22c.github.io/tags/对象属性/)
  - <p>类似于“增删改查”的基本操作，属性操作可分为属性查询、属性设置、属性删除，还包括属性继承。</p>
- [对象属性描述符](https://alexzhong22c.github.io/2017/09/02/js-obj-prop2/)&nbsp;&nbsp;|&nbsp;&nbsp;2017-09-02&nbsp;&nbsp;|&nbsp;&nbsp;标签：[回顾](https://alexzhong22c.github.io/tags/回顾/) [对象属性](https://alexzhong22c.github.io/tags/对象属性/)
  - <p>对于操作系统中的文件，我们可以驾轻就熟将其设置为只读、隐藏、系统文件或普通文件。</p>
  - <p>于对象来说，属性描述符提供类似的功能，用来描述对象的值、是否可配置、是否可修改以及是否可枚举。</p>
- [对象属性之对象状态](https://alexzhong22c.github.io/2017/09/01/js-obj-prop3/)&nbsp;&nbsp;|&nbsp;&nbsp;2017-09-01&nbsp;&nbsp;|&nbsp;&nbsp;标签：[回顾](https://alexzhong22c.github.io/tags/回顾/) [对象属性](https://alexzhong22c.github.io/tags/对象属性/)
  - <p>我们知道，属性描述符只能用来控制对象中一个属性的状态。而如果要控制对象的状态，就要用到下面的6种方法：</p>
- [es5实现继承的6种方式](https://alexzhong22c.github.io/2017/08/12/js-inherit/)&nbsp;&nbsp;|&nbsp;&nbsp;2017-08-12&nbsp;&nbsp;|&nbsp;&nbsp;标签：[面向对象](https://alexzhong22c.github.io/tags/面向对象/) [原型系统](https://alexzhong22c.github.io/tags/原型系统/) [原理](https://alexzhong22c.github.io/tags/原理/)
  - <p>对关于继承的内容做一番整理。</p>
- [new创建对象的过程发生了什么](https://alexzhong22c.github.io/2017/08/12/js-new-happen/)&nbsp;&nbsp;|&nbsp;&nbsp;2017-08-12&nbsp;&nbsp;|&nbsp;&nbsp;标签：[基础](https://alexzhong22c.github.io/tags/基础/) [面向对象](https://alexzhong22c.github.io/tags/面向对象/) [原型系统](https://alexzhong22c.github.io/tags/原型系统/)
  - <p>用面向对象语言们通用的观点来看：new 是用来实例化一个类，从而在内存中分配一个实例对象。</p>
- [原型对象 实战使用](https://alexzhong22c.github.io/2017/08/09/js-prototype-practice/)&nbsp;&nbsp;|&nbsp;&nbsp;2017-08-09&nbsp;&nbsp;|&nbsp;&nbsp;标签：[面向对象](https://alexzhong22c.github.io/tags/面向对象/) [原型系统](https://alexzhong22c.github.io/tags/原型系统/) [进阶](https://alexzhong22c.github.io/tags/进阶/)
  - <p>一般地，javascript使用构造函数和原型对象来进行面向对象编程，它们的表现与其他面向对象编程语言中的“类”相似而又不同。</p>
  - <p>在 <a href="https://alexzhong22c.github.io/2017/08/08/js-proto/">上一篇文章</a> 已经做过对 构造函数 和 原型对象 的简单介绍。在这篇文章主要介绍使用实战，你可不要小看“实战”，坑点还是挺多的。</p>
- [理解prototype、__proto__和constructor等关系](https://alexzhong22c.github.io/2017/08/08/js-proto/)&nbsp;&nbsp;|&nbsp;&nbsp;2017-08-08&nbsp;&nbsp;|&nbsp;&nbsp;标签：[面向对象](https://alexzhong22c.github.io/tags/面向对象/) [原型系统](https://alexzhong22c.github.io/tags/原型系统/) [进阶](https://alexzhong22c.github.io/tags/进阶/)
  - <p>理解对象和函数的prototype、__proto__和constructor等关系：</p>
- [this绑定的优先级](https://alexzhong22c.github.io/2017/08/07/js-this2/)&nbsp;&nbsp;|&nbsp;&nbsp;2017-08-07&nbsp;&nbsp;|&nbsp;&nbsp;标签：[进阶](https://alexzhong22c.github.io/tags/进阶/) [this](https://alexzhong22c.github.io/tags/this/) [new](https://alexzhong22c.github.io/tags/new/)
  - <p>上一篇文章详细介绍过 this的4种绑定规则，那如果在函数的调用位置上同时存在两种以上的绑定规则应该怎么办呢？本文将介绍this绑定的优先级：</p>
- [结合this的4种绑定规则 深入理解this指向的判定](https://alexzhong22c.github.io/2017/08/07/js-this/)&nbsp;&nbsp;|&nbsp;&nbsp;2017-08-07&nbsp;&nbsp;|&nbsp;&nbsp;标签：[IIFE](https://alexzhong22c.github.io/tags/IIFE/) [进阶](https://alexzhong22c.github.io/tags/进阶/) [this](https://alexzhong22c.github.io/tags/this/) [闭包](https://alexzhong22c.github.io/tags/闭包/)
  - <p>此文适合用于进阶对this的理解，不适合用来入门。</p>
- [let和const旧话新编](https://alexzhong22c.github.io/2017/05/08/let-n-const/)&nbsp;&nbsp;|&nbsp;&nbsp;2017-05-08&nbsp;&nbsp;|&nbsp;&nbsp;标签：[作用域](https://alexzhong22c.github.io/tags/作用域/) [ES6](https://alexzhong22c.github.io/tags/ES6/) [闭包](https://alexzhong22c.github.io/tags/闭包/) [任务队列](https://alexzhong22c.github.io/tags/任务队列/)
  - <p>本文的结构是：首先看完了前文就能快速把代码从ES5的变量声明改到ES6，后续部分是作为拓展和详细的介绍：</p>
- [JavaScript Date对象回顾](https://alexzhong22c.github.io/2017/05/07/js-date/)&nbsp;&nbsp;|&nbsp;&nbsp;2017-05-07&nbsp;&nbsp;|&nbsp;&nbsp;标签：[回顾](https://alexzhong22c.github.io/tags/回顾/) [时间](https://alexzhong22c.github.io/tags/时间/)
  - <p>此文用于快速回顾，不适合用来入门。</p>
  - <p>Date 对象：涉及基于1970年1月1日(世界标准时间)起的毫秒数。</p>
- [IIFE回顾](https://alexzhong22c.github.io/2017/03/10/iife-intro/)&nbsp;&nbsp;|&nbsp;&nbsp;2017-03-10&nbsp;&nbsp;|&nbsp;&nbsp;标签：[回顾](https://alexzhong22c.github.io/tags/回顾/) [IIFE](https://alexzhong22c.github.io/tags/IIFE/) [作用域](https://alexzhong22c.github.io/tags/作用域/) [单例](https://alexzhong22c.github.io/tags/单例/)
  - <p>此文用于快速回顾，不适合用来入门。</p>
- [js的for循环回顾](https://alexzhong22c.github.io/2017/03/09/for-loop/)&nbsp;&nbsp;|&nbsp;&nbsp;2017-03-09&nbsp;&nbsp;|&nbsp;&nbsp;标签：[回顾](https://alexzhong22c.github.io/tags/回顾/)
  - <p>非常经典，还分析了老的几个浏览器：<a href="http://www.zhangxinxu.com/wordpress/2013/04/es5%E6%96%B0%E5%A2%9E%E6%95%B0%E7%BB%84%E6%96%B9%E6%B3%95/" target="_blank" rel="noopener">es5新增数组方法和兼容性问题</a></p>
  - <p>ES5 中分别有三种 for 循环：</p>
  - <p>ES6 新增了for of</p>
  - <p>因为for循环和Array关系非常密切，所以先谈谈Array。</p>
- [相等操作符回顾](https://alexzhong22c.github.io/2017/02/11/equality-operators/)&nbsp;&nbsp;|&nbsp;&nbsp;2017-02-11&nbsp;&nbsp;|&nbsp;&nbsp;标签：[回顾](https://alexzhong22c.github.io/tags/回顾/) [操作符](https://alexzhong22c.github.io/tags/操作符/)
  - <p>最早的ECMAscript中的相等和不相等操作符会在执行比较之前，先将对象转换成相似的类型(即，强制转型)。</p>
  - <p>后来有人对这种转换的合理性提出质疑。</p>
  - <p>最后，ECMAcript的解决方案是提供两组操作符：</p>
- [操作符回顾](https://alexzhong22c.github.io/2017/02/11/js-operators/)&nbsp;&nbsp;|&nbsp;&nbsp;2017-02-11&nbsp;&nbsp;|&nbsp;&nbsp;标签：[回顾](https://alexzhong22c.github.io/tags/回顾/) [操作符](https://alexzhong22c.github.io/tags/操作符/)
  - <p>ECMAScript 操作符的与众不同之处在于，它们能适用于很多种基本数据类型的值，例如字符串、数字值、布尔值、甚至对象。</p>
  - <p>不过，在应用于对象时，响应的操作符通常都会调用对象的valueOf()和（或）toString()方法，以便取得可以操作的值。</p>
- [js函数基础回顾](https://alexzhong22c.github.io/2017/01/13/js-function/)&nbsp;&nbsp;|&nbsp;&nbsp;2017-01-13&nbsp;&nbsp;|&nbsp;&nbsp;标签：[回顾](https://alexzhong22c.github.io/tags/回顾/) [函数属性](https://alexzhong22c.github.io/tags/函数属性/)
  - <p>此文用于快速回顾，不适合用来入门。</p>

## ｜04 HTML 

- [H5新标签和被H5拥抱的老元素们](https://alexzhong22c.github.io/2017/03/28/h5-new-ele/)&nbsp;&nbsp;|&nbsp;&nbsp;2017-03-28&nbsp;&nbsp;|&nbsp;&nbsp;标签：[H5](https://alexzhong22c.github.io/tags/H5/)
  - <p>事实上，所有元素都能被归类为几个 元素内容模型（content model），详情请参考MDN：</p>
  - <p><a href="https://developer.mozilla.org/zh-CN/docs/Web/Guide/HTML/Content_categories" target="_blank" rel="noopener">https://developer.mozilla.org/zh-CN/docs/Web/Guide/HTML/Content_categories</a></p>
  - <p>这里不大谈内容模型，只不过按照这种思路划分我们的元素，谈谈那些比较广为接受的HTML5新元素和那些被HTML5拥抱的老元素。</p>
- [IFE2017-CSS-task01笔记](https://alexzhong22c.github.io/2017/03/27/ife-css-task01/)&nbsp;&nbsp;|&nbsp;&nbsp;2017-03-27&nbsp;&nbsp;|&nbsp;&nbsp;标签：[HTML](https://alexzhong22c.github.io/tags/HTML/) [H5](https://alexzhong22c.github.io/tags/H5/) [IFE](https://alexzhong22c.github.io/tags/IFE/)
  - <p>因为大家对html代码不是很重视，所以整理了一些容易忽略的问题并且对一些知识点作了梳理。</p>
  - <p>对应代码的github仓库的地址：<a href="https://github.com/AlexZhong22c/IFE-CSS-learning" target="_blank" rel="noopener">https://github.com/AlexZhong22c/IFE-CSS-learning</a></p>
  - <p>task01其实就是对HTML的学习，对应的代码其实就是task02的<a href="https://alexzhong22c.github.io/IFE-CSS-learning/task02.html">demo</a>的HTML部分。</p>
- [和margin有关的知识](https://alexzhong22c.github.io/2017/03/04/about-margin/)&nbsp;&nbsp;|&nbsp;&nbsp;2017-03-04&nbsp;&nbsp;|&nbsp;&nbsp;标签：[margin](https://alexzhong22c.github.io/tags/margin/) [bug](https://alexzhong22c.github.io/tags/bug/)
  - <p>总结一下和margin有关的基本知识，属于必须了解的范畴。</p>
- [桌面端和移动端图标的引入](https://alexzhong22c.github.io/2017/02/27/icon-usage/)&nbsp;&nbsp;|&nbsp;&nbsp;2017-02-27&nbsp;&nbsp;|&nbsp;&nbsp;标签：[图标](https://alexzhong22c.github.io/tags/图标/) [meta标签](https://alexzhong22c.github.io/tags/meta标签/) [link标签](https://alexzhong22c.github.io/tags/link标签/)
  - <p>本文翻译自<a href="https://bitsofco.de/all-about-favicons-and-touch-icons/" target="_blank" rel="noopener">All About Favicons-bitsofcode</a> ：</p>
  - <p>这星期我决定找到一些合适的方式来使用网站的favicon（另外还包括移动端的touch icon）。我想总结一下我自己的观点并且通过简明的语言来表述清楚：</p>

## ｜05 Vue 

- [Vue-lazyload 原理和使用 个人总结](https://alexzhong22c.github.io/2020/04/02/vue-lazyload-summary/)&nbsp;&nbsp;|&nbsp;&nbsp;2020-04-02&nbsp;&nbsp;|&nbsp;&nbsp;标签：[笔记副本](https://alexzhong22c.github.io/tags/笔记副本/) [回顾](https://alexzhong22c.github.io/tags/回顾/)
  - <p>Vue-lazyload 这个话题，可谓“前人之述备矣”。这里主要写写一些我认为比较重要的点，能够快速回顾这个“第三方组件”的原理和使用方法。</p>
- [纯vue实现checkbox父子联动](https://alexzhong22c.github.io/2017/05/07/vue-checkbox-table/)&nbsp;&nbsp;|&nbsp;&nbsp;2017-05-07&nbsp;&nbsp;|&nbsp;&nbsp;标签：[全选](https://alexzhong22c.github.io/tags/全选/) [复选框](https://alexzhong22c.github.io/tags/复选框/) [表格](https://alexzhong22c.github.io/tags/表格/) [插件](https://alexzhong22c.github.io/tags/插件/)
  - <p>对应代码的github仓库的地址：<a href="https://github.com/AlexZhong22c/vue-checkbox-table" target="_blank" rel="noopener">https://github.com/AlexZhong22c/vue-checkbox-table</a></p>
  - <p><a href="https://alexzhong22c.github.io/vue-checkbox-table/vue-checkbox-table.html">demo</a> (在线演示初次加载会有点慢，请稍等)</p>
  - <p>vue.js的出现，导致很多小插件的简单实现成为可能。</p>
  - <p>但是，正是由于<strong>vue的数据绑定</strong>使用起来耦合度太强，导致一些比较常规的插件的实现方式要稍微有所不同。</p>
- [经典vue单页路由入门全家桶](https://alexzhong22c.github.io/2017/04/25/vue-time-tracker/)&nbsp;&nbsp;|&nbsp;&nbsp;2017-04-25&nbsp;&nbsp;|&nbsp;&nbsp;标签：[express](https://alexzhong22c.github.io/tags/express/) [MongoDB](https://alexzhong22c.github.io/tags/MongoDB/) [vuex](https://alexzhong22c.github.io/tags/vuex/) [异步](https://alexzhong22c.github.io/tags/异步/)
  - <p>vue-cli + vue2 + vue-router + axios + vuex2 + express + mongoose</p>
  - <p>一个简单的ToDoList——经典vue单页路由入门全家桶，我在大神们demo的基础上不断地改进。</p>
  - <p>对应代码的github仓库的地址：<a href="https://github.com/AlexZhong22c/vue-time-tracker" target="_blank" rel="noopener">https://github.com/AlexZhong22c/vue-time-tracker</a></p>
- [按条目展示表格数据小插件](https://alexzhong22c.github.io/2017/04/15/vue-table-nav/)&nbsp;&nbsp;|&nbsp;&nbsp;2017-04-15&nbsp;&nbsp;|&nbsp;&nbsp;标签：[表格](https://alexzhong22c.github.io/tags/表格/) [插件](https://alexzhong22c.github.io/tags/插件/) [条目](https://alexzhong22c.github.io/tags/条目/)
  - <p>对应代码的github仓库的地址：<a href="https://github.com/AlexZhong22c/vue-table-nav" target="_blank" rel="noopener">https://github.com/AlexZhong22c/vue-table-nav</a></p>
  - <p><a href="https://alexzhong22c.github.io/vue-table-nav/vue-table-nav.html">demo</a> (在线演示初次加载会有点慢，请稍等)</p>

## ｜06 项目总结 

- [ToDo小应用完工总结](https://alexzhong22c.github.io/2017/02/17/todo-app/)&nbsp;&nbsp;|&nbsp;&nbsp;2017-02-17&nbsp;&nbsp;|&nbsp;&nbsp;标签：[App](https://alexzhong22c.github.io/tags/App/) [caller](https://alexzhong22c.github.io/tags/caller/) [优化](https://alexzhong22c.github.io/tags/优化/)
  - <p>完成了百度IFE2015的 <a href="https://github.com/baidu-ife/ife/tree/master/2015_spring/task/task0003" target="_blank" rel="noopener">task3</a> ，实现了一个 ToDo 的单页应用，功能颇为强大。</p>
  - <p>使用 localStorage 存储数据，JSON 模拟数据表，实现了分类和待办状态的改变，具有良好的交互体验。</p>
  - <p>repository地址：<a href="https://github.com/AlexZhong22c/ToDoApp-IFE2015" target="_blank" rel="noopener">https://github.com/AlexZhong22c/ToDoApp-IFE2015</a></p>
  - <p>在线预览地址：<a href="https://alexzhong22c.github.io/ToDoApp-IFE2015/">https://alexzhong22c.github.io/ToDoApp-IFE2015/</a></p>
  - <p>新增了 <a href="https://alexzhong22c.github.io/ToDo-WebApp/index.html">升级版</a> 修复了一些bug，并且适配移动端：<a href="https://github.com/AlexZhong22c/ToDo-WebApp" target="_blank" rel="noopener">https://github.com/AlexZhong22c/ToDo-WebApp</a></p>

## ｜07 移动端Web

- [移动开发事件入门概述](https://alexzhong22c.github.io/2017/02/25/webapp-events-intro/)&nbsp;&nbsp;|&nbsp;&nbsp;2017-02-25&nbsp;&nbsp;|&nbsp;&nbsp;标签：[随笔](https://alexzhong22c.github.io/tags/随笔/) [触摸事件](https://alexzhong22c.github.io/tags/触摸事件/) [指针事件](https://alexzhong22c.github.io/tags/指针事件/) [交互](https://alexzhong22c.github.io/tags/交互/)
  - <p>本文修改自<a href="http://www.infoq.com/cn/articles/touch-pointer-event" target="_blank" rel="noopener">PPK的《移动Web手册》</a></p>
- [移动开发入门概述](https://alexzhong22c.github.io/2017/02/24/webapp-intro/)&nbsp;&nbsp;|&nbsp;&nbsp;2017-02-24&nbsp;&nbsp;|&nbsp;&nbsp;标签：[随笔](https://alexzhong22c.github.io/tags/随笔/) [H5](https://alexzhong22c.github.io/tags/H5/)
  - <p><strong>PPK的《移动Web手册》</strong> 是对移动Web现状（2014年夏）的一个系统检阅，市场上有不少公司将赌注放在HTML5上，因此对于HTML5在移动Web上的应用多有炒作，但实际上如何呢？看完本书能让你有个清醒的认识。</p>
  - <p>移动浏览器虽然大都实现了桌面浏览器的功能，但实际上移动设备上的情况更加复杂，而且由于Android系统的碎片化直接导致浏览器的碎片化，它们对于一些和桌面不同情况的处理，以及一些最新特性的支持都是不尽相同的。</p>
  - <p><strong>所以HTML5在移动Web上的兼容性目前是很差的，</strong> 还有像触摸事件向指针事件标准化的过渡，估计最少需要5-10年才能达到一个比较理想的状态。</p>

## ｜08 hexo 

- [yelee主题改bug总结](https://alexzhong22c.github.io/2017/02/22/my-hexo-theme/)&nbsp;&nbsp;|&nbsp;&nbsp;2017-02-22&nbsp;&nbsp;|&nbsp;&nbsp;标签：[hexo](https://alexzhong22c.github.io/tags/hexo/) [yelee](https://alexzhong22c.github.io/tags/yelee/) [theme](https://alexzhong22c.github.io/tags/theme/)
  - <p>从找一个喜欢的hexo主题到修改好bug发布到博客上面，整个过程花了我不少时间，下面是对这个改bug过程中发现的小问题做的总结。</p>
  - <p>此文无图。</p>

## ｜09 随笔 

- [git暂存区知识梳理](https://alexzhong22c.github.io/2017/10/12/git-stage/)&nbsp;&nbsp;|&nbsp;&nbsp;2017-10-12&nbsp;&nbsp;|&nbsp;&nbsp;标签：[随笔](https://alexzhong22c.github.io/tags/随笔/) [git](https://alexzhong22c.github.io/tags/git/) [基础](https://alexzhong22c.github.io/tags/基础/) [指令](https://alexzhong22c.github.io/tags/指令/)
  - <p>暂存区是git的一个重要概念，经过了一段时间的项目实践，总结一下个人对暂存区的一些理解。</p>
  - <p>当我们开始对git的一些知识进行梳理的时候，可以盗用以下这张图：</p>

## ｜10 gulp 

- [gulp的入门和一些简单使用](https://alexzhong22c.github.io/2017/03/02/gulp-usage/)&nbsp;&nbsp;|&nbsp;&nbsp;2017-03-02&nbsp;&nbsp;|&nbsp;&nbsp;标签：[工程](https://alexzhong22c.github.io/tags/工程/)
  - <p>总结gulp的入门和一些简单使用，以便于快速上手。</p>
