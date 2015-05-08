title: "how to build a minecraft server with msm"
date: 2014-09-12 09:20:55
tags:
permalink: how-to-build-a-minecraft-server-with-msm
id: 54
updated: '2014-09-12 09:20:55'
---



[http://msmhq.com/](MSM)

###安裝

####Debian*(Ubuntu)
wget -q http://git.io/Sxpr9g -O /tmp/msm && bash /tmp/msm

####Redhat
wget -q http://git.io/lu0ULA -O /tmp/msm && bash /tmp/msm

###建立 Minecraft Server


```
sudo jargroup add craftbukkit-beta http://xxxxxx.xxxxx.xxxx.xxxx.xxxx.xxx/xxx/xxx
sudo msm server create bukkit-public
sudo msm bukkit-public jar craftbukkit-beta
sudo echo msm-version=craftbukkit/1.7.9 >> /opt/msm/servers/bukkit-public/server.properties
sudo msm bukkit-public start
```
