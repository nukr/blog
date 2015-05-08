title: "zsh and tmux fixed window name"
date: 2014-10-01 15:16:20
tags:
permalink: zsh-and-tmux-fixed-window-name
id: 55
updated: '2014-10-01 15:16:20'
---



這是一個bug

只要你用了 tmux + oh-my-zsh ，tmux 下方的 window name 就會隨著你不斷地切換程式
而跳動，非常的煩，你沒辦法幫它命名，因為只要你命名後再切換程式，他馬上會變成你
正在使用的程式的名字。

如何解決

vi .zshrc

```DISABLE_AUTO_TITLE=true```
