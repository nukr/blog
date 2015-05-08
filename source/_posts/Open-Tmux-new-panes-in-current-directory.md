title: "Open Tmux new panes in current directory"
date: 2014-03-20 12:50:16
tags:
permalink: open-tmux-new-panes-in-current-directory
id: 45
updated: '2014-03-20 12:50:16'
---



```bash .tmux.conf
bind c neww -c '#{pane_current_path}'
bind % split-window -h -c "#{pane_current_path}"
bind '"' split-window -c "#{pane_current_path}"
```
