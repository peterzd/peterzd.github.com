---
layout: post
title: "Ruby Expressions"
description: ""
category: ruby
tags: [ruby, program]
---
{% include JB/setup %}

### Literals and Keyword Literals

一些Keyword也是表达式，如`self`, `true, false`
`__FILE__` :返回Ruby解释器正在执行的文件，String类型
`__LINE__`：返回Integer类型，正在执行的文件的第几行
`__ENCODING__`：当前文件的编码

用`.`表示方法调用；`::`表示调用一个常量

### Variable References

未初始化的变量，有几种不同的情况：

* Class variables(@@): 在使用前必须给它赋一个值。否则会报`NameError`

* Instance(@): 返回`nil`，但不建议这么使用

* Global($)：与实例变量一样

* Local(以小写或\_开头)：Ruby解释器默认认为它是一个方法，然后去找，如果没有找到，会报`NameError`；如果给它赋过值，就把它当成一个变量

### Constant References
一般为大写，如：`LIKE_THIS`。类和Module的名字一般为：`LikeThis`，可以在程序的任何地方使用到，作用跟全局变量差不多

### Method Invocatinos
有四个部分：
* 在一个对象上调用 `.`，如果前面的省略，这个方法是在`self`上被调用的
* 调用的方法名，必须的
* 参数列表。可以用`()`包括，也可以不用。多个参数用`,`分割
* 可选的块。用`{}`或`do/end`来包括。这个传过来的值，在方法里用`yield`来使用

方法的最后一段执行代码就是这个方法的返回值

