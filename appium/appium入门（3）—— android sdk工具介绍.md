在使用appium编写脚本驱动测试之前，我们有必要了解下sdk的几个小工具。

### platform-tools/adb 
#### 什么是adb?
adb工具即Android Debug Bridge（安卓调试桥） tools。它就是一个命令行窗口，用于通过电脑端与模拟器或者真是设备交互。

由于sdk环境变量配置了该路径，可以通过命令提示窗口直接运行adb命令。

#### 常用命令
命令 | 说明
---|---
adb devices | 查看已连接的设备
adb push PCPath devicePath | 推送PC文件到手机
adb pull devicePath PCPath | 下载文件到电脑
adb shell screencap /sdcard/screen.png | 截屏
adb install/uninstall  | 安装，卸载应用
adb logcat | 打印log日志
adb kill-server/adb start-server  | 启动/杀死adb进程
adb shell | 进入调试设备的shell界面
adb shell pm list packages <Filter> |   列出满足filter条件的所有包

### build-tools/XXXX/aapt
aapt即Android Asset Packaging Tool.

这个工具可以查看,创建,更新ZIP格式的文档附件(zip, jar, apk),也可将资源文件编译成二进制文件。

#### 常用命令
命令 | 说明
---|---
aapt dump badging xxx.apk | 查看apk的信息

```
package: name='com.mrqyoung.autoinstall' versionCode='1' versionName='1.0' platf
ormBuildVersionName='6.0-2166767'
sdkVersion:'16'
targetSdkVersion:'23'
application-icon-160:'res/mipmap-mdpi-v4/ic_launcher.png'
application: label='' icon='res/mipmap-mdpi-v4/ic_launcher.png'
feature-group: label=''
  uses-feature: name='android.hardware.faketouch'
  uses-implied-feature: name='android.hardware.faketouch' reason='default featur
e for all apps'
provides-component:'accessibility'
supports-screens: 'small' 'normal' 'large' 'xlarge'
supports-any-density: 'true'
locales:
densities: '160'

```

### tools/uiautomatorviewer
uiautomatorviewer是android SDK自带的工具。通过截屏并分析XML布局文件的方式，为用户提供控件信息查看服务。该工具位于SDK目录下的tools\bin子目录下。可以看到，它是通过bat文件启动的。
![image](https://img-blog.csdn.net/20171016231634801?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvZGFpaHVpbWFvemlkZXJlbg==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)


uiautomatorviewer的菜单栏有四个按钮，分别表示打开已保存的布局，获取详细布局，获取简洁布局，保存布局。点击保存，将存储两个文件，一个是图片文件，一个是.uix文件(XML布局结构)。

通过使用UI Automator Viewer，我们可以在没有代码的情况下，查看控件布局，并获取UI的ID，用于之后的脚本编写。