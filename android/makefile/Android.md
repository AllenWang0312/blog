### Framework知识点
* [ ] init.rc 语法

### shell 常用命令
```shell
touch file/path 更新文件修改时间 使得系统重新编译该模块
```
### c语言基础
静态库（库程序是直接注入目标程序的，不分彼此，库文件通常以.a结尾
动态库（库程序是在运行目标程序时（中）加载的，库文件通常以.so结尾）

### 简单案例
```makefile
LOCAL_PATH:=$(call my-dir) #定义当前模块的相对路径

include $(CLEAR_VARS) 

LOCAL_MODULE:=test #模块名

LOCAL_SRC_FILES:=test.c \
                test1.c
LOCAL_MODULE_PATH:=$(LOCAL_PATH) #指定生成.so的目标目录
include $(BUILD_EXECUTABLE) #编译为可执行文件 test
#include $(BUILD_SHARED_LIBRARY)
#include $(BUILD_STATIC_LIBRARY)
 #编译为动/静态库 libtest.so
```
* [my-dir](build/core/definitions.mk)
* #清除除LOCAL_PATH的所有变量          
    * [CLEAR_VARS](build/core/config.mk)
    * $([BUILD_SYSTEM](build/core/main.mk))/clear_vars.mk

### 动态获取源文件

```makefile
LOCAL_C_ALL_FILES:=$(call all-c-files-under) #拿到当前目录下所有c文件
LOCAL_SRC_FILES:=$(LOCAL_C_ALL_FILES)

```
### 编译两个库
```makefile
LOCAL_PATH:=$(call my-dir) 
include $(CLEAR_VARS) #由此复制一份即可
LOCAL_MODULE:=test #修改module name
LOCAL_SRC_FILES:=test.c #源代码
LOCAL_MODULE_PATH:=$(LOCAL_PATH) 
include $(BUILD_EXECUTABLE) 

include $(CLEAR_VARS) 
LOCAL_MODULE:=test1
LOCAL_SRC_FILES:=test.c 
LOCAL_MODULE_PATH:=$(LOCAL_PATH) 
include $(BUILD_EXECUTABLE) 
```

### 库引用
#### 系统库
```c
#include <utils/Log.h>
extern void call_test(void);
int main(void)
{
    call_test();
    ALOGE("test");
    return 0;
}
```
### 第三方库 方法一
```makefile
LOCAL_SRC_FILES:=...
LOCAL_SHARED_LIBRARIES += liblog #引入系统库
LOCAL_LDFLAGS:= -L./库路径/ -l库名字 #引入第三方库文件
```
### 第三方库 方法二
```c
#include <utils/Log.h>
#include "../inc/test1.h"
int main(void)
{
    call_test();
    ALOGE("test");
    return 0;
}
```
### 第三方库 方法三
```makefile
LOCAL_C_INCLUDES:=$(LOCAL_PATH)/inc# 指定头文件路径
```
```c
#include <test1.h>
```
### 编译生成apk
```makefile
LOCAL_PATH:=$(call my-dir)
include $(CLEAR_VARS)
LOCAL_SRC_FIRES:=$(call all-subdir-java-files)
LOCAL_PACKAGE_NAME:=localpackage #编译生成apk名字
include $(BUILD_PACKAGE)#编译生成apk
```
* [ ] [实战]学习系统应用源代码 
packages/apps/Calculator/Android.mk
### 编译生成jar包
```makefile
LOCAL_PATH:=$(call my-dir)
include $(CLEAR_VARS)
LOCAL_SRC_FILES:=$(call all-subdir-java-files)
LOCAL_MODULE:=com.test.myjar
include $(BUILD_STATIC_JAVA_LIBRARY) #编译成静态jar包 使用.class文件打包 可以在任何java虚拟机运行
# include $(BUILD_JAVA_LIBRARY) #编译成共享jar包 在静态jar包基础上使用.dex打包而成 只能被android识别
```
### 编译包含jar包的apk
```makefile
LOCAL_PATH:=$(call my-dir)
include $(CLEAR_VARS)
LOCAL_STATIC_JAVA_LIBRARIES:= static-library #声明包含某jar包
#LOCAL_JAVA_LIBRARIES:=share-library
LOCAL_SRC_FILES:=$(call all-subdir-java-files)
LOCAL_PACKAGE_NAME:=localpackage
include $(BUILD_PACKAGE)
```
### 预编译jar包
```makefile
LOCAL_PATH:=$(call my-dir)
include $(CLEAR_VARS)
LOCAL_MODULE_CLASS:=JAVA_LIBRARIES #指定编译生成文件类型 dex归档文件
# APPS apk文件 SHARED_LIBRARIES 动态库文件 EXECUTABLES 二进制文件 ETC 其他文件格式
LOCAL_MODULE:=com.test.share

LOCAL_SRC_FILES:=com.test.static
include $(BUILD_PREBUILT)# 预编译
```
```makefile
ifeq($(VALUE),x)#ifneq
else
endif
```
