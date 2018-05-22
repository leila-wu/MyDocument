## Genymotion
Genymotion是一款出色的跨平台的Android模拟器，具有容易安装和使用、运行速度快的特点，是Android开发、测试等相关人员的必备工具。

[Genymotion介绍主页](https://www.genymotion.com/)

### Genymotion安装
1. 进入官网注册个人帐号，[注册地址](https://www.genymotion.com/account/create/)
2. 本地virtualbox安装，[下载地址](https://www.virtualbox.org/wiki/Downloads)
3. 本地android sdk环境配置,可以参考android或者appium的环境搭建
4. 下载Genymotion安装,[下载地址](https://www.genymotion.com/download/)

### Genymotion使用
1. 打开Genymotion
2. 选择Settings,进入设置界面，选择Account,然后进行登录（使用之前注册的个人帐号）
3. 选择ADB，选择Use custom Android SDK tools,设置Android SDK为本地SDK路径
4. 选择Add，弹出选择虚拟设备界面，选择对应的设备安装。安装完成点击“完成”按钮。
5. 回到主页面，点击start按钮，启动模拟器。
6. 启用命令提示符，输入命令：
    ```
    C:\Users\XXXX>adb devices
    List of devices attached
    192.168.51.101:5555     device
    ```
7. 借助adb命令安装卸载查看应用信息

#### 问题记录
- 报错信息“Unable to create virtual device: Failed to import OVA file”
    - 答： 关闭应用， 重新使用管理员权限运行Genymotion和virtualbox

- adb安装应用报错
    ```
    C:\Users\lei>adb devices
    List of devices attached
    192.168.51.101:5555     device


    C:\Users\lei>adb install -s 192.168.51.101:5555 D:\develop\Android\HN4_QHZH_1608
    30_Android_SIT_100_22915.apk
    D:\develop\Android\HN4_QHZH_160830_And.... 29.3 MB/s (16569942 bytes in 0.539s)
            pkg: 192.168.51.101:5555
            ver: /sdcard/tmp/HN4_QHZH_160830_Android_SIT_100_22915.apk
    Failure [INSTALL_FAILED_INVALID_URI]

    ```
    - 答：去掉其他设备，去掉指定-s 安装成功。
    ```
        C:\Users\lei>adb install D:\develop\Android\HN4_QHZH_160830_Android_SIT_100_2291
    5.apk
    D:\develop\Android\HN4_QHZH_160830_And.... 25.6 MB/s (16569942 bytes in 0.618s)
            pkg: /data/local/tmp/HN4_QHZH_160830_Android_SIT_100_22915.apk
    Success
  
    ```

## 网易MuMu试用(相对Genymotion安装来说，操作更方便简洁)
1. 官网下载最新版本MuMu,[下载地址](http://mumu.163.com/)
2. 运行安装,启动MuMu
3. 在设置中打开USB调试模式
3. 在命令提示符窗口执行```>adb connect 127.0.0.1:7555```
4. 通过adb devices查看模拟器
    ```
    C:\Users\XXX>adb devices
    List of devices attached
    127.0.0.1:7555  device
    ```


<meta http-equiv="refresh" content="5">