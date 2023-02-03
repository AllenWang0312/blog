## Android
Service 生命周期
* 多个地方bindService 一个地方unbindService service会被释放吗 为什么
不会 除非四大组件调用stopService 或者 service.stopSelf Service 只用在所有调用者unbind之后 才有可能被SystemServiceManager回收
* ANR 触发条件[](https://zhuanlan.zhihu.com/p/141203533)
    * 主线程对输入事件5s内没有处理完毕
    * 系统
    * cpu 资源耗尽
丢帧的原因 及如何排查
*
* 
### activity启动模式 举例 
* standard 每次调用 startActivity都创建
* singleTop 栈顶复用 onNewInstance activity内部fragment 可以通过startActivity传递参数 
* singleTask clean top 多activity 填写信息表单 最后一步确认
* singleInstance  小程序  

FLAG_ACTIVITY_NEW_TASK
FLAG_ACTIVITY_SINGLE_TOP
FLAG_ACTIVITY_CLEAR_TOP

### handler looper 机制原理  底层是如何绑定线程的

### MVC MVP MVVM
|||优点|缺点|
|---|---|---|---|
|MVC||1.业务逻辑都分离到Controller中,模块化程度高2.相对于mvp文件少更轻量|1.测试困难依赖View
|MVP||1.便于测试,Presenter对View操作 是通过接口方法调用 不依赖具体实现2.view不依赖model 复用性高|会生成很多模板文件 相较于MVVM 有大量的手动同步代码 维护困难
|MVVM||不需要手动同步view model 可维护性高2.测试简单 只需要保证Model正确性 View就正确|1.简单的图形界面不适用 2.数据绑定在 xml文件中 无法断点debug 布局文件没有复用性

面向对象六大原则
* 单一职责原则：一个类中应该是一组相关性很高的函数，数据的封装。两个完全不一样的功能就不应该放在一个类中。
* 开闭原则：对修改封闭，对扩展放开。
* 里氏替换原则：抽象和继承；所有引用基类的地方必须能透明的使用其子类的对象。
* 依赖倒置原则：抽象不应该依赖细节，细节应该依赖抽象。
* 接口隔离原则：将大接口改成多个小接口。
* 迪米特原则：也称为最少知识原则，一个对象应该对另一个对象有最少的了解。

### 事件分发

### 设计模式
1. 建造者模式 builder Dialog
2. 单例模式 ActivityManager AccessibilityManager
3. 原型模式 实现 Cloneable intent clone
4. 工厂方法 BitmapFactory 静态工厂
5. 策略模式 动画差值器 线程池创建
6. 责任链 触摸事件下发
7. 观察者模式 ListView adapter
8. 模板方法  AsyncTask Activity
9. 代理模式 WindowManagerImpl->WindowManagerGlobal
10. 装饰器模式 ContextThemeWrapper 
11. 外观模式 sdk 对外 api

## 双亲委派机制
## 热修复
#### 热修复方案
* NativeHook AndFix 直接在native层进行方法的结构体信息对换，从而实现完美的方法新旧替换，从而实现热修复功能。
    * 优点 即时生效    没有性能开销，不需要任何编辑器的插桩或代码改写
    * 缺点 1.存在稳定及兼容性问题。ArtMethod的结构基本参考Google开源的代码，各大厂商的ROM都可能有所改动，可能导致结构不一致，修复失败。2.无法增加变量及类，只能修复方法级别的Bug，无法做到新功能的发布
* Java Hook Robust 1.打基础包时插桩，在每个方法前插入一段类型为 ChangeQuickRedirect 静态变量的逻辑，插入过程对业务开发是完全透明2、加载补丁时，从补丁包中读取要替换的类及具体替换的方法实现，新建ClassLoader加载补丁dex。当changeQuickRedirect不为null时，可能会执行到accessDispatch从而替换掉之前老的逻辑，达到fix的目的
    * 优点 1.高兼容性（Robust只是在正常的使用DexClassLoader）、高稳定性，修复成功率高达99.9% 2.补丁实时生效，不需要重新启动3.支持方法级别的修复，包括静态方法4.支持增加方法和类5.支持ProGuard的混淆、内联、优化等操作
    * 缺点 1.代码是侵入式的，会在原有的类中加入相关代码2.so和资源的替换暂时不支持3.会增大apk的体积，平均一个函数会比原来增加17.47个字节，10万个函数会增加1.67M
* Java mulitdex Nuwa Hook了ClassLoader.pathList.dexElements[]，将补丁的dex插入到数组的最前端。因为ClassLoader的findClass是通过遍历dexElements[]中的dex来寻找类的。所以会优先查找到修复的类。从而达到修复的效果。
    * 优点 1.不需要考虑对dalvik虚拟机和art虚拟机做适配 2.代码是非侵入式的，对apk体积影响不大
    * 缺点 1.需要下次启动才修复2.性能损耗大，为了避免类被加上CLASS_ISPREVERIFIED，使用插桩，单独放一个帮助类在独立的dex中让其他类调用。
* dex替换 Tinker 提供dex差量包，整体替换dex的方案。差量的方式给出patch.dex，然后将patch.dex与应用的classes.dex合并成一个完整的dex，完整dex加载得到dexFile对象作为参数构建一个Element对象然后整体替换掉旧的dex-Elements数组。
    * 优点 1.兼容性高2.补丁小3.开发透明，代码非侵入式
    * 缺点 1.冷启动修复，下次启动修复2.Dex合并内存消耗在vm head上，容易OOM，最后导致合并失败
* 资源修复原理 instant Run 1.构建一个新的AssetManager，并通过反射调用addAssertPath，把这个完整的新资源包加入到AssetManager中。这样就得到一个含有所有新资源的AssetManager 2、找到所有值钱引用到原有AssetManager的地方，通过反射，把引用处替换为AssetManager
* so修复原理 接口调用替换 
    * 优点：不需要对不同sdk版本进行兼容，所以sdk版本都是System.loadLibrary这个接口
    * 缺点：需要侵入业务代码，替换掉System默认加载so库的接口
* 反射注入 补丁so库的路径插入到nativeLibraryDirectories数组的最前面
    * 优点：不需侵入用户接口调用
    * 缺点：需要做版本兼容控制，兼容性较差
##### Andfix
实效好 不需要重启
只能修复代码 不能修复资源及so库
##### Sophix 收费 通过类加载机制实现
适用性强 修复范围广 限制少
冷修复 需要重启app
##### Tinker 收费 基础版免费
##### Robust

## 插件化