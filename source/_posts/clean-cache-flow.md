title: clean cache flow
date: 2015-07-24 15:15:24
tags:
---

客戶取得資料的方法有2

get

這種方式是 get by id 一定只會取出一筆資料


getAll

這種方式有可能一個 query 會跨多個 table

清 cache 的機會有三個

create

新增一筆資料，不管如何都是一筆一筆，even 是 batch 的，所以清 cache 的方式也很單純，清掉所有 affect 到的 table

update

更新一筆

更新多筆

delete

刪除一筆

刪除多筆
