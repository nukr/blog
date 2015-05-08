title: "How to monitor dd progress in Mac OSX"
date: 2015-04-27 00:37:28
tags:
permalink: how-to-monitor-dd-progress
id: 66
updated: '2015-04-27 01:07:58'
---

```bash
brew install pv
sudo dd /dev/urandom | pv | sudo dd of=/dev/null
```

輸出

```bash
1,74MB 0:00:09 [ 198kB/s] [      <=>                            ]
```

也可以這樣用
```bash
pv /home/user/bigfile.iso | md5sum
```