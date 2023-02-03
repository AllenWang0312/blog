```mermaid
%% 时序图例子,-> 直线，-->虚线，->>实线箭头
  sequenceDiagram
    participant at as ActivityThread
    participant a as Activity
    participant pw as PhoneWindow
    participant li as LayoutInflater
    activate at
    loop: performLauchActivity()
        at->at: ->创建Activity 如果异常直接报错
        at->at: ->创建Application 
        at->-a: ->activity.attach
    end
 
    a->pw:attach() mWindow = new PhoneWindow
    a->a:setContentView()
    a->pw: getWindow().setContentView
    pw->>li: mLayoutInflater.inflate() pull 解析加载根布局

    loop: 根据xml name 是否包含. 判断是自定义view还是系统view
        li->li:rInflate 解析每个xml标签
        li->li: createViewFromTag() 根据name 反射生产view onCreateView生产自定义 -> createView生产原生 缓存构造方法 找不到 反射调用 构造方法(context上下文 attrs属性集)
        li->li: 添加到parent
        li->li: 假装view是viewgroup 递归调用 rInflateChildre() -> rInflate() 是view的话内部没有标签自动结束循环 是viewGroup的话则继续根据name反射出实例添加到parent 所有xml解析完 返回root根节点 完成java bean 树创建
    end
```
<a href = 'http://aospxref.com/android-8.1.0_r81/xref/frameworks/base/core/java/android/app/ActivityThread.java#2686'>app = ActivityClientRecord.PackageInfo.makeApplication</a>
<a>activity = Instrumentation.newActivity</a>

```mermaid
%% 时序图例子,-> 直线，-->虚线，->>实线箭头
  sequenceDiagram
    participant at as ActivityThread 
    participant wmi as WindowManagerImpl
    participant wmg as WindowMangerGlobal
    participant vri as ViewRootImpl
    at->at: handlerResumeActivity
    at->>wmi: wm.addView(DecorView)
    wmi->>wmg: addView()
    wmg->>vri: setView()
    vri->vri:requestLayout()
    vri->vri:scheduleTraversals()
    vri->vri:doTraversal()
    vri->vri:performTraversals()

```