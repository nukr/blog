title: "nodejs workflow"
date: 2013-05-16 23:19:00
tags:
permalink: nodejs-workflow
id: 20
updated: '2013-05-16 23:19:00'
---



本來是想用yeoman，享受那種yo→grunt server之後就可以開始coding的生活，但是事與願違，yeoman是乎沒有支援backend的generator（還是我不會用 ...），只好退而求其次，使用grunt + bower，我的yo ...，但是其實express其實就是一種scaffolding，不廢話了，開始吧。

{% codeblock lang:bash %}
npm install -g express
npm install -g bower
npm install -g grunt
{% endcodeblock %}

這些就是我們本次的三大主角，都裝好之後`express <project name>`，就會產生一個專案資料夾，裡面有一些express必要的module，所以`cd <project name>`，`npm install`會安裝express的dependency，express的部分就到這邊結束了，但是我個人會加上一個`mkdir controllers`，我不喜歡用`routes`。

接下來是`bower`，這是twitter寫的一個package manager，前端的套件就由他來管理，安裝套件的語法跟npm類似，ex. `bower install jquery`、`bower install angular`，這樣你就不用一個一個用網站download新版了。如果你想把package裝到一個指定的位置可以加入以下檔案在project的根目錄`touch .bowerrc`

{% codeblock lang:js %}
{
  "directory": "public/components"
}
{% endcodeblock %}

再來就難了，[Grunt](gruntjs.com)是什麼？，你想像它是一個助理，你可以交待他任何你可能要做的事，當你交待的事發生了，這個助理就會照你所交代的去應對，從此之後你只需要專心寫你的程式，任何衍生的重複性工作，類似compile coffee-script、compile sass、unit test、uglify，這個助理都會幫你在你指定的檔案更動時，做出相對應的行動。

怎麼交代助理呢？列張清單給他吧，`touch Gruntfile.coffee`

``` coffee-script
  # Project configuration.
  grunt.initConfig

  # Load the plugin that provides the "uglify" task.
  grunt.loadNpmTasks('grunt-contrib-uglify')

  # Default task(s).
  grunt.registerTask('default', ['jshint', 'compass', 'coffee', 'watch'])
```

``` bash
npm install -g nodemon
npm install -g coffee-script
touch .npmignore
```
