Desired Capabilities在启动session的时候是必须提供的。ppium的Desired Capabilities是扩展了webdriver的Desired Capabilities。

Desired Capabilities本质上是key value的对象，它告诉appium server这样一些事情：

本次测试是启动浏览器还是启动移动设备？
是启动andorid还是启动ios？
启动android时，app的package是什么？
启动android时，app的activity是什么？


#### 通用的

- automationName：使用哪种自动化引擎。appium（默认）还是Selendroid？

- platformName：使用哪种移动平台。iOS, Android, orFirefoxOS？

- deviceName：启动哪种设备，是真机还是模拟器？iPhone Simulator, iPad Simulator, iPhone Retina 4-inch, Android Emulator, Galaxy S4, etc...

- app：应用的绝对路径，注意一定是绝对路径。如果指定了appPackage和appActivity的话，这个属性是可以不设置的。另外这个属性和browserName属性是冲突的。

- browserName：移动浏览器的名称。比如Safari' for iOS and 'Chrome', 'Chromium', or 'Browser' for Android；与app属性互斥。

- udid：物理机的id。比如1ae203187fc012g。


#### android平台特定属性
- appActivity：待测试的app的Activity名字。比如MainActivity, .Settings。注意，原生app的话要在activity前加个"."。

- appPackage：待测试的app的java package。比如com.example.android.myApp, com.android.settings。

#### iOS平台特定属性
- bundleId : 被测应用的 bundle ID 。用于在真实设备中启动测试，也用于使用其他需要 bundle ID 的关键字启动测试。

- autoAcceptAlerts: 当 iOS 的个人信息访问警告 (如 位置、联系人、图片) 出现时，自动选择接受( Accept )。默认值 `false`。


转自：https://testerhome.com/topics/1086

<meta http-equiv="refresh" content="1.0">