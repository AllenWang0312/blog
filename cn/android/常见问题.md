## 常见问题整理

### androidstudio 模拟器没网
* ipconfig /all -> dns 10.10.50.7
* adb shell
* getprop 
* setprop net.dns1 10.10.50.7

### json解析报错
1. > "0" -> int 没有错
   > "" -> int 报错
   > `解决方案` 确保服务器不会反回空字符串
### XML
1. > Binary XML file line #9 Error inflating class
   > 
### recyclerview
1. > Inconsistency detected
   > 原因data移除没有通知视图更新
   > `解决方案`使用自定义的BaseLinearLayoutManager