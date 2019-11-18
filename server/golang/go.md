
## 常见问题
1. golang.org/x/sys/unix: unrecognized
    ```shell
        cd ~/go/src
        mkdir -p golang.org/x
        cd golang.org/x
        git clone https://github.com/golang/sys.git
    ```
2. 
  

## 编译可执行文件
```shell
set GOOS=linux
set GOARCH=and64
go build
```
