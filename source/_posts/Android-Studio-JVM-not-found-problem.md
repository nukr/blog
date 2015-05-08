title: "Android Studio JVM not found problem"
date: 2014-12-28 19:00:18
tags:
permalink: android-jvm-not-found-problem
id: 3
updated: '2014-12-28 19:05:41'
---

Android Studio 實在很爛，遲早把他換掉，在換掉他之前還是要讓他能動，還是得要解決這個問題

`vi /Application/Android\ Studio.app/Contents/Info.plist`

找到 `1.6*` 這個字串，把它改成 `1.8*` 即可。