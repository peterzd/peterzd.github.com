---
layout: post
title: "Hello Ruby"
description: ""
category: ruby
tags: [ruby programmer]
---
{% include JB/setup %}

Introduction & Structures

```ruby
3.times { puts "good day" }
```
## Lexical Structure
Ruby has a sequence of **tokens**, include *comments*, *literals*, *punctuation(标点符号)*, *identifiers* and *keywords*

Comments
--------
Common way: Begin with "#"
Multiline comment: **_=begin_**, **_=end_** at the very beginning on the line

Literals
--------
Include numbers, strings of text, and regular expressions. Examples:
/three/ # A regular expression literal

Identifiers
-----------
To name variables, methods, classes and so on. Consist of _letters_, _numbers_, and _underscore characters_, CAN NOT begin with a number
Multiword constants are written **LikeThis** or **LIKE_THIS**

Special punctuation in identifiers:

* $ : Global varibales
* @ : Instance varibales
* @@ : Class varibales
* ? : methods that return Boolean values
* ! : methods should be used carefully

Keywords
--------
![ruby keywords](/images/ruby_keywords.png)

Block Structure
---------------
有两种Block，

* 一种是通常说的“Block”，用 **{}**，或者 **do end** 来包括, 如:

```ruby
2.times { print "Ruby!"}

1.upto(10) do |x|
  print x
end
```
* 另一种叫作 **body**,一般用 **Class, Module, def** 来表示

File Structure
--------------
```
#!/usr/bin/ruby -w 						*shebang comment*
# -*- coding: utf-8 -*-					*coding comment*
require 'socket'						*load networking library*

... 									*program code goes here*
__END__ 							  *mark end of code*
... 									*program data goes here*
```
如果有Unix-like的命令，则放在第一行，如果有有编码的注释，放在第二行，如果遇到 _END_，则文件结束

Program Execution
-----------------

* 一行一行执行，从上到下，没有*main*方法, 从最上一行开始(实际上没不是这样，其实是从**BEGIN**开始，找到它里的第一行再去执行的)
* 另一个跟Java之类不同的是它的 **Module**, **Class** 和**方法定义**,Ruby里，它们都是单纯的表达式。
