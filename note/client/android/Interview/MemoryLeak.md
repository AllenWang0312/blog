特殊的
1. webview 
 长期占用内存 activity 销毁后 调用 destory()
当webview callback 持有 activity 引用时 造成webview内存无法释放  先将webview从父容器中移除 再销毁webview
2. 广播注册与反注册 数据库关闭
``线程类``
3. 定时器 生命周期比activity长 thread timer timertask
4. Thread 子线程持久化 Thread直接被GC Root 持有 激活状态的线程 都会持有外部类
  自定义asynctask 在activity生命周期结束时 cancel掉
5. handler msg 持有activity 引用 
    Activity销毁时就将mHandler的回调和发送的消息给移除掉。
6. 属性动画 结束前退出activity 同上

通用的
* 静态变量 生命周期和application 一样长  尽量减少使用
* 非静态内部类 声明为静态内部类
* 静态drawable drawable 会持有view的引用 view会持有上下文
* 静态集合中对象没清理造成的内存泄漏
* 单例模式  持有activity 导致activity不能被回收  换成applicationcontext
