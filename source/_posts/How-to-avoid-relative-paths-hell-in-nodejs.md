title: How to avoid relative paths hell in nodejs?
date: 2015-11-04 10:32:06
tags: ['nodejs']
---

我只推薦一個方法就是 package.json postinstall script

```js
"postinstall": "ln -s ../src node_modules/mc"
```
