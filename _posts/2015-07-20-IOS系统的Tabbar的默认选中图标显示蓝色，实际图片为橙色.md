---
layout: post
title: "系统的Tabbar的默认选中图标显示蓝色，实际图片为橙色"
comments: true
description: ""
keywords: "IOS, Tabbar"
---

修改tabbar默认蓝色：

      UIImage *img = [UIImage imageNamed:@"tabbar_message_hl"];
        img =  [img imageWithRenderingMode:UIImageRenderingModeAlwaysOriginal];
        [self.tabBarItem setFinishedSelectedImage:img
                      withFinishedUnselectedImage:[UIImage imageNamed:@"tabbar_message"]];

![](http://ww1.sinaimg.cn/mw690/6314d064gw1f7t5ie4ef2j20ia0k2ta2.jpg)
