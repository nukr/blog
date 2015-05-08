title: "nodejs with raspberry pi gpio development"
date: 2013-03-06 01:02:00
tags:
permalink: nodejs-with-raspberry-pi-gpio-development
id: 17
updated: '2013-03-06 01:02:00'
---


### GPIO是什麼?

GPIO = General Purpose Input/Output

其實看英文就大概能瞭解了，簡單來說GPIO就是一組針腳，可以讓你用來輸出輸入訊號給Raspberry Pi，進而可以讓你開發一些軟體for周邊的裝置關於Raspberry Pi的GPIO看[這裡](http://elinux.org/RPi_Low-level_peripherals)最準，裡面有接腳的定義。

### 如何控制GPIO

最低階的做法系統灌好就能用：

`sudo -s`

    這很危險，請小心，這指令會讓你變root

`echo "23" > /sys/class/gpio/export`

    這指令會開啓這個port，你就可以開始控制這個port

`echo "out" > /sys/class/gpio/gpio23/direction`

    GPIO的方向，是想要讀入或是輸出

`echo "1" > /sys/class/gpio/gpio23/value`

    將gpio23(pin16)，設成高電位，按照此範例，你將LED的正極接上gpio23(pin16)，負極接上GND，就會亮了

但是這方法很危險(要用到root)，可以用抓[gpio-admin](https://github.com/quick2wire/quick2wire-gpio-admin)解決這問題
