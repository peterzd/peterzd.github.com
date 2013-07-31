---
layout: post
title: "Ruby Object"
description: ""
category: ruby
tags: [ruby, program]
---
{% include JB/setup %}

> Ruby 是纯粹的面向对象，所有的类都继承自`BasicObject`

### Object References
`immediate values`与`references`不同点在于，它们没有**Singleton**方法

### Lifetime
用 `myClass.new`方法来构建一个新的Instance，之后会调用`initialize`方法进行初始化。还有其他的*factory methods*可以返回Instance

Ruby也有**Garbage Collection**机制，当对象变得*unreachable*时，就会被自动回收

### Object Identity
有一个`object_id`方法，可以查到每个Object的id。
`__id__`是`object_id`的同义词

### Object Class and Type

```ruby
o = 'test'
o.class    # String。返回的是o的Class
```

`o.class.superclass`：可以查o的父类
在Ruby1.9里，**BasicObject**才是最终的父类，而不再是**Object**

`o.instance_of? String`：返回Boolean型，判断是否是String的实例
`is_a?`：可以查是不是某个祖类的子孙类。
`o.respond_to? :"<<"`：如果有这个方法，则返回True

### 对象相等性(Equality)
有几种不同的方法，要注意区分

* `equal?`：比较的是*object_id*

```ruby
a = "Ruby"
b = c = "Ruby"
a.equal?(b)  # false
b.equal?(a)  # true
```

* `==`：很多情况下等同于 `equal?`，但很多类里的这个方法使用得更字面化，如：

```ruby
a = "Ruby"
b = "Ruby"
a.equal?(b) # false
a == b # true
```

* `eql?`：会比较类型，两个Hash在比较时就会调用这个方法对里面的Keys进行比较

```ruby
1 == 1.0 # true
1.eql?(1.0) # false
```
* `===`：叫作"case equality"，测试一个**case**表达式是否匹配这个**when**闭包, 有些类对它的实现不太一样：

```ruby
(1..10) === 5 # true: 5 is in the range 1..10
/\d+/ === "123" # true: the string matches the regular expression
String === "s" # true: "s" is an instance of the class String
:s === "s" # true in Ruby 1.9
```

* `=~`：定义在**String**，**Regexp**中，模式匹配。

### 对象转换

* 显式转换： `to_s`, `to_i`, `to_f`, `to_a`, 变化为String，Integer，Float和Array

* 隐式转换：把一个对象转换成一个String-like，或是Array-like的形式。不太常用。

* boolean: 只有**true**, **false**转换成String，没有其他转换成Boolean形式的方法。在一个Boolean表达式里，除了*false*和*nil*之外，其他的都表现得像*true*，0,0.0, 空字符串都表现为*true*

### Marshaling Objects
可以保存一个对象的状态。通过使用`Marshal.dump`，调出状态的方法：`Marshal.load`，通过这种方式可以实现深copy

```ruby
def deepcopy(o)
	Marshal.load(Marshal.dump(o))
end
```

YAML是另一种保存状态的方式。在Standard Library里有，可以通过`require 'yaml'`来使用

### Tainting Objects
一个对象可以给它标记为`.taint`，用来表示这个对象是不安全，不可靠的。可以用 `.tainted?`来判断，用`.untaint`来解除
