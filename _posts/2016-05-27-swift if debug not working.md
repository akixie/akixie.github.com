---
layout: post
title: "swift if debug not working"
comments: true
description: ""
keywords: "swift"
---

下面代码不起作用：

  #if DEBUG
        let a = 2
  #else
        let a = 3
  #endif

  Now, you must set the "DEBUG" symbol elsewhere, though. Set it in the "Swift Compiler - Custom Flags" section, "Other Swift Flags" line. You add the DEBUG symbol with the -D DEBUG entry.

  As usual, you can set a different value when in Debug or when in Release.

  I tested it in real code and it works; it doesn't seem to be recognized in a playground though.

  You can read my original post here.

  IMPORTANT NOTE: -DDEBUG=1 doesn't work. Only -D DEBUG works. Seems compiler is ignoring a flag with a specific value.


参考：

http://stackoverflow.com/questions/24003291/ifdef-replacement-in-swift-language
