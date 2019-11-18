
## 
 [服务器安装教程](https://blog.csdn.net/qq_39135287/article/details/83474865)

##Do()

### SET GET expire

### MSET MGET
//批量设置 批量获取
//MSET key1 value1 key2 value2..
// MGET .key1 key2
### LPUSH
//LPUSH listkey value1 value2...
### HSET HGET
//Hash
//HSET bean feild1 value1 feild2  value2
//HGET bean feild1 feild2
## Send Flush Recevie
//Send：发送命令至缓冲区
//Flush：清空缓冲区，将命令一次性发送至服务器
//Recevie：依次读取服务器响应结果，当读取的命令未响应时，该操作会阻塞。

//客户端可以使用send()方法一次性向服务器发送一个或多个命令，
//命令发送完毕时，使用flush()方法将缓冲区的命令输入一次性发送到服务器，
//客户端再使用Receive()方法依次按照先进先出的顺序读取所有命令操作结果。

```golag
    conn.Send("HSET", "student","name", "wd","age","22")
    conn.Send("HSET", "student","Score","100")
    conn.Send("HGET", "student","age")
    conn.Flush()
    
    res1, err := conn.Receive()
    fmt.Printf("Receive res1:%v \n", res1)
    res2, err := conn.Receive()
    fmt.Printf("Receive res2:%v\n",res2)
    res3, err := conn.Receive()
    fmt.Printf("Receive res3:%s\n",res3)

```
