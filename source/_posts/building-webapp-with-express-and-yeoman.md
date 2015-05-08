title: "building webapp with express and yeoman"
date: 2013-07-07 16:42:00
tags:
permalink: building-webapp-with-express-and-yeoman
id: 27
updated: '2013-07-07 16:42:00'
---



[Yeoman]: http://yeoman.io
[Google]: http://www.google.com

開始之前先說一下我想達成的目標，簡單來說就是`yo something`，`grunt`。搞定！

`yo`要幫我scaffold 的有

1. expressjs
2. angularjs
3. test/e2e
4. test/unit

[Yeoman]()真的是太酷了！配上Express要怎麼做呢？讓我們step by step

[Yeoman]()首先我們要了解它是什麼？

[Yeoman]()是由三個套件組成的，分別是：

* yo
* grunt
* bower

由[Google]()帶領的開放原始碼專案。

[Yeoman]()主要想達成的是，自動化專案模板，舉例來說你在指令列下`yo webapp`他就會幫你把所有你需要的檔案產生出來，像是`.gitignore`，`test/`，然後再下`grunt server`，他會幫你watch sass，*.coffee，還有live-reload等等，整個專案只要你設定好之後，就只要下這兩個指令。

##設定還是最困難的

前面說的是個大概，我試著把它條列出來。

yo是個scaffold tool，用來建立專案的架構，靠得是generator，npm上面已經有許多generator了，你可以下載你需要的generator，例如`npm install -g generator-angular`，之後就可以用`yo angular`去建立專案，裡面就會有你需要用來建構angular專案所需的一切，當然像我這種自定魂，一定要建立自己的generator囉！

需要`yo`幫我建立的資料夾與檔案有：

* views/
* views/layout.jade
* views/index.jade
* models/
* controllers/
* controllers/index.js
* public/
* public/components/
* public/sass/
* public/stylesheets/
* public/javascripts/
* test/
* .gitignore
* .bowerrc
* .editorconfig
* .jshintrc
* package.json
* bower.json
* config.json
* Gruntfile.js

`npm install -d generator-generator`，

`mkdir generator-blog && cd $_`

`yo generator`，輸入自己想要的generator名稱，這邊是用blog

`npm link`，你才可以用`yo blog`

你就可以去別的資料夾用`yo blog`了，當然這樣還不夠，我們還沒自定我們需要的東西

用你喜愛的editor開啟，app/index.js，這就是yo主要的設定檔

先讓我們看一下這段

```js
var prompts = [{
  type: 'confirm',
  name: 'someOption',
  message: 'Would you like to enable this option?',
  default: true
}];
```

這是預設的prompts，也就是你下`yo`的互動問題，我們把它改成:

```js
var prompts = [{
  name: 'blogName',
  message: 'What do you want to call your blog ?',
}];
```

接著，我們把這項資訊存入變數裡面

原本是：

```js
this.prompt(prompts, function (props) {
  this.someOption = props.someOption;

  cb();
}.bind(this));
```

改成：

```js
this.prompt(prompts, function (props) {
  this.blogName = props.blogName;

  cb();
}.bind(this));
```
