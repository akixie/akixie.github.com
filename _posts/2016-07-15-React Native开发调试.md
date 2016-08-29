# ReactNative调试

## 调试基本介绍

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


---
<div style="page-break-after: always;"></div>

## Atom中Nuclide中调试

1. 在Nuclide中，点击 command + shift + p打开command palette（打开终端选项），输入react native debug
![](http://ww4.sinaimg.cn/mw690/6314d064gw1f6eam6sq4xj20vo06kdh0.jpg)

2. 接着，点击模拟器，Command+D，选择Enable Remote JS debugging

![](http://ww2.sinaimg.cn/mw690/6314d064gw1f6eamob31gj20fm0rstav.jpg)

3. 重新启动程序，“react-native run-ios”；这时候，你会看到，Nuclide中，加载了debug窗口

![](http://ww3.sinaimg.cn/mw690/6314d064gw1f6ax64w4a3j21kw111alo.jpg)


 ---
<div style="page-break-after: always;"></div>

## Chrome调试工具

在 Chrome 中调试 JavaScript 代码，在开发者菜单选择 Debug in Chrome 。 将打开一个新的标签 http://localhost:8081/debugger-ui。
安装插件：
![](http://ww4.sinaimg.cn/mw690/6314d064gw1f6ea1o1bg9j21hu0xok1z.jpg)

在 Chrome 中，按下组合键 ⌘⌥J 进入调试页面

![](http://ww2.sinaimg.cn/mw690/6314d064gw1f6ea2deae6j21kw122tpn.jpg)
