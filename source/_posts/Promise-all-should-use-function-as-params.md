title: Promise.all should use function as params
date: 2015-10-16 23:12:27
tags:
---

今天我們要聊的是：`Promise.all`，他吃一個 Array，Promise.all 會試著去 resolve 每一個 array 中的 element，直到 throw error。

重點來了，當 `Promise.all` throw error 之後整個 `Promise.all` 就 reject 了，我想要拿到部分 resolve 的值就拿不到了，我只能選擇全部成功或是全部失敗，這樣好像有點爛。

我有想到幾個解決方案：

1. 把每一個可能會 throw error 的 Promise 包起來自己 handle error，意味著我們的這個 Promise wrapper 只會 resolve，這個方法的缺點是你必須去包裝每一個 Promise 很費工。
2.

我就想到了Promise.all為什麼不做成 `Promise.all(arrayToBeResolve, arrayResolver, arrayRejector)`，讓 arrayResolver 跟 arrayRejector 去處理每一個 Promise.all 遍歷到的元素，但這樣又衍生了一個問題，就是 Promise.all 是 parallel 的處理 array，如果我想要 series 怎麼辦。

所以我就應該有兩隻 function，一個是PromiseTryResolveAllParallel，一個是PromiseTryResolveAllSeries，signiture 一樣

先來實作 PromiseTryResolveAllParallel：

```javascript
function PromiseTryResolveAllParallel (arrayToBeResolve, elementResolver, elementRejector) {
  return new Promise((resolve, reject) => {
    let counter = 0
    let result = Array(arrayToBeResolve.length)
    arrayToBeResolve.forEach((element, index) => {
      element.then
    })
  })
}
```
