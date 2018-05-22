### grep 
- 管道，与'|'一起使用，对命令结果过滤。
- 常用法：
    -  ```
        ls | grep 'a'
        ```   查看目录下所有包含a字符的文件或者目录
    - ```cat log.txt | grep 'error' ```   查看日志中存在error记录的那些行 

    - ``` curl https://testerhome.com 2>/dev/null  | grep Appium | grep -v Python ``` 匹配包含了Appium但是不包含Python的行

- 参数
    - -v 排除匹配条件
        - ```ls | grep -v upload | xargs rm -rf  ```除了上传文件目录，其他文件都删除
    - -c 统计字符串匹配的行数
        - ``` cat demo.py | grep -c 'print'  ``` 统计文件中print匹配到的行数
    - -o 打印匹配的字符
        - ``` curl https://testerhome.com  | grep -o Appium ``` 打印Appium在页面中出现的每一次。不关注前后文。每个字符串占一行

        - ``` curl https://testerhome.com | grep -o Appium | wc -l ``` 利用wc -l 统计行，统计Appium出现的次数

    - -n 显示行号
        - ```curl https://testerhome.com  2>/dev/null | grep -n Appium ``` 过滤显示Appium出现的行，并且显示每一行的行号。

    - -E 正则
        - ``` curl https://testerhome.com  2>/dev/null | grep -n -E  'Appium|Python'   ``` 过滤匹配并显示出现了Appium或者Python的字段，并打印行号

    - -i 忽略大小写
        - ```echo 'HELLO WORLD' | grep -i 'hello' ```

    - 打印匹配行上下文信息,使用 -A n打印匹配行及其后n行信息。使用-B n打印匹配行及其前n行信息。使用 -C n。打印匹配行及其前后n行信息。假设有多重匹配，将使用--隔离。
        - ``` seq 1 10 | grep 5 -A 3 ``` 打印匹配行与后三行

        - ``` seq 1 10 | grep 5 -B 3 ``` 打印匹配行与前三行

        - ``` seq 1 10 | grep 5 -C 3 ``` 打印匹配行与前后三行

### awk
- 分割符。默认通过空格分割，可指定分割符号
- 语法：``` awk '{pattern + action}' {filenames} ```
- 常用法
    - 
- 参数 or 动作
    - RS 行记录分隔符
    - FS 几里路分隔符
    - NR 记录数
    - NF 字段数
    - BEGIN END

### sed
- 替换

### 


<meta http-equiv="refresh" content="1.0">
