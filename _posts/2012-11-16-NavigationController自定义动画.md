---
layout: post
title: "NavigationController自定义动画"
comments: true
description: ""
keywords: "ios"
---


代码：
    [UIView transitionWithView:self.navigationController.view duration:0.8 options:UIViewAnimationOptionTransitionCrossDissolve animations:^{
      [self.navigationController pushViewController:elementController animated:NO];
      [elementController release];
    } completion:NULL];
