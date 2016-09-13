---
layout: post
title: "iOS 10新特性-UserNotifications"
comments: true
description: ""
keywords: "ios10, UserNotifications"
---

> iOS 10 SDK 对Push这块进行了IOS最大的一次重构，现在开发者可以使用独立的 UserNotifications.framework 来集中管理和使用 iOS 系统中通知的功能。
***
> 在原有基础上增加了在通知中展示图片、视频，Action, 自定义通知 UI 等一系列新功能，非常强大。此外还支持撤回单条通知，更新已展示通知，中途修改通知内容。

## 几种新功能

* 1.发送带有图片的通知

  ![](http://ww4.sinaimg.cn/mw690/6314d064gw1f7ruekcduwj20gs0ooacl.jpg)

* 2.发送带有视频的通知

  ![](http://ww2.sinaimg.cn/mw690/6314d064gw1f7ruetb2n6j20eu0o0ade.jpg)
* 3.发送带有 action 的通知
  ![](http://ww2.sinaimg.cn/mw690/6314d064gw1f7ruezh74ej20r20p8ae3.jpg)

* 4.发送自定义UI通知
  ![](http://ww3.sinaimg.cn/mw690/6314d064gw1f7ruf7ib16j20f00o2dig.jpg)


## 新特性
 iOS 10 中通知不仅支持简单的一行文字，你还可以添加 title 和 subtitle，来用粗体字的形式强调通知的目的。对于远程推送，iOS 10 之前一般只含有消息的推送 payload 是这样的：


	{
  		"aps":{
   		 "alert":"Test",
   		 "sound":"default",
    	"badge":1
 		}
	}


如果我们想要加入 title 和 subtitle 的话，则需要将 alert 从字符串换为字典，新的 payload 是：


	{
 	 "aps":{
   	 "alert":{
    	  "title":"I am title",
   		   "subtitle":"I am subtitle",
 	     "body":"I am body"
  		  },
  	  "sound":"default",
   	 "badge":1
 	 }
	}


好消息是，后一种字典的方法其实在 iOS 8.2 的时候就已经存在了。虽然当时 title 只是用在 Apple Watch 上的，但是设置好 body 的话在 iOS 上还是可以显示的，所以针对 iOS 10 添加标题时是可以保证前向兼容的。

### 回顾API历程：

- iOS 3 - 引入推送通知 UIApplication 的 registerForRemoteNotificationTypes 与UIApplicationDelegate 的application(_:didRegisterForRemoteNotificationsWithDeviceToken:)，application(_:didReceiveRemoteNotification:)
- iOS 4 - 引入本地通知 scheduleLocalNotification，presentLocalNotificationNow:，application(_:didReceive:)
- iOS 5 - 加入通知中心页面
- iOS 6 - 通知中心页面与 iCloud 同步
- iOS 7 - 后台静默推送 application(_:didReceiveRemoteNotification:fetchCompletionHandle:)
- iOS 8 - 重新设计 notification 权限请求，Actionable 通知registerUserNotificationSettings(_:)，UIUserNotificationAction 与UIUserNotificationCategory，application(_:handleActionWithIdentifier:forRemoteNotification:completionHandler:) 等
- iOS 9 - Text Input action，基于 HTTP/2 的推送请求 UIUserNotificationActionBehavior，全新的 Provider API 等

### iOS 10 中被标为弃用的 API

- UILocalNotification
- UIMutableUserNotificationAction
- UIMutableUserNotificationCategory
- UIUserNotificationAction
- UIUserNotificationCategory
- UIUserNotificationSettings
- handleActionWithIdentifier:forLocalNotification:
- handleActionWithIdentifier:forRemoteNotification:
- didReceiveLocalNotification:withCompletion:
- didReceiveRemoteNotification:withCompletion:

> 更多信息可以在 WWDC 16 的 Introduction to Notifications 和 Advanced Notifications 这两个 Session 中找到详细信息；另外也不要忘了参照 UserNotifications 的官方文档

* Introduction to Notifications

	<https://developer.apple.com/videos/play/wwdc2016/707/>

* Advanced Notifications

	<https://developer.apple.com/videos/play/wwdc2016/708/>

* UserNotifications

	<https://developer.apple.com/reference/usernotifications>
