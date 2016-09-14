---
layout: post
title: "详细解Xcode上的Other linker flags作用"
comments: true
description: ""
keywords: "ios"
---

> Xcode Targets选项下有Other linker flags的设置，用来填写XCode的链接器参数，如：-ObjC -all_load -force_load等。

那么，Other linker flags设置的值实际上就是ld命令执行时后面所加的参数。

下面逐个介绍3个常用参数：

* －ObjC：加了这个参数后，链接器就会把静态库中所有的Objective-C类和分类都加载到最后的可执行文件中

* －all_load：会让链接器把所有找到的目标文件都加载到可执行文件中，但是千万不要随便使用这个参数！假如你使用了不止一个静态库文件，然后又使用了这个参数，那么你很有可能会遇到ld: duplicate symbol错误，因为不同的库文件里面可能会有相同的目标文件，所以建议在遇到-ObjC失效的情况下使用-force_load参数。

* -force_load：所做的事情跟-all_load其实是一样的，但是-force_load需要指定要进行全部加载的库文件的路径，这样的话，你就只是完全加载了一个库文件，不影响其余库文件的按需加载
