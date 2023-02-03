cd 工程目录
// 搜索
pod search + 库名
vim Podfile
// 写完之后安装就ok 
 :wq 保存退出
pod install

// 要更新的话
pod update

每次执行pod install 和pod update的时候，cocoapods都会默认更新一次spec仓库。这是一个比较耗时的操作。在确认spec版本库不需要更新时，给这两个命令加一个参数跳过spec版本库更新,可以明显提高这两个命令的执行速度。

pod install --verbose --no-repo-update
pod update --verbose --no-repo-update