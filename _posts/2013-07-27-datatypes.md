---
layout: post
title: "Datatypes"
description: ""
category: ruby
tags: [ruby, program]
---
{% include JB/setup %}

## Numbers
  * 有类型如： Integer, Float，BigDecimal。Integer下有Fixnum，Bignum

### Integer
  * 可以用`_`来分割，只能用在数字中间。以_0_开头的是8进制，_ob_开头的是二进制，_ox_开头是16进制

### Arithmetic
  * 用\*\*来表示平方，4\*\*3\*\*2生成的是4\*\*9
  * 使用IEEE-754的语言，包括C，Java，Ruby，在进行浮点运算时都会有出现估值错误。如

```ruby
0.4 - 0.3 == 0.1  # false
```

## Text
### String

* String是可变的，提供了很多操作内容的方法
* 定义：
  * 'this is a string'
	* "\tThis is the #{1 + 1} string"
	* 如果觉得用 ''，或""不方便，也可以使用 `%q`(允许有''出现), `%Q`(或者是%，可以有""出现)来表示。

	```ruby
	%q(Don't worry about escaping ' characters!)
	%Q|"How are you?", he said|
	```

	* Here Document：如果一段文字比较长，可以用_任意字符_作为delimiter，如：

	```ruby
	document = <<HERE
	xxxx
	HERE
	```

	* \`\`，调用系统命令，也可以使用`%x[ls]`来代替。\`实际上是Kernel里的方法
	* Ruby里的String，每次都会给它一个新的object\_id，所以相同的两个String不是同一个对象

#### Substring
* s = "hello"
  * `s[0, 2] # "he"`, 从哪个开始，取几个
	* `s[2..3] # "ll"`, 用Range来取值

## Arrays
 * 可以用 ` %w[this is a test]`来表示一个Array
 * 可以往后面加元素，但不能往第一个前面加元素
 * `-`操作符，提取两个Array间不同的元素，返回一个新的Array
 * `a = [0] * 8  # [0, 0, 0, 0, 0, 0, 0, 0, 0]`

## Hash
`numbers = { one: 1, two: 2, three: 3}`, 是用**Hash Table**来表示的。
如果一个类override了 `eql?`方法，也要重写一下`hash`方法。

## Ranges
`1..10`: 从1到10，包括10
`1.0...10.0`：不包括10.0

## Symbols
以一个`:`开头。也可以用`%s[]`来表示
String to Symbol: `to_sym`
Symbol to String: `to_s`

## True, False, Nil
都是对象，对应为`TrueClass`, `FalseClass`, `NilClass`

## Objects


