title: "Setup Octopress for Mac OS X"
date: 2012-10-26 01:16:00
tags:
permalink: setup-octopress-for-mac-os-x
id: 6
updated: '2012-10-26 01:16:00'
---


要裝Octopress，首先要先把ruby裝好，先看一下Octopress的官網的Setup部分他會說明ruby需求的版本
[Link](http://octopress.org/docs/setup/)
<!-- more -->
細節部分可以看[這篇](http://www.moncefbelyamani.com/how-to-install-xcode-homebrew-git-rvm-ruby-on-mac/)
在Ubuntu下無法安裝Ruby1.9.3可以看[這篇][http://stackoverflow.com/questions/9056008/installed-ruby-1-9-3-with-rvm-but-command-line-doesnt-show-ruby-v/9056395#9056395]


接下來當然是要裝Ruby了，我寫這邊文章的時候是1.9.3，我用的機器是2011 mid Macbook Air 13"，OS是Lion我的git是內建的所以不用裝，如果你沒有git的話要先裝起來，裝ruby可以透過rbenv或是RVM，因為我的系統rbenv裝起來沒辦法用，所以我只能用RVM
    curl -L https://get.rvm.io | bash -s stable --ruby
只要這樣就好了，連ruby1.9.3都裝好了
簡單到爆！
