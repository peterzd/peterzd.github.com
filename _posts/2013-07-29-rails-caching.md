---
layout: post
title: "Rails caching"
description: ""
category: rails
tags: [rails, cache]
---
{% include JB/setup %}

查看[官方的文档](http://guides.rubyonrails.org/caching_with_rails.html)，做个记录

## Basic Caching
有三种基本的Caching：**page**, **action**和**fragment**, 默认使用Fragment，如果要使用另两个，需要加gemfile: actionpack-page_caching, actionpack-action_caching
如果要在Dev和Test中使用Caching，要在 config/environments/\*.rb里设置`config.action_controller.perform_caching = true`

### Fragment Caching

