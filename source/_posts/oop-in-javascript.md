title: "oop in javascript"
date: 2013-06-23 20:10:00
tags:
permalink: oop-in-javascript
id: 23
updated: '2013-06-23 20:10:00'
---



## Chapter 3: Understanding Object

Even though there are a number of built-in reference types in JavaScript, you will most likely be createing your own objects fairly frequently. A large part of JavaScript programming is managing objects. Having a good understanding of how objects work is key to understanding JavaScript as a whole. Keep in mind that objects in JavaScript are dynamic, meaning that they can change at any point during code execution. Where class-based languages lock down objects based on a class definition, JavaScript objects have no such restrictions.

雖然在JavaScript中有數種內建的參照型別，你將非常頻繁的建立你自己的物件。在JavaScript程式設計中很大的一部分是管理物件。對於物件如何運作有相當良好的了解是作為一個整體瞭解JavaScript之鑰，牢記在JavaScript中物件是動態的，意思是他們可以改變在程式運作中的任一個時機。class為基礎的語言鎖定物件基於class定義，JavaScript物件沒有這種限制。

### Defining Properties

Recall From Chapter 1 that there are two basic ways to create your own objects, using that `Object` constructor and using an object literal. For example:

回憶第一章有兩個基本的方法去建立你自己的物件，使用物件建構子和物件實字。例如：

```js
var person1 = {
  name: "Nicholas"
};

var person2 = new Object();
person2.name = "Nicholas";

person1.age = "Redacted";
person2.age = "Redacted";

person1.name = "Greg";
person2.name = "Michael";
```

Both `person1` and `person2` are objects with a `name` property. Later in the example, both objects are assigned an `age` property. This could happen immediately after the definition of the object or quite a bit later. Objects you create are always wide open for modification unless you specify otherwise (more on that later in the book). The last part of this example changes the value of `name` on each object. Property values can be changed at any time as well.

When a property is first added to an object, JavaScript uses an internal method called \[\[Put\]\]
