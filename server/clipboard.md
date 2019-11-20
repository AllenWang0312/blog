
shell

netstat -apn |grep 8080(http服务器) 6379(redis服务器) 3306(mysql)
kill -9 23608

cd /home/wpc/products/netimg
nohup ./main



//启动redis 服务器
/usr/local/redis-5.0.6/bin/redis-server /usr/local/redis-5.0.6/etc/redis.conf
