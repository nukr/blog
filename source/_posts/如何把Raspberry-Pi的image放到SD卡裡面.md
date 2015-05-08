title: "如何把Raspberry Pi的image放到SD卡裡面"
date: 2013-03-04 22:13:00
tags:
permalink: how-to-putting-raspberry-pi-image-into-sd-card
id: 14
updated: '2013-03-04 22:13:00'
---



首先要先下載Raspberry Pi的image[官方網站](raspberrypi.com.tw)中的[相關資源](http://www.raspberrypi.com.tw/resources/)裡面就有一堆了，但是載下來都是img檔怎麼辦呢？你可以參考[elinux.org的Easy SD Card Setup](http://elinux.org/RPi_Easy_SD_Card_Setup)，英文的看不懂，沒關係就讓我們繼續看下去。。。

### Mac版

本範例是在OSX 10.7下測試的，應該以上都可以，以下的版本我就不知道了，而且操作的時候請小心，因為我們會用到dd指令，操作錯誤可能會使得電腦上的資料完全消失。

1. 下載img

前面有給載點了，這邊不贅述，本範例用的是[Raspbian "wheezy"](http://downloads.raspberrypi.org/images/raspbian/2013-02-09-wheezy-raspbian/2013-02-09-wheezy-raspbian.zip)，提醒一點，Raspberry Pi是ARM base的板子，所以不支援x86的作業系統，所以不用去找WindowsXP for Raspberry Pi了，抓下來就解壓縮得到.img檔。

2. 插入SD卡
3. 格式化
4. 退出磁碟
5. 開始DD
6. wait for a long time
7. Done!
