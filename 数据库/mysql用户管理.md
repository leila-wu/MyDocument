### 查看用户数据
SELECT User, Host, Password FROM mysql.user;

SELECT * FROM mysql.user where user='test';

### 创建用户
- 方法一
```
insert into mysql.user(Host,User,Password) values("localhost","test",password("123"));

insert into mysql.user(Host,User,Password) values("%","test",password("123456"));

insert into mysql.user(Host,User,Password) values("192.168.35.215","test",password("123456"));
```
- 方法二
```
CREATE USER 'test' IDENTIFIED BY '123456';
```

### 给用户授权数据库权限
- 授权用户在本机拥有zentao数据库的所有权限
```
GRANT ALL ON zentao.* TO 'test'@'localhost' IDENTIFIED BY '123';
```

- 授权用户在其他机器拥有zentao数据库的查询权限（为了让帐号在任何地方登录，必须两个帐号都存在
```
GRANT select on zentao.* to 'test'@'%' identified by '123456';
GRANT select on zentao.* to 'test'@'192.168.35.215' identified by '123456';
```

- 授权用户拥有数据库的所有权限，且不限制登录服务器
```
grant ALL ON zentao.* to 'zentao'@'192.168.35.215' identified by '123456';
```
- 刷新系统权限表
```
flush privileges;
```
- 查看用户授权
```
show grants for 'test'@'%';
show grants for 'zentao'@'192.168.1.22';
```
### 删除用户
- 通过delete删除用户，删除成功后再新增同名用户会失败
```
DELETE FROM user WHERE User="phplamp" and Host="localhost";
```
- 通过drop删除用户，删除成功后可以新增用户 
```
drop user 'test'@'192.168.187.1';
```

- 删除成功，需要刷新权限表
```
flush privileges;
```

### 修改用户
#### 修改用户权限
- update 
```
update mysql.user set password=password('123456') where User="test" and Host="%";
```
#### 修改用户密码
- update用户表
```
update mysql.user set password=password('新密码') where User="test" and Host="localhost";
```
- alter用户表
```
alter user 'test'@'%' identified by '123456';
```
- 操作完成后，需要刷新权限表
```
flush privileges;
```

### 异常处理
禅道授权完成后，设置其他服务器登录报错。
```
ERROR 2003 (HY000): Can't connect to MySQL server on '192.168.10.210' (111) 
```

原因分析：
禅道配置了访问限制，找到opt/zbox/etc/mysql/my.cnf  把 bind-address= 127.0.0.1注释，然后重启禅道即正常访问。




<meta http-equiv="refresh" content="1.0">