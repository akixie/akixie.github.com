---
layout: post
title: "objective-c生成GUID"
comments: true
description: ""
keywords: "ios"
---

生成代码：

    + (NSString *)GetUUID
    {
      CFUUIDRef theUUID = CFUUIDCreate(NULL);
      CFStringRef string = CFUUIDCreateString(NULL, theUUID);
      CFRelease(theUUID);
      return [(NSString *)string autorelease];
    }
