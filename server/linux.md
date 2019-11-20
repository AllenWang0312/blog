# shell

## yum

 yum list installed
 yum list tomcat //查找可以安装的软件包

 yum (-y)install ..//-y 自动应答所有
 yum info ..
 yum remove ..
 yum deplist .. //列出软件包的依赖
 
 systemctl start mariadb
 systemctl enable mariadb
 mysql_secure_installation
 
## nohup

  nohup /root/test.php &   //不挂断的运行程序  同时把程序运行的输出信息放到当前目录的nohup.out 文件中去

## 常用命令 
netstat -apn |grep 8080(http服务器) 6379(redis服务器) 3306(mysql)
kill -9 23608

cd /home/wpc/products/netimg
nohup ./main


//启动redis 服务器
/usr/local/redis-5.0.6/bin/redis-server /usr/local/redis-5.0.6/etc/redis.conf