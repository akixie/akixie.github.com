---
layout: post
title: "解决RegexKitLite编译报错"
comments: true
description: ""
keywords: "IOS"
---


解决办法：

在项目的编译设置中找到Other Linker Flags，然后在后面字段空白处双击，添加“-licucore”就可以了。
