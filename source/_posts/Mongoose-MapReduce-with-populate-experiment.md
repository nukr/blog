title: "Mongoose MapReduce with populate experiment"
date: 2014-02-25 00:54:59
tags:
permalink: mongoose-mapreduce-with-populate-experiment
id: 43
updated: '2014-02-25 00:54:59'
---



這mongoose的MapReduce真的不知道是怎麼一回事，真的讓我很搞不懂，寫一篇文章來記錄
一些實驗結果，釐清倒底MapReduce with populate是怎麼運作的，先看一下Schema



``` javascript article.js
var ArticleSchema = new Schema({
    created: {
        type: Date,
        default: Date.now
    },
    title: {
        type: String,
        default: '',
        trim: true
    },
    content: {
        type: String,
        default: '',
        trim: true
    },
    user: {
        type: Schema.ObjectId,
        ref: 'User'
    }
});
```

我們可以看到ArticleSchema是有參考UserSchema的，那就再看一下UserSchema

``` javascript user.js
var UserSchema = new Schema({
    name: String,
    email: String,
    username: {
        type: String,
        unique: true
    },
    hashed_password: String,
    provider: String,
    salt: String,
    facebook: {},
    twitter: {},
    github: {},
    google: {},
    linkedin: {}
});
```
