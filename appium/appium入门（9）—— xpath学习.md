## 通过xpath定位元素
### 通过绝对路径

### 通过相对路径

//className[@属性='value']
//className[contains(@属性,"value")]
//android.widget.HorizontalScrollView/android.widget.LinearLayout/android.support.v7.app.ActionBar$Tab[0]/android.widget.TextView
eg:
```
#已知文本信息
//android.widget.TextView[@text='夜盘行情']
```
//*[@resource-id='com.huawei.works:id/tv_menu_item_text' and @text='发博客']


```
//*[not(ancestor-or-self::UIATableView)]
//*[not(ancestor-or-self::UIAStatusBar)]
//*[@resource-id='com.xueqiu.android:id/action_search']/parent::*
//*[@resource-id='com.xueqiu.android:id/action_search']
//*[contains(name(), 'Text')]
//*[@resource-id!='' and not(contains(name(), 'Layout'))]
//*[../*[@selected='true']]
```


