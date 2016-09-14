---
layout: post
title: "AppStore审核被驳回 PLA 3.3.12 解决办法"
comments: true
description: ""
keywords: "AppStore"
---

原因有可能是第三方sdk用到了采集IDFA，广告服务

输入命令：
      strings - -a -arch armv7 "Payload/(你的ipa包的名字).app/(你的ipa包的名字)" | grep advertisingIdentifier
比如
      strings - -a -arch armv7 "Payload/xianrenzhng.app/xianrenzhng" | grep advertisingIdentifier   回车执行


      strings - -a -arch armv7 "Payload/BabyVPDr.app/BabyVPDr" | grep advertisingIdentifier

> App提交审核的时候按照下图填写：

  ![](http://ww3.sinaimg.cn/mw690/6314d064gw1f7t6g0jv51j210q0myadw.jpg)
