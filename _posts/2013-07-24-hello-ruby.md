---
layout: post
title: "Hello Ruby"
description: ""
category: ruby
tags: [ruby programmer]
---
{% include JB/setup %}

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
