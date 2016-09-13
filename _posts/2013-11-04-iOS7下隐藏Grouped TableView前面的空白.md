---
layout: post
title: "iOS7下隐藏Grouped TableView前面的空白"
comments: true
description: ""
keywords: "ios"
---



    self.hotelListTableView.tableHeaderView = [[UIView alloc] initWithFrame:CGRectMake(0.0f, 0.0f, self.hotelListTableView.bounds.size.width, 0.01f)];
