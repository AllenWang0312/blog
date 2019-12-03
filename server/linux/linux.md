
122.51.205.29
5IViitVRy7xq54P
Wq!_mYVissM-A5a

nohup ./main > nohup.out 2>&1 &  
nohup ./main_file > nohup_file.out 2>&1 &
# shell
关机：
　　shutdown -h now  #立刻关机重启，工作中常用
　　shutdown -h +1    #1分钟后关机
　　init 0
　　halt                        #立即停止系统，需要人工关闭电源
　　halt -p                    #
　　poweroff　　　　  #立即停止系统，并且关闭电源
重启：
　　reboot　　　　　　#工作中常用
　　shutdown -r now      #工作中常用
　　shutdown -r +1　　 #一分钟后重启
　　init 6
注销：
　　logout
　　exit　　　　　　#工作中常用
　　ctrl+d　　　　　#工作中常用
vmstat：用以检测CPU和内存情况 
    -f //显示从系统启动至今的fork数量
    -s //查看内存使用的详细信息
    -d //查看磁盘的读/写
iostat：用于检测磁盘状态 
netstat：用于检测带宽状态
    -an | grep 2158//查看进程路径
    -lntp
    -apn 
### 白名单
polkitd
nobody


                             




SYN_SENT 请求连接
TIME_WAIT
FIN_WAIT1 主动要求关闭tcp连接
## swap
//if 表示infile，of表示outfile，bs=1024代表增加的模块大小，count=16384000代表16384000个模块，也就是16G空间
dd if=/dev/zero of=/var/swap bs=1024 count=16384000
mkswap /var/swap
mkswap -f /var/swap
swapon /var/swap
free -m
cat /proc/swaps

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

## 
 [服务器安装教程](https://blog.csdn.net/qq_39135287/article/details/83474865)
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

### |grep 8080(http服务器) 6379(redis服务器) 3306(mysql)
### kill -9 23608

cd /home/wpc/products/netimg
### nohup ./main
