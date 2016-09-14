---
layout: post
title: "ReactNative项目发布CodePush"
comments: true
description: ""
keywords: "React Native"
---

> ReactNative项目发布借助微软提供的工具CodePush

下面来看发布命令：

查看版本记录

    code-push deployment ls Get_OP_IOS
打包

    react-native bundle --platform ios --entry-file index.ios.js --bundle-output ./CodePush/main.jsbundle --assets-dest ./CodePush --dev false
发布

    code-push release Get_OP_IOS ./CodePush 2.2.0  -d Production

回滚到指定版本：

    code-push rollback Get_OP_IOS Production --targetRelease v6

查看正式环境发版记录

    code-push deployment history Get_OP_IOS Production

发布到测试环境

打包：

    react-native bundle --platform ios --entry-file index.ios.js --bundle-output ./CodePush/main.jsbundle --assets-dest ./CodePush --dev false
发布：

    code-push release Get_OP_IOS ./CodePush 2.2.0  -d Staging --mandatory true
检查测试环境安装情况：

    code-push deployment history Get_OP_IOS Staging

发布到正式环境：

从开发环境中最近版本，转到正式环境。

    code-push promote Get_OP_IOS Staging Production -r 20%


![](http://ww3.sinaimg.cn/mw690/6314d064gw1f7t8jcqdh9j20za0wewqi.jpg)

更多其它用法和工具的安装请参考官方文档：

<https://github.com/Microsoft/react-native-code-push#ios-setup>
