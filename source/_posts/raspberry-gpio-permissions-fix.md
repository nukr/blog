title: "raspberry gpio permissions fix"
date: 2013-03-05 22:42:00
tags:
permalink: raspberry-gpio-permissions-fix
id: 16
updated: '2013-03-05 22:42:00'
---



`sudo nano /etc/rc.local`

`chgrp -R dialout /sys/class/gpio`

`chmod -R g+rw /sys/class/gpio`

then reboot

結果好像沒用fuck

直接sudo -s搞定

2013年 3月 6日 周三 01時32分52秒 CST 後記：

還是要用[gpio-admin](https://github.com/quick2wire/quick2wire-gpio-admin)，比較安全，root太危險了

