## Xcode Error - the executable was signed with invalid entitlements

遇到这个问题可能是以下两个原因：

1. 安装了同一个应用
2. 证书过期后，或更新后。xcode--》Organizer ---》右下角点更新，把最新证书更新到xocde中
   可能存在xcode缓存，  进行project -->clean，把Xcode 彻底退出后。再打开。重新选择证书。
   
    ![](http://ww3.sinaimg.cn/mw690/6314d064gw1f7b0eaj8l5j20bo05lgm2.jpg)
    