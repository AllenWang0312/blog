## Access denied for user 'root'...

mysql -uroot -p //登录
use mysql
select host,user from user;
GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY 'youpassword' WITH GRANT OPTION;
