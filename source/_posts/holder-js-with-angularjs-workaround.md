title: "holder.js with angularjs workaround"
date: 2014-03-20 13:25:19
tags:
permalink: holder-dot-js-with-angularjs-workaround
id: 44
updated: '2014-03-20 13:25:19'
---



```js directives.js
angular.module('mean').directive('holderFix', function () {
    return {
        link: function (scope, element, attrs) {
            Holder.run({images: element[0], nocss: true});
        }
    };
});
```

```html index.html
<img src="holder.js/100x100" alt="" holder-fix>
```
