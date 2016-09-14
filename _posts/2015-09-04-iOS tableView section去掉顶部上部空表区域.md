---
layout: post
title: "iOS tableView section 去掉顶部上部空表区域"
comments: true
description: ""
keywords: "IOS"
---


解决办法：

      self.homeTableView.contentInset=UIEdgeInsetsMake(-34, 0, 0, 0);
