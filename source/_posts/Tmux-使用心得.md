title: "Tmux 使用心得"
date: 2013-11-10 01:03:00
tags:
permalink: tmux-experience
id: 30
updated: '2013-11-10 01:03:00'
---



Tmux在MacOSX上的modify key預設是`ctrl + b`，底下的指令皆為加上`ctrl + b`

其實只要在tmux裡面`ctrl + b -> ?`，就會列出所有shortcut

    s 列出sessions
    $ 命名session

### Window(tab)

    c 新視窗
    , 命名視窗
    w 列出清單
    f 尋找視窗
    & 關閉視窗
    . 更改視窗編號
    :movew<CR>  move window to the next unused number

### Panes

    % 水平分割
    " 垂直分割

    o 交換窗格
    q 顯示窗格編號
    x 關閉窗格
    ⍽ space - toggle between layouts"

### Window/pane surgery

    :joinp -s :2<CR>  move window 2 into a new pane in the current window
    :joinp -t :1<CR>  move the current pane into a new pane in window 1
[Move window to pane](http://unix.stackexchange.com/questions/14300/tmux-move-window-to-pane)
[How to reorder windows](http://superuser.com/questions/343572/tmux-how-do-i-reorder-my-windows)

### Misc

    d  detach
    t  big clock
    ?  list shortcuts
    :  prompt
