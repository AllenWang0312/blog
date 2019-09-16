## ubuntu环境
【Ubuntu如何修改swap大小】(https://blog.csdn.net/qq_16597625/article/details/83514912)
## 常见问题
1. sudo chmod 777 -R ... 获得...及所有子文件修改权限

1. as install-snap change in progress
> snap changes \
> sudo snap abort 5

## snap 一些常用的命令

其实使用snap包很简单，下面我来介绍一下一些常用的命令

1. sudo snap list
列出已经安装的snap包

2. sudo snap find <text to search>
搜索要安装的snap包

3. sudo snap install <snap name>
安装一个snap包

4. sudo snap refresh <snap name>
更新一个snap包，如果你后面不加包的名字的话那就是更新所有的snap包

4. sudo snap revert <snap name>
把一个包还原到以前安装的版本

6. sudo snap remove <snap name>
删除一个snap包
