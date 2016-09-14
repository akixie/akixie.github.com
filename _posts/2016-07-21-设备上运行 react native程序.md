---
layout: post
title: "设备上运行 react native程序"
comments: true
description: ""
keywords: "React Native"
---

If anyone wants to improve on these instructions and add them to the docs, feel free, I can do it later if nobody else jumps on it - I just wanted to document it somewhere for now.

- Open iOS/AppDelegate.m
- Comment out jsCodeLocation = [NSURL URLWithString:@"http://localhost:8081/index.ios.bundle"];
- Uncomment jsCodeLocation = [[NSBundle mainBundle] URLForResource:@"main" withExtension:@"jsbundle"];
- Start up the packager with npm start and then run curl http://localhost:8081/index.ios.bundle -o main.jsbundle - if this fails (as it did on my machine) add the --ipv4 flag to the end of it.
- In XCode, right click on your project directory and click Add Files to "Project Name Here" - choose the main.jsbundle file that you generated.

You can now run the app on a device (either via usb or TestFlight) without needing to have a server running.

![](http://ww1.sinaimg.cn/mw690/6314d064gw1f7t8dh975fj20r80n0jx1.jpg)

![](http://ww1.sinaimg.cn/mw690/6314d064gw1f7t8dqo1z5j20oi0d2tb5.jpg)

参考：
https://github.com/facebook/react-native/issues/240
