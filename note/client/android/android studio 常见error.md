Error:SSL peer shut down incorrectly

gradle 版本问题

 解决 Android N 7.0 上 报错：android.os.FileUriExposedException

http://blog.csdn.net/yy1300326388/article/details/52787853

### Error:SSL peer shut down incorrectly
* 原因: gradle 版本问题
* 解决: 改为本地gradle 

###解决 Android N 7.0 上 报错：android.os.FileUriExposedException
* 原因: 7.0文件访问权限
* 解决: http://blog.csdn.net/yy1300326388/article/details/52787853

### unable to find valid certfication path to requested target
* 原因: 找不到部分库
* 解决: 复制已有项目project build.gradle repositories

### This project uses AndroidX dependencies, but the 'android.useAndroidX' property is not enabled. Set this property to true in the gradle.properties file and retry.
gradle.properties
添加 android.useAndroidX=true
NonExistentClass???????Annotation
    @error.NonExistentClass()
    