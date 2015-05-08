title: "Coffeescript note"
date: 2013-11-11 10:54:00
tags:
permalink: coffeescript-note
id: 31
updated: '2013-11-11 10:54:00'
---



首先要知道如何讓coffeescript監視檔案的變更然後重新編譯

`coffee -wc [path/*.coffee] -o [compiled/]`
 
但是如果要監視多個檔案，並且編譯到不同的資料夾該怎麼做呢？

在google了之後，找到兩個解法（還不知道是不是最好的）
1. 寫Cakefile
2. `coffee -o lib -c -w **/**.coffee`

Cakefile 怎麼寫看一下這邊[Cakefile](http://coffeescript.org/documentation/docs/cake.html)


`coffee -o lib -c -w **/**.coffee`

For example, I have following files:

    /controllers/users.coffee
    /models/user.coffee

Compiled as below

    /lib/controllers/users.js
    /lib/controllers/user.js

這樣不行，我要的是下面這樣

    /lib/controllers/users.js
    /lib/models/user.js

我知道了！

`coffee -cwo lib .`

神招

[來源](https://groups.google.com/forum/#!msg/coffeescript/-P-ODCaurEo/aSzNehKxP90J)
