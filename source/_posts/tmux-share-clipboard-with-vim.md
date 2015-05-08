title: "tmux share clipboard with vim"
date: 2014-02-05 16:41:39
tags:
permalink: tmux-share-clipboard-with-vim
id: 40
updated: '2014-02-05 16:41:39'
---



# Vim與Tmux共享剪貼簿

緣起：我的習慣是在terminal瀏覽檔案，看到想編輯的檔案就用mvim去開啟檔案，但是當
我換到Tmux之後就遇到麻煩了，tmux的clipboard好像是獨立的，所以我在比如說網頁上複
製一段文字，就無法貼上在tmux中開啟的vim。

解決方法：`brew install reattach-to-user-namespace`

原理：please google reattach-to-user-namespace
