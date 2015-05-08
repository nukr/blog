title: "AngularJS E2E test by protractor"
date: 2013-12-28 18:27:04
tags:
permalink: angularjs-e2e-test-by-protractor
id: 34
updated: '2013-12-28 18:27:04'
---



測試是我寫程式到現在，都沒有去執行的項目，一直以來很想好好的搞懂，隨著程式肥大，維護變得越來越困難了，再不導入測試真的會死人

我現在專注在AngularJS 上面所以首先處理AngularJS 的E2E Test，這是屬於前端的測試，有別于後端，前端有非常惱人的Brower 相容性的問題

現在AngularJS Team 推薦使用Protractor 來做E2E Test，請看[連結](http://docs.angularjs.org/guide/dev_guide.e2e-testing)，好像很強大

Protractor：量角器，這個名字真的超適合作為AngularJS 的Testing framework

Protractor 是什麼？

Webdriver 是什麼？

Selenium 是什麼？


```bash
npm install protractor -g

webdriver-manager update

webdriver-manager start

protractor conf.js
```

因為protractor default 是用jasmine，我如果想改用mocha的話要做一些修改

```bash
npm install -g protractor@canary

webdriver-manager update

webdriver-manager start

npm install -g mocha
npm install -g chai
npm install -g chai-as-promised

```

`vi conf.js`

```javascript
var chai = require('chai');
var chaiAsPromised = require('chai-as-promised');

chai.use(chaiAsPromised);
var expect = chai.expect;
```

之後就要用`expect(myElement.getText()).to.eventually.equal('some text');`
