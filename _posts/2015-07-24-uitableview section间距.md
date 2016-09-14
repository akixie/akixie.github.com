---
layout: post
title: "uitableview section 间距"
comments: true
description: ""
keywords: "IOS,tableView"
---


在ios7中使用group类型的tableview时，第一个section距离navigationbar的距离很大，不符合这边的设计图。使用 myTableView . sectionHeaderHeight = 8.0无效。 于是通过各种方法测试，终于得到解决方法。就是通过设置tableview的headerview高度来控制这个距离。使用的方法是：

    - ( CGFloat )tableView:( UITableView *)tableView heightForHeaderInSection:(NSInteger )section
    {
      return 8.0 ;
    }

但对于第一个和第二个section之间的距离设置则不能使用- ( float )tableView:(UITableView *)tableView heightForFooterInSection:( NSInteger )section这个方法。

需要使用：
    myTableView . sectionFooterHeight = 1.0。
这个距离的计算是header的高度加上footer的高度。
