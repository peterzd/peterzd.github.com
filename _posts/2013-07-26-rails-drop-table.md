---
layout: post
title: "Rails drop table"
description: ""
category: rails
tags: [technique, note]
---
{% include JB/setup %}

在 `db/migrate`目录里，如果想要drop一个表，在写migration时要注意防止这个表不存在的情况
在[这篇博客](http://coryforsyth.com/2008/03/27/checking-table-existence-in-rails-migrations/)里找到方法，实践可行，记录如下：

```ruby
class DropJoinExpertTable < ActiveRecord::Migration
	def up
		drop_table :join_experts if self.table_exists?("join_experts")
	end

	def down
		raise ActiveRecord::IrreversibleMigration
	end
end
```
`if self.table_exists?("join_experts")`对是否存在进行判断
