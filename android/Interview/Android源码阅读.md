
### 系统源码
#### recyclerview  
* mAttachedScrap mChangedScrap 
* mCachedViews DEFAULT_CACHE_SIZE =2 从屏幕上完全移除的viewHolder 
* mViewCacheExtension 自定义缓存
* mRecyclerPool DEFAULT_MAX_SCRAP = 5 如果mCachedViews 
#### imageloader


### 第三方源码阅读 
### glide 
使用添加不可见fragment 来感知生命周期
LruCache 算法
* Glide.with
    * 创建Glide实例
    * 获取RequestManager
* requestManager.load
    * 获取RequestBuilder
    * 生成Request
* request.into
    * 生成 Target
    * 调用 request.begin 启动加载请求
    * 调用 Engine.load 加载请求
    * 构建EngineJob 使用线程池启动 DecodeJob
    * 通过原始数据选取合适的ModelLoader
    * 使用DateFetcher 加载原始数据
    * 使用编码器将数据写入本地文件缓存
    * 根据原始数据类型 选用合适的解码器
    * 将原始数据按照图片大小以及Option按需加载
    * 将资源缓存至内存缓存
    * 将图片设置到imageView上

#### LeakCanary 
1. 利用ContentProvider 无需显示初始化特性来实现自动注册
2. 通过 registerActivityLifecycleCallbacks 对Activity生命周期进行监听
3. 当Activity销毁时 将Activity添加到一个WeakReference中 去ReferenceQueue中观察是否成功回收
4. 调用Android原生提供的dump方法 捕获堆栈log Debug.dumpHprofData(meapDumpFile.absolutePath)
5. 使用解析库来分析heap dump 文件

#### okhttp 
通过系统核心数来动态设置最大并发线程
根据业务需求来设置同一domain最大并发数 .setMaxRequestsPerHost(8); 
Call  Dispatcher
1. 创建client
2. 创建request client.call(request)
3. RealCall 调用 enqueue异步请求 excuture 同步请求
4. Dispatcher 通过三个队列管理请求 
    * 如果runningAsync count <64 并且 同host的正在请求call个数<5 加入线程池执行  ArrayDeque 循环链表 比linkedArrayList 快
    * 其他情况加入ready队列 等待running中完成时 判断是否有符合条件的call 可以加入running执行
    * 通过设置线程池 SynchronousQueue 来立即执行添加进来的任务 
##### OkHttpClient
这个是整个OkHttp的核心管理类，所有的内部逻辑和对象归OkHttpClient统一来管理，它通过Builder构造器生成，构造参数和类成员很多，这里先不做具体的分析。
##### Request 和Response
Request是我们发送请求封装类，内部有url, header , method，body等常见的参数，Response是请求的结果，包含code, message, header,body ；这两个类的定义是完全符合Http协议所定义的请求内容和响应内容。
##### RealCall
负责请求的调度（同步的话走当前线程发送请求，异步的话则使用OkHttp内部的线程池进行）；同时负责构造内部逻辑责任链，并执行责任链相关的逻辑，直到获取结果。虽然OkHttpClient是整个OkHttp的核心管理类，但是真正发出请求并且组织逻辑的是RealCall类，它同时肩负了调度和责任链组织的两大重任，接下来我们来着重分析下RealCall类的逻辑。
RealCall类并不复杂，有两个最重要的方法，execute() 和 enqueue()，一个是处理同步请求，一个是处理异步请求。跟进enqueue的源码后发现，它只是通过异步线程和callback做了一个异步调用的封装，最终逻辑还是会调用到execute()这个方法，然后调用了getResponseWithInterceptorChain()获得请求结果。

* client.interceptors
* RetryAndFollowUpInterceptor
    * 当请求内部抛出异常时，判定是否需要重试
        * 规则1: client的retryOnConnectionFailure参数设置为false，不进行重试
        * 规则2: 请求的body已经发出，不进行重试
        * 规则3: 特殊的异常类型不进行重试（如ProtocolException，SSLHandshakeException等）
        * 规则4: 没有更多的route（包含proxy和inetaddress），不进行重试
    * 当响应结果是3xx重定向时，构建新的请求并发送请求
* BridgeInterceptor
    * 负责把用户构造的请求转换为发送到服务器的请求 、把服务器返回的响应转换为用户友好的响应，是从应用程序代码到网络代码的桥梁
    * 设置内容长度，内容编码
    * 设置gzip压缩，并在接收到内容后进行解压。省去了应用层处理数据解压的麻烦
    * 添加cookie
    * 设置其他报头，如User-Agent,Host,Keep-alive等。其中Keep-Alive是实现连接复用的必要步骤
* CacheInterceptor
    * 通过Request尝试到Cache中拿缓存，当然前提是OkHttpClient中配置了缓存，默认是不支持的。
    * 根据response,time,request创建一个缓存策略，用于判断怎样使用缓存。
    * 如果缓存策略中设置禁止使用网络，并且缓存又为空，则构建一个Response直接返回，注意返回码=504
    * 缓存策略中设置不使用网络，但是又缓存，直接返回缓存
    * 接着走后续过滤器的流程，chain.proceed(networkRequest)
    * 当缓存存在的时候，如果网络返回的Resposne为304，则使用缓存的Resposne。
    * 构建网络请求的Resposne
    * 当在OkHttpClient中配置了缓存，则将这个Resposne缓存起来。
    * 缓存起来的步骤也是先缓存header，再缓存body。
    * 返回Resposne
* ConnectInterceptor
    * 
* client.networkInterceptors
* CallServerInterceptor
    * 向服务器发送 request header
    * 如果有 request body 向服务器发送
    * 读取 response header 构造Response
    * 如有 response body 在3的基础上构建新的response
### [Retrofit](https://zhuanlan.zhihu.com/p/226076809)
注解运行时生成代理类处理网络接口调用
1. 使用builder 配置 baseUrl/httpclient /gson 解析器/
2. 使用注释编写 网络接口
3. retrofit.create(Api::class.jave) 创建动态代理 Proxy
4. 在invocationhandler.invoke 中处理具体请求
    1. 通过ServiceMethod.parseAnnotations创建httpServiceMethod 
    2. 全局缓存httpServiceMethod 方便复用
    3. 调用httpServiceMethod.invoke 根据配置及解析的注解 创建okhttpCall 并调用
    4. OkhttpCall 内部创建okhttp.Call okhttp.Request 并请求网络 
    5. 在OkhttpCall enqueue 内部对response做解析 返回通过json解析生成的java bean

#### RxJava
#### EventBus 
#### ARouter

