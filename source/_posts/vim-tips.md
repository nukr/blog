title: vim tips
date: 2016-08-04 11:41:14
tags: [vim]
---

我想要重新調整文章的格式讓我整篇文章都在 80 行換行，且要考慮到 word 的完整性
[source](http://stackoverflow.com/questions/3033423/vim-command-to-restructure-force-text-to-80-columns)

首先 `set textwidth=80` 選擇我們要的寬度

再來 `gqG` 就會 format 整篇文章
