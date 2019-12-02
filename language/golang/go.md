
## 常见问题



1. golang.org/x/sys/unix: unrecognized
    ```shell
        $cd ~/go/src
        $mkdir -p golang.org/x
        $cd golang.org/x
        $git clone https://github.com/golang/sys.git
    ```
2. golang.org/x/net: unrecognized 
    ```shell
      $mkdir -p $GOPATH/src/golang.org/x/
      $cd $GOPATH/src/golang.org/x/
      $git clone https://github.com/golang/net.git net
      $go install net
    ```

## 编译可执行文件

    ```shell
        $set GOOS=linux
        $set GOARCH=and64
        $go build
    ```
