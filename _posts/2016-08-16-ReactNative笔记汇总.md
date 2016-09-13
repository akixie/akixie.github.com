---
layout: post
title: "React Native笔记汇总"
comments: true
description: ""
keywords: "React Native"
---
	
使用前沿的JAVASCRIPT为IOS、ANDROID编写跨平台原生APP

![](http://ww1.sinaimg.cn/mw690/6314d064gw1f69crsvfgoj207s064weg.jpg)

***
##简介
Facebook开源框架，已经在多项产品中使用了React Native，并且在持续投入建设

![](http://ww4.sinaimg.cn/mw690/6314d064gw1f69ctvbwfqj20a205kt8p.jpg)

React Native写的应用是Native App，而不是Hybrid App

**Hybrid App问题**

* WebView 单线程模型；
* DOM/CSS 排版复杂，在渲染上需要大量计算；
* 动画


最近版本：

    "react": "15.2.1",
    "react-native": "0.29.2"

###代表作品

FB官方代表作品开源地址：<https://github.com/fbsamples/f8ap>

 * Show Case

	<https://facebook.github.io/react-native/showcase.html>


###学习必要性


**Learn once, write anywhere**

IOS Anroid 跨平台原生开发

**个人角度**

学习必要性，全栈工程师, 提高竟然力

**公司角度**

团队协助，项目维护成本降低

组件化开发（RN技术核心），提高代码利用率

一个技术牛逼的人搞定两个平台（ios,安卓）

**苹果审核政策**

苹果目前的政策明确允许基于javascriptCore的热更新，但FB官方没有提供热更新方案.

随着React Native大规模应用，Appstore的政策前走了一步：

![](http://ww3.sinaimg.cn/mw690/6314d064gw1f6eeivq3ixj20xa0760xq.jpg)

* 2015.7.28 AppStore审核政策调整：允许运行于JavascriptCore的动态加载代码，下图是此前的审核政策，对比加亮部分的改变
![](http://ww1.sinaimg.cn/mw690/6314d064gw1f6eeksjk1ej20r40c479u.jpg)


##技术背景
app store更新慢,facebook 从纯web html环境到native,遇到版本更新速度问题，始终逃不过苹果审核

Hybrid app: native + web混合模式相互补短 但这个技术还是webview在移动设备下性能并不是很理想

所以2015年初F8大会的时候推出react native技术。目前已经有29个版本迭代。技术已经很成熟。性能方面优化的跟native很接近

###涉及技术

![](http://ww3.sinaimg.cn/mw690/6314d064gw1f69jbx7125j20x20j8myp.jpg)

* React 在开发者和 DOM 中间构建一个中间件，然后通过高效的算法来 diff 两次 Virtual DOM 渲染的差异，然后在最小范围内更新 DOM
* JSX编译器的核心是将基于XML的语言编译成JS代码，HTML直接写在JavaScript中

* Virtual DOM：相对Browser环境下的DOM（文档对象模型）而言，Virtual DOM是DOM在内存中的一种轻量级表达方式（原话是lightweight representation of the document），可以通过不同的渲染引擎生成不同平台下的UI，JS和Native之间通过Bridge通信
* 支持iOS、安卓、Web三大平台


**React Native**

<https://github.com/facebook/react-native>

<https://facebook.github.io/react-native/docs/getting-started.html#content>

**React(JS,JSX)**

<https://github.com/facebook/react>
<https://facebook.github.io/react/docs/getting-started.html>

<https://jsx.github.io/>

HTML 语言直接写在 JavaScript 语言之中，不加任何引号，这就是 JSX 的语法，它允许 HTML 与 JavaScript 的混写。

Native 与 JS的互相调用

* 0.17版本开始React Native JS引擎已经全部使用的是iOS自带的JavaScriptCore，在JSContext提供的Native与js互相调用的基础上，封装出了自己的互调方法。下面是一张结构图

![](http://ww4.sinaimg.cn/mw690/6314d064gw1f6e9nk6dkxj20za0pitf3.jpg)

* Native和JS的互相调用的原理解析参考:
<http://www.jianshu.com/p/269b21958030>

**JavaScriptCore**

* iOS 7 引入了 JavaScriptCore 库，它把 WebKit 的 JavaScript 引擎用 Objective-C 封装,提供了简单，快速以及安全的方式接入JS.

<http://nshipster.cn/javascriptcore/>

**NodeJS**

<https://github.com/nodejs/node>

<http://nodejs.cn/doc/node/>

**ES6**

<http://es6.ruanyifeng.com/>

**ios,Anroid基本意识**    

***


##环境搭建
基于MAC+IOS环境
###依赖
 Xcode, node.js, React Native command line tools,  Watchman, Homebrew


###安装
**安装homebrew**

Homebrew, Mac系统的包管理器，用于安装NodeJS和一些其他必需的工具软件。<http://brew.sh/>

homebrew在安装软件时可能会碰到/usr/local目录不可写的权限问题。可以使用下面的命令修复：

sudo chown -R `whoami` /usr/local

**安装node**

*brew install node*


React Native需要NodeJS 4.0或更高版本。

Homebrew默认安装的是最新版本

node -v可以查看版本情况

**安装watchman**

*brew install watchman*

Watchman是由Facebook提供的监视文件系统变更的工具。安装此工具可以提高开发时的性能（packager可以快速捕捉文件的变化从而实现实时刷新）。
<https://facebook.github.io/watchman/docs/install.html>


![](http://ww3.sinaimg.cn/mw690/6314d064gw1f69df98l3hj20v00myh0h.jpg)

**安装React Native的命令行工具**

*npm install -g react-native-cli*

![](http://ww2.sinaimg.cn/mw690/6314d064gw1f69dg25frzj20us06cq5p.jpg)


npm是安装node时会自动带过来

如果你看到EACCES: permission denied这样的权限报错，那么请参照上文的homebrew译注，修复/usr/local目录的所有权：

*sudo chown -R `whoami` /usr/local*


npm -v 查看版本情况

如果你安装的是旧版本的 npm，可以通过 npm 命令来升级，命令如下：
*npm install npm -g*

**检测安装环境**

*react-native init AwesomeProject*

*cd AwesomeProject*

*react-native run-ios*

你也可以在Nuclide中打开AwesomeProject文件夹 然后运行，或是双击ios/AwesomeProject.xcodeproj文件然后在Xcode中点击Run按钮。

###React Native项目结构说明

![](http://ww3.sinaimg.cn/mw690/6314d064gw1f69dikhq6dj20qg0g2aci.jpg)

* node_modules 文件夹，这是 Node.js 用来存放和管理 npm 包的文件夹，现在这里包含了 React Native 框架。

* index.android.js 文件和 index.ios.js 文件。这是 React Native CLI 工具分别为 Android 和 iOS 创建的空壳应用。

* android 文件夹和 ios 文件夹。包含了用于生成两个平台的App项目。


###IDE开发工具
**WebStorm--Web前端开发神器**

JetBrains：捷克,IntelliJ，RubyMine，ReSharper，PHPStorm ，WebStorm

下载WebStorm:

<http://www.jetbrains.com/webstorm/>

<http://soft.macx.cn/5813.htm>

下载ReactNative插件：

*git clone <https://github.com/virtoolswebplayer/ReactNative-LiveTemplate>*

打开web storm导入插件Jar包

file -> import settings -> ReactNative.jar

WebStorm不识别React Native语法解决方案
只需要开启JSX语法支持即可，具体解决方案如下:
Preferences -> Languages and Frameworks -> JavaScript -> language version下拉框里选JSX

![](http://ww2.sinaimg.cn/mw690/6314d064gw1f69d95toh9j21b40viwo6.jpg)

**Nuclide**

1. 先下载Atom
https://atom.io/
atom
2. 然后利用 Atom 的包管理器 apm 安装安装nuclide插件
$ apm install nuclide

或直接源码安装

*git clone <https://github.com/facebook/nuclide.git>*
cd nuclide

或在atom设置中安装nuclide

Preferences -> Install -> nuclide
![](http://ww3.sinaimg.cn/mw690/6314d064gw1f69db333tkj21j40u0agi.jpg)


Atom自动代码揭示  
Atom > Open Your Keymap 文件添加

'atom-text-editor':
  'cmd-alt-l': 'editor:auto-indent'

 ![](http://ww3.sinaimg.cn/mw690/6314d064gw1f69dbme5dmj20xm0q0tdb.jpg)
 ![](http://ww2.sinaimg.cn/mw690/6314d064gw1f69dcaramuj210c14yn5a.jpg)


 ***


##IOS原有项目中集成React Native
1. 创建package.json
![](http://ww3.sinaimg.cn/mw690/6314d064gw1f69dnm7bqhj20u40byjtp.jpg)
2. 执行npm install安装react-native包依赖
3. 编辑或创建Podfile，新增React引用
![](http://ww4.sinaimg.cn/mw690/6314d064gw1f69do5sm0lj20vq0cqgq1.jpg)
4. 执行pod install --verbose --no-repo-update
![](http://ww4.sinaimg.cn/mw690/6314d064gw1f69domza71j20r80n0ais.jpg)
5. 创建一个文件夹来存放应用的React代码
6. 然后新建一个简单的testview.ios.js文件


	$ mkdir ReactComponent

	$ touch ReactComponent/testview.ios.js


7. 编辑testview.ios.js
![](http://ww4.sinaimg.cn/mw690/6314d064gw1f69dp2gew0j218u14wk27.jpg)
8. 开启React Native开发服务器

    (JS_DIR=`pwd`/ReactComponent; cd node_modules/react-native; npm run start -- --root $JS_DIR)

    这条命令会启动一个React Native开发服务器，用于构建我们的bundle文件。--root选项用来标明你的React Native应用所在的根目录。在我们这里是ReactComponents目录，里面有一个index.ios.js文件。开发服务器启动后会打包出index.ios.bundle文件来，并可以通过http://localhost:8081/index.ios.bundle来访问。
9. xcode项目中添加react native模块组件
![](http://ww1.sinaimg.cn/mw690/6314d064gw1f69ds3hdmkj21kw0njtkh.jpg)

10. 模拟器运行程序

	*react-native run-ios*
	![](http://ww2.sinaimg.cn/mw690/6314d064gw1f69dsiyb3gj20hc0camxu.jpg)

**在手机设备真机上运行程序**


* 打开iOS文件AppDelegate.m

	注释这行代码 ：jsCodeLocation = [NSURL URLWithString:@"http://localhost:8081/	index.ios.bundle"];

	替换成： jsCodeLocation = [[NSBundle mainBundle] URLForResource:@"main" 	withExtension:@"jsbundle"];

* 执行npm start命令打包程序
* 运行下载main.jsbundle到本地 http://localhost:8081/index.ios.bundle -o main.jsbundle

	![](http://ww3.sinaimg.cn/mw690/6314d064gw1f6ebnadhtfj20r80n0jx1.jpg)
* 把main.jsbundle拷贝到项目中，添加引用
	![](http://ww1.sinaimg.cn/mw690/6314d064gw1f6ebpiljwhj20oi0d2tb5.jpg)

main.jsbundle

***
##组件


**ListView示例**
	![](http://ww3.sinaimg.cn/mw690/6314d064gw1f6alkxx6dfj211u0jqq5o.jpg)


XCode下添加ListView
![](http://ww3.sinaimg.cn/mw690/6314d064gw1f6alt1i3ccj216c0icwos.jpg)

* 更多组件参考官方文档：<https://facebook.github.io/react-native/docs/listview.html>


***
##APIS
**系统提示框**
调用Alert示例
![](http://ww2.sinaimg.cn/mw690/6314d064gw1f6am063w1uj211k0dqju5.jpg)
运行效果：


![](http://ww2.sinaimg.cn/mw690/6314d064gw1f6am0i65lgj20gw0uojsx.jpg)

* 更多API参考官方文档：<https://facebook.github.io/react-native/docs/alert.html>


##Networking-JS

* JS网络请求：

 		fetchData: function() {
    		fetch(REQUEST_URL)
      		.then((response) => response.json())
      		.then((responseData) => {
        		this.setState({
          		dataSource: this.state.dataSource.cloneWithRows(responseData.movies),
          		loaded: true,
       		 });
     		 })
      		.done();
 		 },

* 展示数据

		<ListView
       	 dataSource={this.state.dataSource}
        	renderRow={this.renderMovie}
        	style={styles.listView}
    	 />



***

##调试React Native 应用

####调试基本介绍

* 访问应用程序内开发者菜单：

	在 iOS 中摇动设备或在虚拟机里按组合键 control + ⌘ + z .
	在 Android 中摇动设备或按硬件菜单按钮 （旧的设备中以及大多数虚拟机中都有效，例如， 在 genymotion 	中，你可以按组合键 ⌘ + m 来模拟点击硬件菜单按钮）
	提示

* 隐藏开发人员菜单:

	在 iOS 中，打开 Xcode 中的项目，选择 Product → Scheme → Edit Scheme... (或按组合键 ⌘ + <).下一步, 在左边的菜单中选择 Run 然后将 Build Configuration 改为 Release。

	在 Android 中， 默认情况下, 由 Gradle 建立发布的开发者菜单将被禁用(例如， Gralde 的 assembleRelease 任务)。 虽然这种行为可以通过传递给 ReactInstanceManager#setUseDeveloperSupport 正确的值来自定义。

* 重加载JS

	选择 Reload (或者在 iOS 虚拟机中按组合键 ⌘ + r) 将会重新加载作用于你的应用程序中的 JavaScript 。 如果你增加了新的资源 (例如，将一幅图添加到 iOS 中的 Images.xcassets ，或 Android 中的 res/drawable 文件夹) 或者对任何本地代码进行修改 ( iOS 中的 Objective-C/Swift 代码或 Android 中的 Java/C++ 代码),你将需要重新生成该应用程序以使更改生效。



* 在实际设备上进行调试：

	在 iOS 中，- 打开文件 RCTWebSocketExecutor.m 并更改 localhost 为你的电脑IP地址。摇动设备打开开发菜单，选择启动调试。

	在 Android 中， 如果你正在运行通过 USB 连接的 Android 5.0+ 设备，您可以使用 adb 命令行工具来从设备到您的计算机设置端口转发。 运行： adb reverse 8081 8081 (参阅 此链接 以获得 adb 命令详情)。 或者，你可以打开设备上开发菜单并选择开发设置，然后为设备设置更新调试服务器主机到您的计算机的 IP 地址。
React 开发工具 (可选)

	安装 React Developer Tools 作为谷歌浏览器的扩展。这将允许您通过 React 在开发工具中导航组件层次结构 ( 更多详情参阅 facebook/react-devtools )。

* Live Reload 自动刷新JS

	这个选项可触发 JS 在连接设备/模拟器上自动刷新。启用此选项：

	在 iOS 中，通过开发者菜单选择 Enable Live Reload ，当 JavaScript 有改动时，应用程序会自动重新加载。

	在 Android 中，启动开发菜单，进入 Dev Settings 并选择 Auto reload on JS change 选项。



####Chrome调试工具

在 Chrome 中调试 JavaScript 代码，在开发者菜单选择 Debug in Chrome 。 将打开一个新的标签 http://localhost:8081/debugger-ui。
安装插件：
![](http://ww4.sinaimg.cn/mw690/6314d064gw1f6ea1o1bg9j21hu0xok1z.jpg)

在 Chrome 中，按下组合键 ⌘⌥J 进入调试页面

![](http://ww2.sinaimg.cn/mw690/6314d064gw1f6ea2deae6j21kw122tpn.jpg)


####Atom中Nuclide中调试

1. 在Nuclide中，点击 command + shift + p打开command palette（打开终端选项），输入react native debug
![](http://ww4.sinaimg.cn/mw690/6314d064gw1f6eam6sq4xj20vo06kdh0.jpg)

2. 接着，点击模拟器，Command+D，选择Enable Remote JS debugging

![](http://ww2.sinaimg.cn/mw690/6314d064gw1f6eamob31gj20fm0rstav.jpg)

3. 重新启动程序，“react-native run-ios”；这时候，你会看到，Nuclide中，加载了debug窗口

![](http://ww3.sinaimg.cn/mw690/6314d064gw1f6ax64w4a3j21kw111alo.jpg)


***
##App更新 热更新
***

**在Debug下我们看到直接读取本地文件 URL 的方式：**

	NSString *urlString = @"http://localhost:8081/productlist.ios.bundle";
    NSURL *jsCodeLocation = [NSURL URLWithString:urlString];
    RCTRootView *rootView = [[RCTRootView alloc] initWithBundleURL:jsCodeLocation moduleName:@"ProductList" initialProperties:nil launchOptions:nil];
    [self.view addSubview:rootView];

* 如果我们将这个 URL 换成远程服务器上的 URL，就可以动态的读取最新的 JS Bundle 了。但是实际上这种方式是不可行的，因为远程加载 JS Bundle 是需要时间的，我们总不可能让用户在那干等着吧。于是想到另外的方式


通过进入 App 之后进行检测，如果有新版本的 JS Bundle 的话，则进行新 Bundle 的下载，不让用户察觉，在后头进行新版本的下载，用户下次使用 App 的时候加载新的资源包。
也就是通过后台更新。为了让用户每次打开 App 能拿到当前最新的 JS Bundle，我们让其从 Document 处去读取 JS Bundle，新版本的 JS Bundle 下载后也同样存在这个目录，类似下面代码：

	NSURL *jsCodeLocation;
	jsCodeLocation = [self URLForCodeInDocumentsDirectory];
  	if (![self hasCodeInDocumentsDirectory]) {
   		 //从 Document 上读取 JS Bundle
    	BOOL copyResult = [self copyBundleFileToURL:jsCodeLocation];
    	if (!copyResult) {
      		//拷贝失败，从 main Bundle 上读取
      		jsCodeLocation = [self URLForCodeInBundle];
   		 }
  	}
 	RCTBridge *bridge = [self createBridgeWithBundleURL:jsCodeLocation];
  	rootView = [self createRootViewWithBridge:bridge];

* 上面代码只是进行了 Bundle 的读取操作，由于每个 JS 包需要进行版本的控制，所以，我将版本的检测放到了 JavaScript 里面，在 index.ios.js 文件开头，定义了一个常量const JSBundleVersion = 1.0; //JS 版本号，每次迭代新的 JS 版本则让其加 0.01。而如果向 APP Store 提交新版本，比如提交了 1.1 版本，则相应的将 JSBundleVersion 设置为 1.1，为什么这样做我后面再详细说明。
当检测到有新的 JS 版本时，则通知 Native 进行 JS 的下载和保存，当然也可以直接在 JS 上进行下载保存。如下：

		getLatestVersion((err, version)=>{
  			if (err || !version) {
    			return;
  			}
  			let serverJSVersion = version.jsVersion;
  			if (serverJSVersion > JSBundleVersion) {
   				 //通知 Native 有新的 JS 版本
    		NativeNotification.postNotification('HadNewJSBundleVersion');
  			}
		});

Native 接到通知后，负责去下载新的 JS bundle，下载成功后并保存到指定路径，用户下次打开 App 时直接加载即可。
这里有几个地方可以优化一下：

1. 当检测到有新版本时，进一步判断用户当前网络是否是 wifi 网络，如果是则通知 native 下载，反之不下载。
2. 在 1 的条件下，添加一个网络改变的监测，因为很多情况下用户在非 wifi 网络下打开了 App 但是之后 App 又没被 kill 掉，这样就下载不到最新的 bundle 了，所以通过监测网络的改变，如果网络变为 wifi 并且有新版本，则下载。于是代码大概如下：



		const JSBundleVersion = 1.0;
		let hadDownloadJSBundle = true;
		//.....
		componentDidMount() {
   			 NetInfo.addEventListener('change', (reachability) => {
     		 if (reachability == 'wifi' && hadDownloadJSBundle == false) {
      			 hadDownloadJSBundle = true;
       			 NativeNotification.postNotification('HadNewJSBundleVersion');
      		}
   		 	});
    	this._checkUpdate();
		}

		_checkUpdate() {
   		 getLatestVersion((err, version)=>{
      		if (err || !version) {
       		 	return;
     		}
     		let serverJSVersion = version.jsVersion;
      		if (serverJSVersion > JSBundleVersion) {
        		//通知 Native 有新的 JS 版本
        		isWifi((wifi) => {
        			if (wifi) {
            			hadDownloadJSBundle = true;
            			NativeNotification.postNotification('HadNewJSBundleVersion');
          			} else {
           				hadDownloadJSBundle = false;
         			}
       		 	});
      		}
   			});
		}

JS 代码基本就这些，接下来看看在 native 上需要做哪些操作。

首先，要接收到下载 JS bundle 的通知，当然是要先注册为观察者了。

	- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
  	//...
  	[NativeNotificationManager addObserver:self 	selector:@selector(hadNewJSBundleVersion:) name:@"HadNewJSBundleVersion" 	object:nil];
  	//...
	}

* hadNewJSBundleVersion 方法里面根据需求下载 JS bundle， 为了能保证下载的包完整，我们可以同时准备一份 JS bundle 的 md5 码，用于校验。如下：

		- (void)hadNewJSBundleVersion:(NSNotification *)notification {
  			//根据需求设置下载地址
  			NSString *version = APP_VERSION;
  			NSString *base = [@"http://domain/" stringByAppendingString:version];
  			NSString *uRLStr = [base stringByAppendingString:@"/main.jsbundle"];
  			NSString *md5URLStr = [base stringByAppendingString:@"/mainMd5.jsbundle"];
  			//存储路径为每次打开 App 要加载 JS 的路径
  			NSURL *dstURL = [self URLForCodeInDocumentsDirectory];
  			[self downloadCodeFrom:uRLStr md5URLString:md5URLStr toURL:dstURL 			completeHandler:^(BOOL result) {
   				 NSLog(@"finish: %@", @(result));
  			}];
		}


* 下面，来完成文件读取并初始化 RCTRootView 的操作。在 AppDelegate 内我们通过调用自定义方法来获得 RCTRootView ，如下：
		- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:		(NSDictionary *)launchOptions
		{
 			RCTRootView *rootView = [self getRootViewModuleName:@"DynamicUpdateDemo" 			launchOptions:launchOptions];

  			self.window = [[UIWindow alloc] initWithFrame:[UIScreen mainScreen].bounds];
  			UIViewController *rootViewController = [UIViewController new];
  			rootViewController.view = rootView;
  			self.window.rootViewController = rootViewController;
  			[self.window makeKeyAndVisible];
  			return YES;
		}


* getRootViewModuleName:launchOptions方法负责处理一些我们需要的逻辑（如：根据是否在Debug模式下，是否在模拟器上等不同状态初始化不同的rootView），最终返回一个 RCTRootView 对象。

   ![](http://ww3.sinaimg.cn/mw690/6314d064gw1f6e3wp1iatj21d80yw7ga.jpg)


* 这里，我们主要看 production 部分。上面其实已经贴出一次这段代码，在这之前我先说下我们存放和读取 JS 的路径。首先在 Documents 内创建一个目录叫 JSBundle，然后根据当前 App 的版本号再创建一个和版本号相同名字的目录（如：1.0， 1.1），最后路径大概这样：…/Documents/JSBundle/1.0/main.jsbundle

**大致思路**

首先判断我们的目标路径是否存在 JS bundle（用户首次安装或更新版本后该路径是不存在 JS 的），如果不存在，则将项目上的 JS bundle 拷贝到该路径下。可以看到在拷贝之前调用了 resetJSBundlePath 方法，该方法的作用是将这个路径的其他文件清除，这样做的原因是：从旧版本更新到新版本（这里指的是App发布的新版本）后，之前旧的 JS bundle 还存在着。为了保险起见，得判断一下文件是否拷贝成功了，如果没成功，则将读取路径设置成项目上的 JS bundle 路径。最后，创建 bridge，创建 rootView 并返回。
这样，动态更新的操作就完成了。


**内容出处：**

<http://blog.csdn.net/linshaolie/article/details/50961955>

####安卓-React Native进行签名打包成Apk
参考：
<http://blog.csdn.net/developer_jiangqq/article/details/50525976>
