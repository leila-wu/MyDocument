## AppCrawler
一个基于自动遍历的app爬虫工具. 支持android和iOS, 支持真机和模拟器. 最大的特点是灵活性. 可通过配置来设定遍历的规则.

### 开源地址
https://github.com/seveniruby/AppCrawler

### 用途
- 手工测试新功能的时候，执行自动遍历
- 手工测试完成，花时间查看遍历结果
- 自动遍历前登陆账户，有助于减少问题

### 功能
- 自动遍历
    - 自定义遍历路径
    - 定制自动输入和自动滑动
- 结果分析
    - logcat syslog数据收集
    - 点击前后的截图对比
    - 新老版本UI dif
    - app结构思维导图展示
- 可扩展
    - [Appetizer插桩监控](https://testerhome.com/topics/8162)


## 运行环境
### 环境搭建
参考 http://192.168.90.169/QualityAssurance/Automated_testing/tree/master/AppiumDoc

### 执行命令
- 自动生成demo yml文件
    - Java -jar appcrawler-2.1.3.jar --demo

- 最简单的启动
    - java -jar path/appcrawler-2.1.3.jar -a XXX.apk

- 指定配置文件并指定报告存放路径
    - java -jar path/appcrawler-2.1.3.jar -c conf/XXX.yml -o tmp/0

- 遍历已安装的app
    - java -jar appcrawler-2.1.3.jar --capability appPackage=com.thinkive.future.dev.standard,appActivity=com.thinkive.futureshl.activity.LauncherActivity
    
    - java -jar appcrawler-2.1.3.jar --capability "appPackage=com.thinkive.future.dev.standard,appActivity=com.thinkive.futureshl.activity.LauncherActivity"(mac机器需要添加引号)

- 查看操作耗时：
    - grep "<--.*wd\/hub" appium.log

- 配置文件说明
    - [appcrawler字段名介绍.yaml](http://192.168.90.169/QualityAssurance/Automated_testing/tree/master/AppCrawler/appcrawler字段名介绍.yaml)

- 配置文件示例
    -  [qihuodashi_run.yaml](http://192.168.90.169/QualityAssurance/Automated_testing/tree/master/AppCrawler/qihuodashi_run.yaml)

<meta http-equiv="refresh" content="3.0">