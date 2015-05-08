title: "Fix vim indent"
date: 2013-12-29 13:25:20
tags:
permalink: fix-vim-indent
id: 37
updated: '2013-12-29 13:25:20'
---



```
:set ts=2 sts=2 noet
:retab!
```

This changes every 2 spaces to a TAB character, then:

```
:set ts=4 sts=4 et
:retab
```
