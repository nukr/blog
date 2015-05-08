title: "Avoid implicit return in coffeescript"
date: 2013-12-29 21:49:08
tags:
permalink: avoid-implicit-return-in-coffeescript
id: 36
updated: '2013-12-29 21:49:08'
---



## 避免Coffeescript 自動幫你加入 return

Coffeescript 會在function 的最後自動幫你加入`return` ，有時候會造成一些錯誤，解決的方法就是在function的最後手動加上一個`return`

```coffeescript
controller: ($scope) ->

    $scope.abilities = []

    this.addStrength = ->
        $scope.abilities.push "strength"

    this.addSpeed = ->
        $scope.abilities.push "speed"

    this.addFlight = ->
        $scope.abilities.push "flight"
    return

```
