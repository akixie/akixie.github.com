---
layout: post
title: "AppleWatch dyld: library not loaded rpath libswiftcore dylib"
comments: true
description: ""
keywords: "IOS"
---

![](http://ww2.sinaimg.cn/mw690/6314d064gw1f7t5wb40trj20qi0ac0x1.jpg)

解决办法：

For me none of the previous solutions worked. We discovered that there is an "Embedded Content Contains Swift Code" flag in the Build Settings that needs to be set to YES. It was NO by default!

![](http://ww3.sinaimg.cn/mw690/6314d064gw1f7t5wms35hj211w0cs0vl.jpg)
