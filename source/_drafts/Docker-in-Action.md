title: "Docker in Action"
tags:
permalink: docker-in-action
id: 59
updated: '2015-01-20 13:50:38'
---

```
build
images
ps -a
rm
rmi
run -t -i
```
可能會遇到的問題

* image 刪不掉：可以跑一下 `sudo docker ps -a`，用 `sudo docker rm <containerId>`，再回去刪除原來刪不掉的 image 應該就可以成功了
* run 沒 -t -i 之後要 start 就沒tty