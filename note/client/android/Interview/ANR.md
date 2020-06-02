## 造成ANR 的原因有哪些
1. 主线程阻塞 开辟子线程执行耗时任务
activity/fragment 主线程阻塞5s
service 阻塞10s
2. cpu满负荷 i/o 阻塞 文件读写/数据库操作在主线程 开辟子线程异步执行
3.  内存不够用 排查内存泄漏 使用largeheap

## 哪些地方是执行在主线程的
1. Activity的所有生命周期回调都是执行在主线程的.
2. Service默认是执行在主线程的.
3. BroadcastReceiver的onReceive回调是执行在主线程的.
4. 没有使用子线程的looper的Handler的handleMessage, post(Runnable)是执行在主线程的.
5. AsyncTask的回调中除了doInBackground, 其他都是执行在主线程的.
6. View的post(Runnable)是执行在主线程的.

## 如何开启子线程
1. Thread  设置更低的优先级  防止任然阻塞ui Process.setThreadPriority(THREAD_PRIORITY_BACKGROUND);
2. Runable
3. AsyncTask
4. HandlerThread 
5. IntentService
6. Loader cursorloader