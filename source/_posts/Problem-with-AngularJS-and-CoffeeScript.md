title: "Problem with AngularJS and CoffeeScript"
date: 2013-05-18 23:39:00
tags:
permalink: problem-with-angularjs-and-coffeescript
id: 22
updated: '2013-05-18 23:39:00'
---



要用CoffeeScript請用標準的寫法去寫AngularJs

```coffee-script
app = angular.module 'App', []

app.controller 'YourCtrl', ($scope) ->
  # Write you code here ...
```

還有另外一種寫法是用CoffeeScript中的Class去初始化controller（應該是吧）

這種寫法我目前還看不太懂，要研究一下CoffeeScript的Class

```coffee-script
app = angular.module 'myapp', []

class MySimpleCtrl

  @$inject: ['$scope'] 
  constructor: (@scope) ->
    @scope.demo = 'demo value'
    @scope.clearText = @clearText

  clearText: =>
    @scope.demo = ""

app.controller 'MySimpleCtrl', MySimpleCtrl

angular.bootstrap document, ['myapp']
```
