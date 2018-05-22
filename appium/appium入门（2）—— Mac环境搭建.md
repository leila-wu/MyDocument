appium的访问地址：http://appium.io/#

查看appium的官网，安装命令如下：

```
Easy setup process, run a test now.
> brew install node      # get node.js
> npm install -g appium  # get appium
> npm install wd         # get appium client
> appium &               # start appium
> node your-appium-test.js
```
安装过程看似简单，但是由于墙的存在，难倒了一大片新手入门。

### 安装环境准备
#### ruby

一般情况下，新的mac ox系统会自带ruby，查看ruby的版本```ruby -v```

#### brew

brew是mac的包管理工具，就像pip是python的包管理工具，yum是redhat系统的包管理工具一样。 我们可以借助brew安装mac环境中需要用到的工具。
    
安装命令：```ruby -e "$(curl -fsSL https://raw.github.com/Homebrew/homebrew/go/install)" ```
   
#### Nodejs
   
由于appium工具是通过Node安装的，所以我们需要先安装Node，再通过npm工具安装appiu.

- 安装命令```brew install node```
    - 安装完成查看node信息```brew info node```
    - 升级node版本``` brew pgrade node```
    - 删除node ```brew r -g node```
    

注：由于我的系统升级到最新后，通过brew直接下载了最新版本的node，导致对appium的不兼容。最后删除了node，手动从官网下载旧版本的node安装，后续流程得以继续。

#### jdk
- 访问Oracle官网 http://www.oracle.com，浏览到首页的底部菜单,点击'Java for Developers' 
- 找到jdk8的部分，点击'jdk download'按钮
- 在弹出页面选择'Accept Lisence Agreement'同意协议
- 点击'Mac OS X x64' 后的dmg后缀安装包文件下载
- 安装jdk文件
    - 安装目录 /Library/Java/JavaVirtualMachines/jdk1.8.0_40.jdk/Contents/Home
    
#### sdk
dk下载地址同windows没有区别。一般平台都提供多种平台下载源。

[下载地址推荐](http://tools.android-studio.org/index.php/sdk)

- sdk安装
    - 通过safari浏览器下载完成后，sdk所在目录：~/Download
    - 进入sdk的tools目录，输入命令```./android sdk``` 请出SDK Manager，选择需要的插件
    
#### .bash_profile
系统在环境启动初期，先加载/etc/profile(全局配置)与/etc/bashrc(全局配置)，然后加载用户级配置文件~/.bash_profile文件。

在已经安装好jdk与sdk后，将环境变量配置到.bash_profile中

```
JAVA_HOME=$(/usr/libexec/java_home -v 1.8)
CLASS_PATH=$JAVA_HOME/lib/tools.jar:$JAVA_HOME/lib/dt.jar:.
ANDROID_HOME=/usr/local/opt/android-sdk
PATH=$JAVA_HOME/bin:$ANDROID_HOME/bin/:~/bin/:$PATH

export JAVA_HOME
export ANDROID_HOME
export CLASS_PATH
export PATH

```

退出保存，执行命令```source.bash_profile```。


#### xcode
    
通过app store安装最新版本即可。

#### python
    
通过brew可以直接安装python
- brew install python3
    
但是在此我使用的是anaconda的python环境。anaconda集成了大量python插件，安装包会比较大，但是后续方便环境管理。

[清华大学开源软件镜像站](https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/)

#### appium service安装
- 方法一：翻墙
    
    执行```npm install -g appium```
    
    如果要删除appium执行```npm r -g appium --verbose```
    
    安装完成，appium的安装目录：

- 方法二:设置代理安装
     
    方法来源：https://testerhome.com/topics/6040
    
    ```
    proxy=http://112.126.81.122:6$(date +%m%d)
    http_proxy=$proxy https_proxy=$proxy npm --proxy $proxy --https-proxy $proxy  install -g appium --verbose
    ```


- 方法三： 使用淘宝cnpm
        
    ```
    npm install -g cnpm --registry=https://registry.npm.taobao.org
    cnpm install -g appium
    ```
 
 安装完成后，通过appium-doctor检查环境。
 
##### 此处不采用appium-desktop的原因：
1. appium更新后，还得再等待时间才能安装desktop
2. appium的服务端，一般情况下不需要查看界面,直接通过命令行调用

	
##### 问题一
安装过程中报错``` TypeError: frame.getFileName is not a function
    at isInsideNodeModules (internal/util.js:360:28)
    at showFlaggedDeprecation (buffer.js:149:8)
    at new Buffer (buffer.js:174:3)
    at Array.<anonymous> (/usr/local/lib/node_modules/appium/node_modules/_source-map-support@0.4.18@source-map-support/source-map-support.js:149:21)
    at /usr/local/lib/node_modules/appium/node_modules/_source-map-support@0.4.18@source-map-support/source-map-support.js:53:24
    at mapSourcePosition (/usr/local/lib/node_modules/appium/node_modules/_source-map-support@0.4.18@source-map-support/source-map-support.js:171:21)```

解决思路：可以看到报错相关为node-modules。这个问题是由于node版本太高。目前appium server 1.8版本最高支持node 9。建议从官网下载正确的node8版本安装成功后，再重新执行安装命令。


##### 问题二
执行appium-doctor报错：
```
$ appium -v
-bash: appium: command not found
```

解决思路： 需要安装appium-docker: ``` npm install appium-doctor -g  ```

#### appium客户端安装

wd即webdriver。通过npm形式安装，即支持python或者java或者其他语言的驱动支持。不需要单独根据开发语言安装插件。


```
npm install wd
```

<meta http-equiv="refresh" content="1.0">