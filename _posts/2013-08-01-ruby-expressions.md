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
P89
