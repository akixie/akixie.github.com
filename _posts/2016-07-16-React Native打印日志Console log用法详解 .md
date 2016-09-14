---
layout: post
title: "React Native打印日志Console log用法详解"
comments: true
description: ""
keywords: "React Native"
---

> console.log
Use string formats;


		console.log("%s %O", "My Object", obj);





Chrome has Format Specifiers with the following;


- %s Formats the value as a string.
- %d or %i Formats the value as an integer.
- %f Formats the value as a floating point value.
- %o Formats the value as an expandable DOM element (as in the Elements panel).
- %O Formats the value as an expandable JavaScript object.
- %c Formats the output string according to CSS styles you provide.

Firefox also has String Substitions which have similar options.

- %o Outputs a hyperlink to a JavaScript object. Clicking the link opens an inspector.
- %d or %i Outputs an integer. Formatting is not yet supported.
- %s Outputs a string.
- %f Outputs a floating-point value. Formatting is not yet supported.

Safari has printf style formatters

- %d or %i Integer
- %[0.N]f Floating-point value with N digits of precision
- %o Object
- %s String
