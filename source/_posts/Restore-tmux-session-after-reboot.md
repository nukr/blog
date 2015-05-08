title: "Restore tmux session after reboot"
date: 2014-06-15 14:41:35
tags:
permalink: restore-tmux-session-after-reboot
id: 52
updated: '2014-06-15 14:41:35'
---



```bash
#!/bin/zsh

SESSIONNAME="script"
tmux has-session -t $SESSIONNAME &> /dev/null

if [ $? != 0 ]
then
    tmux new-session -s $SESSIONNAME -n script -d
    tmux send-keys -t $SESSIONNAME "~/bin/script" C-m
fi

tmux attach -t $SESSIONNAME
```
