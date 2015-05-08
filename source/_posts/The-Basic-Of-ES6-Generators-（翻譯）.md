title: "The Basic Of ES6 Generators （翻譯）"
date: 2015-01-11 15:49:36
tags:
permalink: the-basic-of-es6-generators
id: 64
updated: '2015-01-11 17:10:18'
---

One of the most exciting new features coming in JavaScript ES6 is a new breed of function, called a generator. The name is a little strange, but the behavior may seem a lot stranger at first glance. This article aims to explain the basics of how they work, and build you up to understanding why they are so powerful for the future of JS.

Javascript ES6 有一項最令人興奮的新特性是一種新型態的 function 叫做 generator。這個名字有點奇怪，但是第一瞥他的行為似乎更奇怪了。本篇文章目標是解釋基本上他是如何運作的，並且讓你了解為何他在未來的 JS 中如此強大。

## Run-To-Completion
## 運行到完成
The first thing to observe as we talk about generators is how they differ from normal functions with respect to the "run to completion" expectation.

第一件事去觀察像我們談論關於 generators 是如何不同於普通的 function 並且遵照我們的「運行到完成」的期待。

Whether you realized it or not, you've always been able to assume something fairly fundamental about your functions: once the function starts running, it will always run to completion before any other JS code can run.

```language-javascript
setTimeout(function(){
    console.log("Hello World");
},1);

function foo() {
    // NOTE: don't ever do crazy long-running loops like this
    for (var i=0; i<=1E10; i++) {
        console.log(i);
    }
}

foo();
// 0..1E10
// "Hello World"
```