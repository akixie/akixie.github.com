## React Native—调用GPS经纬度。

1. plist添加或编辑：NSLocationWhenInUseUsageDescription  ：PropertyFinder would like to use your location to find nearby properties

2. Location 按钮的TouchableHighlight，然后为其添加下面的属性值：
onPress={this.onLocationPressed.bind(this)}
3. 将下面的代码添加到 SearchPage 类中：

  ```javascript
onLocationPressed() {
  navigator.geolocation.getCurrentPosition(
    location => {
      var search = location.coords.latitude + ',' + location.coords.longitude;
      this.setState({ searchString: search });
      var query = urlForQueryAndPage('centre_point', search, 1);
      this._executeQuery(query);
    },
    error => {
      this.setState({
        message: 'There was a problem with obtaining your location: ' + error
      });
    });
}
  ```

* 通过 navigator.geolocation 检索当前位置；这是一个 Web API 所定义的接口，所以对于每个在浏览器中使用 location 服务的用户来说这个接口都应该是一致的。React Native 框架借助原生的 iOS location 服务提供了自身的 API 实现。

* 如果当前位置很容易获取到，你将调用第一个箭头函数；这会向Nestoria 发送一个 query。如果出现错误则会得到一个基本的出错信息。

* 因为你已经改变了属性列表，你需要重新启动这个应用以看到更改。抱歉，这次不可以 Cmd+R。请中断 Xcode 中的应用，然后创建和运行项目。


* 在使用基于位置的搜索前，你需要指定一个被 Nestoria 数据库覆盖的位置。在模拟器菜单中，选择 Debug\Location\Custom Location … 然后输入 55.02 维度和 -1.42 经度。*

  ![](http://ww4.sinaimg.cn/mw690/6314d064gw1f7b0xepx8oj20ku12a0w5.jpg)
