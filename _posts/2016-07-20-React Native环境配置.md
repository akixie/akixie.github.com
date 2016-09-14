---
layout: post
title: "React Native环境配置"
comments: true
description: ""
keywords: "React Native"
---

> environment.js

React native does not have the concept of global variables. It enforces modular scope strictly, in order to promote component modularity and reusability.

Sometimes, though, you need components to be aware of their environment. In this case it's very simple to define an Environment module which components can then call to get environment variables, for example:


environment.js


		var _Environments = {
    		production:  {BASE_URL: '', API_KEY: ''},
    		staging:    {BASE_URL: '', API_KEY: ''},
    		development: {BASE_URL: '', API_KEY: ''},
			}

			function getEnvironment() {
    		// Insert logic here to get the current platform (e.g. staging, production, etc)
    		var platform = getPlatform()

    		// ...now return the correct environment
    		return _Environments[platform]
			}

			var Environment = getEnvironment()
			module.exports = Environment


my-component.js


		var Environment = require('./environment.js')

		...somewhere in your code...
		var url = Environment.BASE_URL


This creates a singleton environment which can be accessed from anywhere inside the scope of your app. You have to explicitly require(...) the module from any components that use Environment variables, but that is a good thing.


参考：
http://stackoverflow.com/questions/33117227/setting-environment-variable-in-react-native/33134782#33134782
