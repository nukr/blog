title: "Redis Install and basics"
date: 2013-11-11 17:41:00
tags:
permalink: redis-install
id: 32
updated: '2013-11-11 17:41:00'
---



剛剛用brew install redis 後出現了以下訊息，覺得有必要記錄一下

    To have launchd start redis at login:
        ln -sfv /usr/local/opt/redis/*.plist ~/Library/LaunchAgents
    Then to load redis now:
        launchctl load ~/Library/LaunchAgents/homebrew.mxcl.redis.plist
    Or, if you don't want/need launchctl, you can just run:
        redis-server /usr/local/etc/redis.conf

再來裝個redis-commander

`npm install -g redis-commander`

接著run

`redis-commander`

專案裡面這樣裝

`npm install redis`

redis command line 這樣開

`redis-cli`

在cli run 一些簡單的指令

```
set
get
lpush
rpush
lrange
rrange
incr
incrby
sadd
smember
```
