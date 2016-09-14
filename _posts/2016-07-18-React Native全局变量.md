---
layout: post
title: "React Native全局变量"
comments: true
description: ""
keywords: "React Native"
---

> Globals.js-react native


// File: Globals.js
		module.exports = {
  		STORE_KEY: 'a56z0fzrNpl^2',
  		BASE_URL: 'http://someurl.com',
  		COLOR: {
    		ORANGE: '#C50',
    		DARKBLUE: '#0F3274',
    		LIGHTBLUE: '#6EA8DA',
    		DARKGRAY: '#999',
  			},

			};

Then I just require it at the top...

		GLOBAL = require('../Globals');


And access them like so...

		GLOBAL.COLOR.ORANGE
