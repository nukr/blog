title: "Vim在Tmux中會沒有colorscheme"
date: 2014-06-09 17:37:55
tags:
permalink: vimzai-tmuxzhong-hui-mei-you-colorscheme
id: 48
updated: '2014-06-09 17:37:55'
---


```bash
#To fix the issue, I have set up an alias in ~/.zshrc:
alias tmux=”TERM=screen-256color-bce tmux”

#And set up the default-terminal option in ~/.tmux.conf:
set -g default-terminal “screen-256color”
```
