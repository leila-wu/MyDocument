# 需求分析
随着禅道数据的增加，原来通过虚拟机提供的mysql服务器相应速度跟不上需求。且原来禅道的前端与数据库分离安装在windows与linux中，现在提供实体服务器，需要将禅道环境迁移。

## 确认环境信息
ip | 系统版本 | sql版本 | 角色 
---|---|---|---
192.168.1.249 | centos 6.4 | 5.6.28-log mysql | 旧服务器
192.168.35.130 | centos 7.2  | 10.1.22-MariaDB | 新服务器

# 操作步骤
## 在linux服务器中安装相同版本的禅道一键安装包
- 解压到opt目录 tar -zxvf ZenTaoPMS.9.6.2.zbox_64.tar.gz -C /opt

- apache和mysql的起停
    + 执行/opt/zbox/zbox start 命令开启Apache和Mysql。
    - 执行/opt/zbox/zbox stop 命令停止Apache和Mysql。
    - 执行/opt/zbox/zbox restart 命令重启Apache和Mysql。
    - /opt/zbox/zbox -ap 8080 -mp 3307 
        - ap参数 可以修改Apache的端口
        - mp参数 可以修改Mysql的端口
    - 如果需要开机自动启动，可以把 /opt/zbox/zbox restart 加到操作系统的自启目录。

## 还原数据
- 将windows的附件(zentao\www\data\upload\1)备份上传到linux服务器中，覆盖相应的目录文件，/opt/zbox/app/zentao/www/data/upload/1
- 导出数据（旧数据库）
    - >$ /usr/local/mysql/bin/mysqldump -S /data/mysql/mysql3307/tmp/mysql.sock -p --master-data=2 --single-transaction  --default-character-set=utf8 zentao > zentao.sql
	
	   /usr/local/mysql/bin/mysqldump -S /data/mysql/mysql3307/tmp/mysql.sock -p --master-data=2 --single-transaction  --default-character-set=utf8 zentao > zentao.sql
		/opt/zbox/bin/mysqldump -u root -p zentao > /root/zentao.sql
    - 报错： 
       >ERROR 1194 (HY000): Table 'zt_file' is marked as crashed and should be repaired
    - 解决方法： 
       >REPAIR TABLE `zt_file`
- 导入数据（新数据库）
    - /opt/zbox/bin/mysql -u root -p < /home/zentao.sql 


## 重启服务

## 禅道使用
- 访问和登录禅道
    - 启动Apache和Mysql服务后，浏览器直接访问 http://禅道服务器ip:apache端口 即可访问和登录禅道。
    - 注：如果网页无法访问，请先关闭禅道所在电脑的防火墙和selinux再刷新网页访问试一下。
    - 禅道默认管理员帐号是 admin，密码 123456。

- 禅道数据库
    - 网页登录数据库
        - 禅道数据库管理用的是adminer，但是为了安全，访问adminer的时候需要身份验证，需要运行/opt/zbox/auth/adduser.sh来添加用户(先 cd /opt/zbox/auth/ 然后执行 ./adduser.sh)
        - 网页访问 http://禅道服务的ip:apache端口，点击“数据库管理”按钮有2层验证：
            + 弹窗验证是输入运行 addusers.sh添加的用户名和密码
            + 网页直接显示登录界面：
                * 系   统：默认选择MySQL。
                * 服务器：127.0.0.1:mysql端口
                * 用户名： root
                * 密   码：123456
                * 数据库：zentao
 
    - 命令行连接数据库
        + 登录数据库：/opt/zbox/bin/mysql -u root -P mysql端口 -p  （比如：/opt/zbox/bin/mysql -u root -P 3306 -p）
        + 导入数据库：/opt/zbox/bin/mysql -u root -P mysql端口 -p 要导入的库名 < XXXX.sql （比如：/opt/zbox/bin/mysql -u root -P 3306 -p zentao < zentao.sql）
        + linux数据库存储目录： /opt/zbox/data/mysql/zentao

    - 创建禅道用户，供外网访问
		- CREATE USER 'zentao' IDENTIFIED BY 'zentao';
		- GRANT ALL ON zentao.* TO 'zentao'@'%' IDENTIFIED BY 'zentao';
		- FLUSH PRIVILEGES;

<meta http-equiv="refresh" content="1.0">


CREATE USER 'zentao' IDENTIFIED BY 'zentao';
GRANT ALL ON zentao.* TO 'zentao'@'%' IDENTIFIED BY 'zentao';
FLUSH PRIVILEGES;