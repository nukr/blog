title: "AngularJS Notes"
date: 2013-12-29 14:31:02
tags:
permalink: angularjs-notes
id: 35
updated: '2013-12-29 14:31:02'
---




## Filter

## Directive

一個最基本的Directive 是這樣的

```coffeescript
app = angular.module 'myApp', []

app.directive "superman", ->
    restrict: "E"
    template: "<div>superman save the world</div>"

```

restrict 中文叫限制，前面的例子`restrict: 'E'`就是限制directive 爲Element，default 是`restrict: 'A'`

再看下一個

```coffeescript
app = angular.module 'myApp', []

app.directive "superman", ->
    restrict: "A"
    link: ->
        alert('it's work)

```

`restrict: 'A'` A for attritube 就是用在html element 的attritubes

`restrict: 'C'` C for class

`restrict: 'M'` M for comment，comment 用法比較詭異，來看例子

```html
<!-- directive:superman -->
```

### 簡化

```coffeescript
app = angular.module 'myApp', []

app.directive "superman", ->
    (scope, element)->
        console.log element
```

## Isolate Scope

isolate scope 這東西是有點難懂，我還是儘量的把它搞懂了isolate scope 有三種形式

```coffeescript main.coffee
app.directive "drink", ->
    scope:
        flavor: '@'
    template: "{{flavor}}"
```

```jade index.jade
div(ng-controller="AppCtrl")
    div(drink flavor="cherry")
```


```coffeescript
app.controller "AppCtrl", ($scope) ->
    $scope.ctrlFlavor = "shit"

app.directive "drink", ->
    scope:
        flavor: "="
    template: "{{flavor}} flavor is good"
```

```jade index.jade
div(ng-controller="AppCtrl")
    div(drink flavor="ctrlFlavor")
```

## Transclusion















