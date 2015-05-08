title: "如何用Node.js和github來建立一個新專案"
date: 2012-10-26 18:09:00
tags:
permalink: how-to-start-a-new-project-with-nodejs-and-github
id: 5
updated: '2012-10-26 18:09:00'
---


要使用node.js必須先建立它的開發環境，[下載Node.js](http://nodejs.org/download/)之後把它安裝起來，你在你的command line裡面打node -v應該就會出現版本號了，node.js就這樣裝好了。

node.js有內建套件管理系統[npm](https://npmjs.org/)，你可以利用npm安裝各式各樣的前人開發的node.js外掛

接下來要選擇framework，現在node.js上最多人用的[MVC](http://zh.wikipedia.org/wiki/MVC) framework就是express，node.js的套件都是經由npm安裝的，安裝的方法如下：

`npm install express -g`
