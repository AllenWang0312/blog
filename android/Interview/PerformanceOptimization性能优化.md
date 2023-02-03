## 通用优化
* 体积瘦身
    * 混淆

* 启动优化
    * 业务动作,耗时操作
* 绘制优化
* 内存优化
    * 静态变量,
开启okhttp * gson gzip压缩

# 性能优化
### 彩谱
爆炸物检测
#### 技术点
``优化不优雅的实现``
4. 因为要展示sqlite可配置的显示数据  使用动态生成行 来作为Excel item
``收获 对数据操作有了新的认识  对性能敏感 追求极致``
#### 优化点
* [内存优化]图像还原算法 使用尽可能小的基础数据类型进行运算 而不是封装类型 argb 尽可能使用基本数据类型计算  结果可预计的情况下尽可能使用 量程小的数据类型 依次 byte8 short16 int32 long64 flout double (char string)
* [计算加速]区域范围 圆形->方形 爆炸物检测 区域判断不再使用圆形计算范围 减少浮点计算 加快检测时间
* [重连优化]缓存蓝牙设备信息 加速重连
#### 未落地
使用线程池 为每个区域执行判断任务
[计算加速]使用jni 调用颜色模型转换算法

### 言川
#### 技术点 
1. 和后端协商使用自json+定义元素 展示表单 
* ``epub lrc解析``
#### 优化点
* 头像 base64压缩
* 大文件多线程异步下载 合并  网速为瓶颈时提升不大
* [绘制优化]悬浮动画 gif -> lottile 
* [绘制优化]日历控件 是用viewpager 加 1000个 item 生成的 RecyclerView +  ArrayList 动态加载更多
#### 未落地
2. 开屏插画 预缓存  节假日插画  缓存json wifi条件下下载 资源包

### 东方网升
#### 技术点
#### 优化点
* [省流]边下边播 
* [启动优化] 推迟第三方sdk初始化时间(地图ipo)  Application MainActivity 减少onCreate方法工作量(布局复杂度 层级 耗时操作)  
* [绘制优化] 图标 png->svg
* [省流]接口本地 文件缓存 每个证书课程一般不会变动  本地缓存课程列表json  + 版本号 课程更新的时候 同时修改版本号
#### 未落地
* [内存优化] 首页多个recyclerview 存在样式一样的 item 复用同一个RecycledViewPool
* [接口key精简]

### 中软国际
## Conference&MediaSDK
* [美颜预览偶现闪退] 美颜预览退出没有release rtcEngine导致会议拿到的rtcEngine与基座美颜预览拿到的是同一个对象 退出会议会release rtcEngine再进入美颜预览的话 调用已经被释放资源的rtcEngine.startPreview闪退
* [使用体验优化]不到万不得已不申请敏感权限
    1. 去除 进入【会议】或【预览】页面之前的权限请求，即 发起会议 加入会议 列表加入 详情加入 四处入口去除权限申请，统一进入【会议/预览】页面申请
    2. 根据基座设置 动态获取最小权限
## DanmuSDK

## IMDSK
* modulestate 统一
* 数据结构优化 
* 登陆冲突信令 和 websocket断开回调 无法保证前者先执行
    * 加时延
    * websocket断开时携带断开原因
    * websocket 断开生成一个自定义事件 放到下发队列里执行
* 登陆重连时 连错了
* [拉黑的用户发消息一直转圈圈] 带err 的 TextMessage 跨站场景下  走到了 多端下发场景  被当成未完成消息丢弃了  

### protobuf

### 涉及到的数据结构
* CountDownLatch
* ConcurrentHashMap  
    线程安全的HashMap 多线程性能比较好
* CopyOnWriteArrayList
* ConcurrentLinkedQueue 
    并发非阻塞
* ConcurrentLinkedQueue使用约定：
    1:不允许null入列
    2:在入队的最后一个元素的next为null
    3:队列中所有未删除的节点的item都不能为null且都能从head节点遍历到
    4:删除节点是将item设置为null, 队列迭代时跳过item为null节点
    5:head节点跟tail不一定指向头节点或尾节点，可能存在滞后性
* LinkedBlockingDeque  
    * 支持双向并发插入取出
    * 支持FIFO FILO
    * 可选容量的(防止过度膨胀)
* PriorityBlockingQueue
    无界队列 可以一直添加  每次添加都会排序 
* LinkedHashMap

### 项目业务实现 
  项目使用netty提供的websocket 和 protobuf 实现端侧 IM 功能
   对外封装 handler 使用户可以通过handler 

* 一个module 对应一个 handler 可能会产生多个connection 
* KeyIndex 端到端加密
* 
* Sender 和connection 一一对应 
* Resolver 和connection 一一对应 
* Dispatcher 全局单例
    * 优势 占用系统资源整体可控 只用一个线程池
    * 劣势 所有module 走统一个下发线程池 性能瓶颈
    * 改成 handler 成员变量的好处  
        * 特殊命令处理 登陆冲突可以 单独


#### 项目介绍
彩谱科技
介绍一下 
1. 维护之前一款配合蔬菜质检仪器使用的app
2. 独立开发配合测量颜色的仪器使用的app(蓝牙 2.0 4.0升级 jdbk sqlite 上传mysql)无服务器 只有阿里云数据库 ^加密mysql秘钥
3. 新疆中科院 合作项目 独立开发配合爆炸物检测的仪器使用的app(蓝牙 2.0 4.0升级 蓝牙 4.0 连接速度慢 换回蓝牙2.0  usb数据传输协议(图像信息传输  打印机驱动) 图像还原算法 本地存储)
4. 使用android4.4 开发板 launcher 开发台式仪器嵌入式终端(驱动移植 系统裁剪 )


[言川教育] 

[世尊慈航] 

### 内存调优 内存回收算法 from 阿里PI

### 如何保证应用高可用性 不出现内存泄漏 from 阿里PI

内存优化 
    大量数据计算时  使用基本数据类型  不使用封装类型
    确保(引用大量资源的线程) asy task handler 生命周期小于activity  及时回收  避免造成内存泄漏  如果是全局任务可以封装到service 中
    图片按需加载  自定义缓存级别
    io 操作  或者 数据库操作  及时关闭资源/游标
    尽量少使用 static 的变量  会一直占用内存
    第三方sdk 在需要的时候再初始化
数据优化

异步线程上传图片

大数据   tensorflow  机器人
NAS 个人媒体库  android TV 手机

   