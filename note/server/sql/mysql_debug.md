## Access denied for user 'root'...

mysql -uroot -p //登录
use mysql
select host,user from user;
GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY 'qunsi003' WITH GRANT OPTION;

## 2013-Lost connection to MySQL server
    1. vi /etc/my.cnf
    追加
    2. skip-name-resolve
    保存退出，并重启mysql服务：
    3. service mysqld restart 