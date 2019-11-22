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
//启动redis 服务器
/usr/local/redis-5.0.6/bin/redis-server /usr/local/redis-5.0.6/etc/redis.conf

### netstat
        -r, --route                display routing table
        -I, --interfaces=<Iface>   display interface table for <Iface>
        -i, --interfaces           display interface table
        -g, --groups               display multicast group memberships
        -s, --statistics           display networking statistics (like SNMP)
        -M, --masquerade           display masqueraded connections
 
        -v, --verbose              be verbose
        -n, --numeric              don't resolve names
            --numeric-hosts            don't resolve host names
            --numeric-ports            don't resolve port names
            --numeric-users            don't resolve user names
        -N, --symbolic             resolve hardware names
        -e, --extend               display other/more information
        -p, --programs             display PID/Program name for sockets
        -c, --continuous           continuous listing
 
        -l, --listening            display listening server sockets
        -a, --all, --listening     display all sockets (default: connected)
        -o, --timers               display timers
        -F, --fib                  display Forwarding Information Base (default)
        -C, --cache                display routing cache instead of FIB
        -T, --notrim               stop trimming long addresses
        -Z, --context              display SELinux security context for sockets 
-lntp
-apn 
### |grep 8080(http服务器) 6379(redis服务器) 3306(mysql)
### kill -9 23608

cd /home/wpc/products/netimg
### nohup ./main
