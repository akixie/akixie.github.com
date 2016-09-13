---
layout: post
title: "Xcode Error - Could not launch app - No such file or directory Error"
comments: true
description: ""
keywords: "ios"
---



Thats really annoying. This error happens in a number of different situations. Sometime restarting the Xcode, fixes the problem. If not, follow these steps:
Disconnect your device.

* Delete the app from your device.

* Quit xcode (Don't just simply close the window, quit it)

* Delete derived data folder (~/Library/Developer/Xcode/DerivedData/-gbrvhlvwmpiobxdujegtghggrffp - or something like that)

* Now start Xcode, connect device and run the project. It should work fine.
There it is.

   ![](http://ww1.sinaimg.cn/mw690/6314d064gw1f7b0la2ivnj20bo03qdg7.jpg)
