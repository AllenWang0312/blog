## nginx 安装
1. 安装依赖包
    //一键安装上面四个依赖
    yum -y install gcc zlib zlib-devel pcre-devel openssl openssl-devel
2. 下载并解压安装包
    //创建一个文件夹
    cd /usr/local
    mkdir nginx
    cd nginx
    //下载tar包
    wget http://nginx.org/download/nginx-1.13.7.tar.gz
    tar -xvf nginx-1.13.7.tar.g
3. 安装nginx
    //进入nginx目录
    cd /usr/local/nginx-1.13.7/nginx
    //执行命令
    ./configure
    //执行make命令
    make
    //执行make install命令
    make install
4. 配置nginx.conf
    //打开配置文件
    vi /usr/local/nginx/nginx-1.13.7/conf/nginx.conf
    将端口号改成8089，因为可能apeache占用80端口，apeache端口尽量不要修改，我们选择修改nginx端口。
    localhost修改为你服务器ip地址。

5. 启动nginx
    /usr/local/nginx/sbin/nginx -c /usr/local/nginx/conf/nginx.conf
    /usr/local/nginx/sbin/nginx -s reload
    //查看nginx进程是否启动：
    ps -ef | grep nginx


6. 关闭防火墙
    若想使用外部主机连接上虚拟机访问端口192.168.131.2，需要关闭虚拟机的防火墙：
    centOS6及以前版本使用命令： systemctl stop iptables.service
    centOS7关闭防火墙命令： systemctl stop firewalld.service
    随后访问该ip即可看到nginx界面。

 

7. 访问服务器ip查看

## 常用命令
vi /usr/local/nginx/conf/nginx.conf

安装完成一般常用命令

进入安装目录中，
命令： cd /usr/local/nginx/sbin

启动，关闭，重启，命令：

/usr/local/nginx/sbin/nginx 启动
/usr/local/nginx/sbin/nginx -s stop 关闭
/usr/local/nginx/sbin/nginx -s reload 重启