# ReactNative环境搭建


基于MAC+IOS环境
### 依赖
 Xcode, node.js, React Native command line tools,  Watchman, Homebrew

## 安装

**安装homebrew**

Homebrew, Mac系统的包管理器，用于安装NodeJS和一些其他必需的工具软件。<http://brew.sh/>

homebrew在安装软件时可能会碰到/usr/local目录不可写的权限问题。可以使用下面的命令修复：

sudo chown -R `whoami` /usr/local


**安装node**

*brew install node*


React Native需要NodeJS 4.0或更高版本。

Homebrew默认安装的是最新版本


---

<div style="page-break-after: always;"></div>



**安装watchman**

*brew install watchman*

Watchman是由Facebook提供的监视文件系统变更的工具。安装此工具可以提高开发时的性能（packager可以快速捕捉文件的变化从而实现实时刷新）。

<https://facebook.github.io/watchman/docs/install.html>

![](http://ww3.sinaimg.cn/mw690/6314d064gw1f69df98l3hj20v00myh0h.jpg)



 ---
<div style="page-break-after: always;"></div>


**安装React Native的命令行工具**

* npm install -g react-native-cli*

![](http://ww2.sinaimg.cn/mw690/6314d064gw1f69dg25frzj20us06cq5p.jpg)


npm是安装node时会自动带过来

如果你看到EACCES: permission denied这样的权限报错，那么请参照上文的homebrew译注，修复/usr/local目录的所有权：

* sudo chown -R `whoami` /usr/local*


npm -v 查看版本情况

如果你安装的是旧版本的 npm，可以通过 npm 命令来升级，命令如下：
* npm install npm -g*

**检测安装环境**

* react-native init AwesomeProject*

* cd AwesomeProject*

* react-native run-ios*

你也可以在Nuclide中打开AwesomeProject文件夹 然后运行
