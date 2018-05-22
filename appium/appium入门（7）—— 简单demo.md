以下是使用python实现的简单demo。通过之前记录的方法，获取设备信息与app信息，然后新建一个driver连接。最后通过driver.quit() 退出连接。

请求连接前，需要启动appium server。

python需要安装客户端：**pip install Appium-Python-Client**

```
#coding=utf-8

from appium import webdriver
import time

desired_caps={}
#使用的移动平台
desired_caps['platformName']='Android'
#指定平台的版本
desired_caps['platformVersion']='4.4'
#设备名称
desired_caps['deviceName']='022SSE1468000190'
#待测试的app的Java package
desired_caps['appPackage']='com.thinkive.future.dev.standard'
#待测试的app的Activity名字
desired_caps['appActivity']='com.thinkive.futureshl.activity.LauncherActivity'
#automationName 使用哪种自动化引擎。appium（默认）还是Selendroid。

# 新建一个连接
driver = webdriver.Remote('http:/localhost/wd/hub', desired_caps)
# 设置等待时间，等待页面加载
time.sleep(10)
# 使用xpath方式获取元素并点击
driver.find_element_by_xpath("//android.widget.HorizontalScrollView/android.widget.LinearLayout/android.widget.LinearLayout[2]").click()
time.sleep(3)
driver.find_element_by_id("com.thinkive.future.dev.standard:id/iv_quotation_futures_search").click()

# 退出连接
driver.quit()
```


#### 问题
报错信息```urllib.error.URLError: <urlopen error [WinError 10061] 由于目标计算机积极拒绝，无法连接。> ``` 意味着appium server服务没有开启


<meta http-equiv="refresh" content="1.0">