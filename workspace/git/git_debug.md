

## 常见问题
1. the remote end hung up unexpectedly

    工程>.git>config> append
    [http]
    postBuffer = 524288000
    或者
    git config --global http.postBuffer 524288000 //1048576000

