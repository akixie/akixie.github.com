---
layout: post
title: "tableview隐藏section"
comments: true
description: ""
keywords: "ios"
---


先设置
    tableView.sectionHeaderHeight = 0;
    tableView.sectionFooterHeight = 0;
再根据需要实现：
    - (CGFloat)tableView:(UITableView *)tableView heightForHeaderInSection:(NSInteger)section- (CGFloat)tableView:(UITableView *)tableView heightForFooterInSection:(NSInteger)section
