## 查看手机设备信息
### 获取手机设备id
通过执行adb命令得到设备列表

```
adb devices
```

python通过subprocess.Popen执行管道任务，得到查询返回值。

```
result = subprocess.Popen("adb devices", shell=True, stdout=subprocess.PIPE,stderr=subprocess.PIPE).stdout.readlines()
```

python通过split拆分查询结果，去devices的设备id

```
devices = []
for item in result:
    t = item.decode().split("\tdevice")
    if len(t) >= 2:
        devices.append(t[0])
```


### 获取deviceName
- 借助adb查看/system/build.prop,得到结果根据参数指定需要的值
    - ro.build.version.release 手机操作系统版本
    - ro.product.model 设备型号（同平台）
    - ro.product.brand 设备品牌
    - ro.product.device 设备型号
        
    ```
    'adb -s' + devices + ' shell cat /system/build.prop'
    phone_info = subprocess.Popen(cmd, shell=True, stdout=subprocess.PIPE, stderr=subprocess.PIPE).stdout.readlines()
    ```
    
## 获取app信息
由于测试app固定不变，所以直接将取到的app信息写在desired_caps中。

- 借助adb获取appActivity信息
    - >adb shell monkey -p 包名 -v -v -v 1 > D:\test.log
    
    - 查找文件中的cmp= XXX, 等于后接的的就是appActivity
    - 通过uiautomatorviewer同步得到包名

- 通过寻找开\查看源码配置文件得到appPackage与appActivity信息
 
- 借助aapt获取app的详细信息。
    - >aapt dump badging app文件 > test.log
    
    - 通过查找package: name=得到包名
    - 通过查找launchable-activity: name= 得到activity的名称

- 通过 adb logcat 抓取当前 Android 机运行的 App 的包名
- 通过查看 APK 源码下的 AndroidManifest.xml 文件
- 通过pm命令查看
```
adb shell
pm list package
```

<meta http-equiv="refresh" content="1.0">
