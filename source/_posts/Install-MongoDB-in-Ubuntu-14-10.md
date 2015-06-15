title: "Install MongoDB in Ubuntu 14.10"
date: 2015-06-13 09:24:02
tags:
---
```bash
$ sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 7F0CEB10
$ echo "deb http://repo.mongodb.org/apt/ubuntu "$(lsb_release -sc)"/mongodb-org/3.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb.list
$ sudo apt-get update
$ sudo apt-get install mongodb-org
$ sudo service mongod start
$ sudo service mongod stop
```

