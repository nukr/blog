title: "Install MariaDB"
date: 2013-07-13 03:10:00
tags:
permalink: install-mariadb
id: 28
updated: '2013-07-13 03:10:00'
---



## MariaDB in OS X Lion

```bash
brew update
brew install mariadb

#Set up databases with:
unset TMPDIR
mysql_install_db --user=`whoami` --basedir="$(brew --prefix mariadb)" --datadir=/usr/local/var/mysql --tmpdir=/tmp

#To have launchd start mariadb at login:
ln -sfv /usr/local/opt/mariadb/*.plist ~/Library/LaunchAgents

#Then to load mariadb now:
launchctl load ~/Library/LaunchAgents/homebrew.mxcl.mariadb.plist

#Or, if you don't want/need launchctl, you can just run:
mysql.server start
```

## MariaDB in Linux (Ubuntu 13.04 "raring")

[MariaDB repositories](https://downloads.mariadb.org/mariadb/repositories/)

```bash
#Here are the commands to run to add MariaDB to your Ubuntu system:

sudo apt-get install software-properties-common
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0xcbcb082a1bb943db
sudo add-apt-repository 'deb http://ftp.yz.yamagata-u.ac.jp/pub/dbms/mariadb/repo/10.0/ubuntu raring main'

#Once the key is imported and the repository added you can install MariaDB with:

sudo apt-get update
sudo apt-get install mariadb-server
```
