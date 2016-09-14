---
layout: post
title: "IOS生成的MD5与后台Service不匹配的问题"
comments: true
description: ""
keywords: "ios"
---

问题原因json序列化的方法不能随便用第三方库，推荐用苹果默认提供的解析方法：

![](http://ww3.sinaimg.cn/mw690/6314d064gw1f7t7w8qdbcj218m0d8jxt.jpg)
