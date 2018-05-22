### 目录
- [需求分析](#1)
- [工具](#2)
- [安装插件](#3)
    - [安装Package Control](#4)
    - [安装插件](#5)
- [插件配置](#6)
- [使用](#7)


<span id = "1"></span>
### 需求分析
- 轻量级的编辑器
- 支持编辑刷新预览同步
- 免费

基于目前市面上各种各样的Markdown编辑器，排除掉收费的、在线的、以及笔记类工具，最终选择了sublime3 + MarkdownEditing插件的模式。

<span id = "2"></span>
### 需要的工具
- Sublime3
- Sublime3插件
    - Package Control
    - MarkdownEditing 配色方案
    - Markdown Preview 实时预览

<span id = "3"></span>
### 安装插件
<span id = "4"></span>
#### 安装Package Control
- 通过View->Show Console菜单打开命令行，粘贴如下代码：
    - ``` import urllib.request,os; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); open(os.path.join(ipp, pf), 'wb').write(urllib.request.urlopen( 'http://sublime.wbond.net/' + pf.replace(' ','%20')).read())``` 
- 手动下载Package Control.sublime-package
    - 点击Preferences > Browse Packages菜单
    - 进入打开的目录的上层目录，然后再进入Installed Packages/目录
    - 下载[Package Control.sublime-package](https://packagecontrol.io/Package%20Control.sublime-package)并复制到Installed Packages/目录
    - 重启Sublime Text

如果顺利的话，此时就可以在Preferences菜单下看到Package Settings和Package Control两个菜单了。

<span id = "5"></span>
#### 安装插件
- 快捷键 Ctrl+Shift+p ，打开 “Command Palette” 悬浮对话框，在顶部输入 “install”, 然后下选点击 “Package Control:Install Package”，然后就可以在新的搜索框中查找需要的插件，回车即自动安装
- 输入MarkdownEditing回车
- 输入Markdown Preview回车
- 重启Sublime Text

<span id = "6"></span>
### 插件配置
- 开启MarkDown Preview
    - 修改Markdown Preview的配置文件，打开Preferences – Package Settings – Markdown Preview – Setting User，添加下面代码：
``` 
{
    "enable_autoreload": true,
} 
```

- 配置MarkDown Preview预览快捷键
    - 打开Preferences — Key Bindings-User，添加下面代码：
```
[
    { "keys": ["alt+m"], "command": "markdown_preview", "args": {"target": "browser", "parser":"markdown"} },
]
```

- 配置sublime失焦保存
    - 打开Preferences – Setting，添加下面代码：

        ```"save_on_focus_lost": true,```

- 配置md文件自动刷新
    - 每次我们写完，添加下面代码：

        ```
        <meta http-equiv="refresh" content="0.5">
        #注意：每次写md文件都要加上上面这段代码，可以修改content的数值，代表每次刷新的时间。
        ```

<span id = "7"></span>
### 使用
- 新建md文件
- 在文件末尾加入``` <meta http-equiv="refresh" content="1.0"> ```
- 使用 alt + m 打开浏览器，实时预览效果


<meta http-equiv="refresh" content="1.0">
