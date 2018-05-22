命令行启动配置成功后，直接通过appium启动。


```
C:\Users\lei>appium -h
usage: C:\Users\lei\AppData\Roaming\npm\node_modules\appium\build\lib\main.js
       [-h] [-v] [--shell] [--reboot] [--ipa IPA] [-a ADDRESS] [-p PORT]
       [-ca CALLBACKADDRESS] [-cp CALLBACKPORT] [-bp BOOTSTRAPPORT]
       [-r BACKENDRETRIES] [--session-override] [-l] [-g LOG]
    ...
    ...


A webdriver-compatible server for use with native and hybrid iOS and Android
applications.

Optional arguments:
  -h, --help            Show this help message and exit.
  -v, --version         Show program's version number and exit.
  --shell               Enter REPL mode
  --reboot              (Android-only) reboot emulator after each session and
                        kill it at the end
  --ipa IPA             (IOS-only) abs path to compiled .ipa file
  -a ADDRESS, --address ADDRESS
                        IP Address to listen on
  -p PORT, --port PORT  port to listen on
  -ca CALLBACKADDRESS, --callback-address CALLBACKADDRESS
                        callback IP Address (default: same as --address)
  -cp CALLBACKPORT, --callback-port CALLBACKPORT
                        callback port (default: same as port)
 ...
 ...
 ...

```

在此记录几个常用参数命令
- **-a , --address:** 修改appium的监听ip地址
- **-p , --port:** 修改appium的监听端口,默认4723
- **-bp ,--bootstrap-port:** 指定android设备连接的端口号
- **-g :** 将日志输出到指定文件
- **--session-override :** 如果有session冲突，允许session覆盖.
    - 不设置该参数，那么当测试异常退出时，Appium服务器的session可能还存在，下一条用例尝试建立session就会失败。
- **-U , --udid:** 连接物理设备的唯一设备标识符

eg:
appium -p 4700 -bp 4701 -U 127.0.0.1:21503


appium的启动端口