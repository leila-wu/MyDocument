python介绍推荐虫师的网站：[appium介绍](http://www.testclass.net/appium/appium-base-summary/)

#### appium环境搭建需要准备的应用有
- [jdk](#1)
- [android sdk](#2)
- [python](#3)
- [appium service](#4)
- [appium click](#5)

### <span id = "1">JDK</span>
直接安装jdk1.8，并配置环境变量

变量名 | 变量值
---|---
JAVA_HOME | C:\Program Files\Java\jdk1.8.0_121
Path | %JAVA_HOME%\bin
CLASSPATH | .;%JAVA_HOME%/lib;%JAVA_HOME%\lib;%JAVA_HOME%\lib\tools.jar;



### <span id = "2">android sdk</span>
作为appium的测试环境，我们只需要android sdk的部分，不需要下载集成sdk且庞大的Android Studio。

[下载地址推荐](http://tools.android-studio.org/index.php/sdk)

sdk解压后的目录结构如下

```
 D:\develop\Android\android-sdk-windows 的目录

2018/03/01  16:17    <DIR>          .
2018/03/01  16:17    <DIR>          ..
2018/03/07  17:57    <DIR>          .android
2018/03/05  21:13    <DIR>          add-ons
2015/10/14  09:51           220,209 AVD Manager.ex
2018/03/06  17:34    <DIR>          build-tools
2018/03/01  14:09    <DIR>          docs
2018/03/01  14:21    <DIR>          extras
2018/03/02  16:19    <DIR>          platform-tools
2018/03/05  20:36    <DIR>          platforms
2015/10/14  09:51           220,721 SDK Manager.ex
2015/10/14  09:51             1,170 SDK Readme.txt
2018/03/05  20:38    <DIR>          sources
2018/03/05  20:57    <DIR>          system-images
2018/03/06  17:34    <DIR>          temp
2018/03/02  15:49    <DIR>          tools
               3 个文件        442,100 字节
              13 个目录 58,913,771,520 可用字节
```

#### 设置sdk环境变量
变量名 | 变量值
---|---
ANDROID_HOME | D:\android\Android\sdk
PATH | ;%ANDROID_HOME%\platform-tools;%ANDROID_HOME%\tools;



#### 安装sdk版本
双击 SDK Manage.exe 启动SDK管理器。

![image](http://otfah9orz.bkt.clouddn.com/appium_sdk_manage.png)

根据需求与喜好选择android版本。
其中必须安装的有： 
- Android SDK Tools
- Android SDK Platform-tools
- Android SDK Build-tools
- Extras/Google USB Driver


### 启动SDK虚拟机
- 双击 AVD Manage.exe 启动AVD管理器。
- 点击 “Create…” 按钮，创建Android虚拟机(我的配置如下)
    - AVD Name : demo
    - Device：Nexus 4
    - Target: Android 6.0
    - CPU/ABI: Intel Atom(x86)
    - Keyboard: 选中
    - Skin: no skin
    - Front Camera: None
    - Back Camera: None
    - Memory Options: 
        - RAM: 512
        - VM Heap: 64
    - Internal Storage: 200
    - SD Card : 空
- 点击“OK”创建完成。
- 在AVD Manage 工具中选中创建的Android虚拟机，点击 “Start…” 按钮启动。



### <span id = "3">python</span>
此处选择安装anaocode,安装成功后自动配置python环境变量。

[清华大学开源软件镜像站](https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/)



### <span id = "4">appium-desktop</span>
**appium-service**

我们通过appium-service监听移动设备请求，解析不同语言编写的appium脚本驱动设备来运行测试。
appium-service下载地址：
- 地址一：https://bitbucket.org/appium/appium.app/downloads/
- 地址二：https://pan.baidu.com/s/1pKMwdfX

**appium-desktop**

由于appium-service许久未更新，实际上项目中采用的是desktop版本。

appium-desktop开源项目地址：https://github.com/appium/appium-desktop

appium-desktop下载地址：https://github.com/appium/appium-desktop/releases

当前环境为windwos，选择appium-desktop-Setup-1.5.0-ia32.exe下载安装，安装过程与其他软件一致，在此不多做介绍。

**desktop的使用：**
1. 安装完成桌面会生成一个紫色的 appium 图标，双击打开。
2. 默认显示监控的 host 和 port ，这和 Appium-Server中是一致的。点击 “Start Server V 1.7.1” 按钮启动服务。
3. 查看到以下内容，表示启动成功

```
[Appium] Welcome to Appium v1.7.2
[Appium] Appium REST http interface listener started on 0.0.0.0:4723
```

**命令行方式安装（支持命令行启动）**
1. 安装nodejs : https://nodejs.org/en/download/
2. 设置vpn：npm install -g appium
3. 未设置vpn使用淘宝源：

```
npm install -g cnpm --registry=https://registry.npm.taobao.org
cnpm install -g appium
```



### <span id = "5">python-client</span>
推荐使用pip安装appium的客户端。

python-client的项目名称叫做：Appium-Python-Client

```
pip install Appium-python-Client
```

到此，环境基本准备好了。