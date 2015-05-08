title: "透過rsync+ssh deploy nodejs到遠端server，以及MongoDB的備份與還原"
date: 2012-10-26 11:09:00
tags:
permalink: depoly-nodejs-from-local-by-rsync-plus-ssh-and-mongodb-backup-and-restore
id: 4
updated: '2012-10-26 11:09:00'
---


為什麼要用rsync+ssh？

因為他最快，可以一鍵搞定，又可以在command line底下做

<!-- more -->

為什麼要把那麼多東西擠在同一篇？

因為一次的部署(deploy)就是做這些事情，拆開就還要跑兩篇文章去查看，雖然多了點，但還是這樣比較方便。server端只要有sshd在跑即可，沒記錯的話`apt-get install ssh-server`就好client的話我假設你有bash，用windows的就抱歉了，不然你也可以去抓win-bash，還要有ssh-client。

[參考網站](http://kawsing.blogspot.tw/2011/05/ssh-rsync.html)  
[參考網站](http://www.andowson.com/posts/list/191.page)

先來無斷轉載MongoDB Backup and Restore

mongodb的備份與還原
mongodb提供了兩個命令來備份（mongodump ）和還原（mongorestore ）資料庫

1.备份（mongodump ）

用法 ：
root@web3 3# mongodump --help
options:
--help                   produce help message
-v  --verbose          be more verbose (include multiple times for more 
verbosity e.g. -vvvvv)
-h  --host  arg        mongo host to connect to ("left,right" for pairs)
-d  --db  arg          database to use
-c  --collection  arg  collection to use (some commands)
-u  --username  arg    username
-p  --password  arg    password
--dbpath arg             directly access mongod data files in the given path,
instead of connecting to a mongod instance - needs 
to lock the data directory, so cannot be used if a 
mongod is currently accessing the same path
--directoryperdb         if dbpath specified, each db is in a separate 
directory
-o  --out  arg (=dump) output directory

例子：

root@web3 ~# mongodump -h 192.168.1.103 -d citys -o /backup/mongobak/3  
connected to: 192.168.1.103  
DATABASE: citys  to     /backup/mongobak/3/citys  
citys.building to /backup/mongobak/3/citys/building.bson  
13650 objects  
citys.system.indexes to /backup/mongobak/3/citys/system.indexes.bson  
1 objects  

备份出来的数据是二进制的，已经经过压缩。比实际数据库要小很多，我的数据库显示占用了260多M，备份后只有2M。

2.恢复（mongorestore ）

用法：
root@web3 3# mongorestore --help
usage: mongorestore options directory or filename to restore from
options:
--help                  produce help message
-v  --verbose         be more verbose (include multiple times for more 
verbosity e.g. -vvvvv)
-h  --host  arg       mongo host to connect to ("left,right" for pairs)
-d  --db  arg         database to use
-c  --collection  arg collection to use (some commands)
-u  --username  arg   username
-p  --password  arg   password
--dbpath arg            directly access mongod data files in the given path, 
instead of connecting to a mongod instance - needs to
lock the data directory, so cannot be used if a 
mongod is currently accessing the same path
--directoryperdb        if dbpath specified, each db is in a separate 
directory
--drop                  drop each collection before import
--objcheck              validate object before inserting

--drop参数可以在导入之前把collection先删掉。

例子：

root@web3 3# mongorestore -h 127.0.0.1 --directoryperdb /backup/mongobak/3/
connected to: 127.0.0.1
/backup/mongobak/3/citys/building.bson
going into namespace citys.building
13667 objects
/backup/mongobak/3/citys/system.indexes.bson
going into namespace citys.system.indexes
1 objects

另外mongodb还提供了mongoexport 和 mongoimport 这两个命令来导出或导入数据，导出的数据是json格式的。也可以实现备份和恢复的功能。
例：
mongoexport -d mixi_top_city_prod -c building_45 -q '{ "uid" : "10832545" }' > mongo_10832545.bson
mongoimport -d mixi_top_city -c building_45 --file mongo_10832545.bson
