---
layout: post
title: "Redis first"
description: "touch Redis"
category: redis
tags: []
---
{% include JB/setup %}

> 一种K_V的数据库，NoSql类似的数据库。[官网](http://redis.io/), [下载](http://redis.io/download)

## Redis 下载，安装，启Server

官网给出的安装过程：

```
$ wget http://redis.googlecode.com/files/redis-2.6.14.tar.gz
$ tar xzf redis-2.6.14.tar.gz
$ cd redis-2.6.14
$ make
```

运行Server：
```
$ src/redis-server
```

交互：
```
$ src/redis-cli
```

## 基本操作
* `SET connections 10`: 设置值，key是connections， value是10
* `GET connections`：取值，返回 10
* `DEL connections`：删掉这个Key和对应的Value
* `INCR connections`：返回11, 自动增长(*increment*),好处是支持多用户操作，不会产生脏数据

* `EXPIRE resource:lock 120`：设置过期时间为120秒，可以用`TTL`来查看还有多少时间过期，-1 表示不会过期。重新SET值之后，过期时间也变为-1

### Data structures
#### List
支持Key为List的数据类型，一些重要的命令为：`RPUSH`, `LPUSH`, `LLEN`, `LRANGE`, `LPOP`, `RPOP`
* `RPUSH friends "tom"`：在List_最后_加上新值
* `LPUSH friends "sam"`：在_最前_加上新值
* `LRANGE friends 0 1`：从第几个到第几个值。-1表示全部
* `LLEN`：返回长度
* `LPOP`：移除第一个值，并返回它
* `RPOP`：最后一个值

#### Set
主要命令有：`SADD`, `SREM`, `SISMEMBER`, `SMEMBERS`, `SUNION`
* `SUNION super bird`：把两个Set合并到一起，并返回所有的元素

#### Sorted Set

```
ZADD hackers 1940 "Alan Kay"
ZADD hackers 1953 "Richard Stallman"
ZADD hackers 1965 "Yukihiro Matsumoto"
ZADD hackers 1916 "Claude Shannon"
ZADD hackers 1969 "Linus Torvalds"
ZADD hackers 1912 "Alan Turing"

ZRANGE hackers 2 4 => ["Alan Kay","Richard Stallman","Yukihiro Matsumoto"]
```

会自动根据时间进行排序


