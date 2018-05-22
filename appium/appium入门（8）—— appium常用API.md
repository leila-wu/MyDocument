appium的客户端（WebDriver）提供的接口按作用大致可以分为控件的查找、手势才做和系统操作。

## 控件查找API
WebDriver支持ID、Xpath、Class Name、Accessbility id和UIAutomator来查找控件。

### 通过id定位元素
- 语法
    - ```find_element_by_id(self,id_)```
    - ```find_elements_by_id(self,id_)```(返回list)
- 通过控件的resource id查找
- 举例
    - ```driver.find_element_by_id("com.thinkive.future.dev.standard:id/iv_quotation_futures_search")```

### 通过xpath定位元素
- 语法
    - ```find_element_by_xpath(self,xpath)```
    - ```find_elements_by_xpath(self,xpath)```(返回list)
- 通过xpath查找控件
- 举例
    - ```driver.find_element_by_xpath(@resource_id, "com.thinkive.future.dev.standard:id/iv_quotation_futures_search"```

### 通过class name定位元素
- 语法
    - ```find_element_by_class_name(self,name)```
    - ```find_elements_by_class_name(self,name)```(返回list)
- 在Native App测试中，参数Nname表示控件的类型，如``` android.view.Text```
- 在网页测试中，参数Name指代网页element的属性类名。如```<div class='test-demo'>...</div.>```
- 举例
    - ```driver.find_element_by_class("android.view.Text")```

### 通过Text定位元素
- 语法
    - ```find_element_by_name(self,name)```
    - ```find_elements_by_name(self,name)```(返回list)
- name表示text,在appium 1.5.0中废弃了该语法。但是WebDriver实际上是支持的
- 举例
    - ```driver.find_element_by_class("登录")```

### 通过Content Description定位元素
- 语法
    - ```find_element_by_accessibility_id(self,id)```
    - ```find_elements_by_accessibility_id(self,id)```(返回list)
- accessibility_id指Native App控件的Content Description
- 举例
    - ```driver.find_element_by_accessibility_id("请登录")```

### 通过UIAutomator定位元素
- 语法
    - ```find_element_by_android_uiautomator(self, uia_string)```
- uia_string通过java语言编写，
- 举例
    - ```self.device.find_element_by_android_uiautomator('text(\"列表\")')```
    - ```driver.find_element_by_android_uiautomator('new UiSelector().text("18513199586")').clear() ```



## 获取和操作控件信息的 API
 API | 方法描述
 --- | --- 
 text(self) | element.text 获取控件的文本信息
 click(self) | element.click 点击控件
 clear(self) | element.click 清空文本控件的内容
 get_attribute(self,name) | element.get_attribute("enabled") 获取控件的enabled属性。相当于is_enabled()
 is_enabled(self) | 判断控件是否可用,如可用返回true
 is_selected(self) | 判断控件是否被选中, 如选中返回true
 is_displayed(self) | 判断控件是否显示，如显示返回true
 send_keys(self,*value) | 模拟键盘输入到控件中

## 手势操作API
### 滑动操作
- 语法
    - ```swipe(self,start_x, start_y, end_x, end_y, duration=None) ```
- 从A点移动到B点
- duration为滑动动作执行事件，单位为毫秒
- APP的坐标，左上角值最小（0,0），右下角值最大
- 举例
    -  ``` ```


### 点击屏幕
- 语法
    - ```tap(self,positions,duration=None) ```
- 点击屏幕上的位置，最多支持五个手指同时点击
- duration为滑动动作执行事件，单位为毫秒。如果该参数不提供，则认为是点击操作；如果该参数指定，则认为是长按
- positions是一个列表，每一个列表项是一个二元组，值分别是屏幕上坐标的X和Y
- 举例
    -  ```driver.tap([(100,20),(100,60),(100,100)],500)```


### 缩小操作
- 语法
    - ```flick(self,element=None, precent=200, step=50) ```
- 在某控件上执行缩小操作，默认缩放比例为200%
- step表示缩小动作分多少步完成，默认50
- 举例
    -  ```driver.flick(element)```

### 放大操作
- 语法
    - ```zoom(self,element=None, precent=200, step=50) ```
- 在某控件上执行缩小操作，默认缩放比例为200%
- step表示缩小动作分多少步完成，默认50
- 举例
    -  ```driver.zoom(element)```

### 放大操作
- 语法
    - ```zoom(self,element=None, precent=200, step=50) ```
- 在某控件上执行缩小操作，默认缩放比例为200%
- step表示缩小动作分多少步完成，默认50
- 举例
    -  ```driver.zoom(element)```

### 滚动操作
- 语法
    - ```scroll(self, origin_el, destination_el) ```
- 从origin_el控件滚动到destination_el控件
- 参数必须是控件，而不是控件信息
- 举例
    -  ```driver.zoom(element)```

### 拖曳操作
- 语法
    - ```drag_and_drop(self, origin_el, destination_el) ```
- 把origin_el控件拖曳到destination_el的位置
- 举例
    -  ```driver.zoom(element)```


## 系统操作API
 API | 方法描述
 --- | --- 
 contexts(self) | 获取当前会话Session所有可用的上下文
 context(self)  | 获取当前会话Session正在使用的上下文
 current_context(self) |
 keyevent(self, keycode, metastate=None) | 模拟发送一个硬件码到手机。具体键值可参考http://cs.szpt.edu.cn/android/reference/android/view/KeyEvent.html
 press_keycode(self, keycode,metastate=None) | 模拟发送一个硬件码到手机
 long_press_keycode(self, keycode,metastate=None) | 模拟发送一个长案件吗到手机
 current_activity(self) | 获取当前正在显示的Activity信息
 start_activity(self, app_package, app_activity, **opts) | 启动某个Activity,如果该Activity不属于另一个未启动的程序，那么该程序将被启动，然后改Activity被打开。参考adb shell am start
 close_app(self) | 如果Desired Capabilities指定的应用程序正在运行，则关闭该程序
 launch_app(self) | 在测试设备上启动Desired Capabilities中指定的应用程序
 reset(self) | 终止当前被测程序到初始状态
 shake(self) | 模拟晃动手机事件
 install_app(self, app_path) | 将app_path路径的应用安装到实际上，此处的app_path指PC端path,需要包含目录和文件名。
 is_app_install(self, bundle_id) | 判断应用程序是否安装。在android手机上，bundle_id表示应用的完整包名。
 background_app(self, seconds) | 将被测应用程序放到后台运行一段事件，seconds为持续的秒数
 set_network_connection(self, connectionType) | 设置网络。
 get_screenshot_as_file(self, filename) | 将手机屏幕截图并保存电脑上的文件，filename为文件的路径和名称。
 pull_file(self, path) | 拉取手机上的一个文件，并以Base64格式编码返回文件数据，path为手机上的文件路径
 push_file(self, path, base64data) | 将一个Base64格式编码的数据推送到手机的文件路径，path为手机上的文件路径，base64data为要推送的数据
