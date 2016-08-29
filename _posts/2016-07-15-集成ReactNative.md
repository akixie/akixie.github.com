#IOS原有项目中集成React Native

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
