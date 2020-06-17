# java基础

### 线程池好处 from 阿里PI

### 阻塞性IO 非阻塞性IO from 阿里PI

### arraylist linkedlist hashmap 使用场景 from 阿里PI

### hashmap线程不安全 from 阿里PI
what hashmap 在异步操作时是线程不安全的 
why hashmap 插入item的时候会有一个临界值 如果同时用两个线程去插入item 的时候 同时扩表 有可能导致一个线程的插入操作无效
how
1.替换成Hashtable，Hashtable通过对整个表上锁实现线程安全，因此效率比较低
2.使用Collections类的synchronizedMap方法包装一下。方法如下：
public static <K,V> Map<K,V> synchronizedMap(Map<K,V> m)  返回由指定映射支持的同步（线程安全的）映射
3.使用ConcurrentHashMap，它使用分段锁来保证线程安全，效率高，推荐使用




有用到过哪些算法
# android基础
service 启动方式
1. onCreate -> onStartCommand -> onDestroy
                     -> onStartCommand
2. onCreate -> onBind -> onUnbind -> onDestroy 
    activity       -> onServiceConnected
    
# 延伸
## android 应用可以多进程吗
## aidl
## 有看过框架源码吗  Retroft2  什么设计模式 glide

## android 模块化开发需要注意些什么

##从用户点击图标  到界面展示  都发生了什么

# 开发过程中有遇到过哪些影响深刻的bug

1. 直播SurfaceView 切换横竖屏 不会自动撑开 
    - 自定义SurfaceView 在 onMeasure里判断当前屏幕方向 设置宽高
2. 使用HTML.fromHtml 解析html 的时候 会将 < 识别成html 左标签 导致后面的字符无法展示
   富文本数据为老数据 其他地方可能引用 不可能转化为纯文本 只能让前端保存的时候 将< 转义成规范的格式 ;lt


   

