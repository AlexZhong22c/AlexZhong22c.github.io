---
title:  eslint折腾记
date: 2017-03-11 21:50:31
categories: [essay]
tags: [eslint,配置,插件]
---

关于 eslint 这一个简单的工具的使用，本人目前仍在摸索。

<!--more-->

## 卸载干净

在同类型的 jslint 、jshint 、eslint 当中我选择了 eslint 。

为了简单起见，我先从 sublime 的 eslint 插件入手。

一开始我想着对自己要求严格一点，那就用 airbnb 版的 eslint 插件配置吧。

没想到：

- airbnb 对ES6的使用非常深入，这使得我如果不按照ES6来写的话会遭遇大量的错误，即便把要使用ES6的配置关闭，这个代码校正也让我无法承受
- 网上不建议初学者直接上手 ES6
- 最近做一个小项目，我的前端搭档要求 JavaScript 代码要兼容比较老的一些浏览器
- 用babel 可以将ES6转成ES5，但是最后是在你的工程中配置了babel

为了 airbnb 版，我安装了一堆npm插件，大概是卸载干净了。

最终，我只安装了[SublimeLinter](https://github.com/SublimeLinter/SublimeLinter3)和[SublimeLinter-contrib-eslint](https://github.com/roadhump/SublimeLinter-eslint) 和cssLint，xxxx。另外的这一篇 [《在Sublime3中使用ESLint》](http://www.tuicool.com/articles/faANRvj) 也值得一读。

## 私人配置

我用的是eslintrc.json文件来自定义配置，这样的一个好处是，可以通过

```
"extends": "standard",
```

引入 standar 版的 eslint 插件配置，作为我的配置的主题。然后它就像css 一样，写在文件后方的配置可以**覆盖**前方的同名配置，这样就可以私人订制一些个别的修改，经过了一个晚上的奋战，下面这些就是我私人添加的配置，仅供参考：

```
{
  "extends": "standard",					//引入大神的配置作为主体
  "globals": {
    "$": true,                                //zepto
    "define": true,                           //requirejs
    "require": true                           //requirejs
  },
  "env": {
    "browser": true                           //执行环境 浏览器
  },
  "rules": {
    //官方文档 http://eslint.org/docs/rules/
    "no-unused-vars": [1, { "vars": "all", "args": "none", "ignoreRestSiblings": true }],                 //变量定义后未使用
    "quotes": [1, "single", { "avoidEscape": true, "allowTemplateLiterals": true }],
    // "no-inner-declarations": [0, "both"],     //不建议在{}代码块内部声明变量或函数
    "no-extra-boolean-cast": 1,               //多余的感叹号转布尔型
    "no-extra-semi": 1,                       //多余的分号
    "no-extra-parens": 1,                     //多余的括号
    "no-empty": 1,                            //空代码块
    "no-use-before-define": [1, "nofunc"],    //使用前未定义
    "complexity": [1, 10],                    //圈复杂度大于10 警告
    "no-cond-assign": [2, "always"],          //条件语句中禁止赋值操作
    "no-native-reassign": 2,                  //禁止覆盖原生对象

    //代码风格优化
        "operator-linebreak": ["error", "before"],
    "no-else-return": 1,                      //在else代码块中return，else是多余的
    "no-multi-spaces": 1,                     //不允许多个空格
    "key-spacing": [1, {"beforeColon": false, "afterColon": true}],//object直接量建议写法 : 后一个空格前面不留空格
    "block-scoped-var": 2,                    //变量应在外部上下文中声明，不应在{}代码块中
    "consistent-return": 2,                   //函数返回值可能是不同类型

    "no-loop-func": 2,                        //禁止在循环体中定义函数
    "no-return-assign": [2, "always"],        //不允return时有赋值操作
    "no-redeclare": [2, {"builtinGlobals": true}],//不允许重复声明
    "no-unused-expressions": [2, {"allowShortCircuit": true, "allowTernary": true}],//不执行的表达式
    "no-useless-concat": 2,                   //无意义的string concat
    "no-void": 2,                             //禁用void
    "no-with": 1,                             //禁用with
    "valid-jsdoc": [2, {"requireParamDescription": true, "requireReturnDescription": true}],//jsdoc
    "no-warning-comments": [2, { "terms": ["todo", "fixme", "any other term"], "location": "anywhere" }],//标记未写注释
    "curly": 1                                //if、else、while、for代码块用{}包围
  }
}
```



## 

