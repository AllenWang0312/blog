## JNI 项目学习总结




### jni 常用方法

```cpp
// 将赋值取值方法封装成工具类
//im_utils.h
setJavaXXXFieldValue
getJavaObjXXXFieldValue
static jobject createJavObj(const jclass &paramCls, JNIEnv* &env)
{
    if (!paramCls)
    {
        LOGE("error paramCls");
        return NULL;
    }
    jmethodID constr = env->GetMethodID(paramCls, "<init>", "()V");
    if (!constr)
    {
        LOGE("error constr");
        return NULL;
    }

    jobject value = env->NewObject(paramCls, constr);
    if (!value)
    {
        LOGE("error init java object");
        return NULL;
    }
    return value;
}
//JNIEnv
env->NewObject(cls,methodID...) //创建 cls 实例 一般调用 <init> 方法
env->GetMethodID(cls,fucName,sig) // ()I 无参返回值为int (Ljava/lang/Object;)Z 有一个String类型参数 返回值为 bool V代表void
env->GetFieldID(cls,fieldName,sig)
env->GetXXXField(obj,field)
env->SetXXXField(obj,field,cvalue)


jfieldID fieldID = env->GetFieldID(cls,fieldName, "Ljava/lang/String;");//string
jfieldID fieldID = env->GetFieldID(cls,fieldName, "I");//int
jfieldID fieldID = env->GetFieldID(cls,fieldName, "Z");//bool
jfieldID fieldID = env->GetFieldID(cls,fieldName, "D");//double
jfieldID fieldID = env->GetFieldID(cls,fieldName, "J");//long




// onLoad 时 初始化常用class
JNIEXPORT jint JNICALL JNI_OnLoad(JavaVM *vm, void *reserved){
    JNIEnv *env;
    if (vm->GetEnv((void **)&env, JNI_VERSION_1_6) != JNI_OK){
        return -1;
    }
    g_jvm = vm;
    //是否有必要缓存
    int length = sizeof(java_Entities)/sizeof(java_Entities[0]);//计算字符串数组长度

    for (int i = 0; i < length; i++) {
        jclass cls=env->FindClass(java_Entities[i]);
        g_JavaParamClass[ENUM_JAVA_ENTITY(i)] = (jclass)(env->NewGlobalRef(cls));
    }
    LOGI("java_Entities.length = %d",length);
    return JNI_VERSION_1_6;
}

// unload 删除引用
JNIEXPORT JNICALL void JNI_OnUnload(JavaVM *vm, void *reserved){
    JNIEnv *env;

    if (vm->GetEnv((void **)&env, JNI_VERSION_1_6) != JNI_OK){
        return;
    }

    int length = sizeof(java_Entities)/sizeof(java_Entities[0]);
    for (int i = 0; i < length; i++) {
       env->DeleteGlobalRef(g_JavaParamClass[ENUM_JAVA_ENTITY(i)]);
    }

    LOGE("jni unload");

    if (callBackImpl){
        delete callBackImpl;
        callBackImpl = nullptr;
    }
    LOGE("jni unload 2");
    env->DeleteGlobalRef(g_IMHandlerJavaObj);
}
//定义 java 主接口类 
public native int login(String,boolean)
//自动生成 native-lib.cpp 对应方法

//主回调类实现约定方法回调
OnXXXXX
    void call2Java(const char* functionName, const char* sig, int paramCount,const RETURN_JOBJ_FUNC_TYPE &func)
    {
        int status;
        JNIEnv *env = NULL;
        bool isAttached = false;

        status = g_jvm->GetEnv((void **)&env, JNI_VERSION_1_6);

        if (status < 0)
        {
            status = g_jvm->AttachCurrentThread(&env, NULL);

            if (status < 0) {
                return;
            }

            isAttached = true;
        }

        jclass javahandlerCls = env->GetObjectClass(g_IMHandlerJavaObj);
        if (!javahandlerCls) {
            LOGE("can't find g_Handler class");
            if (isAttached) {
                g_jvm->DetachCurrentThread();
            }
            return;
        }
        LOGI("call functionName: %s, sig: %s", functionName, sig);
        jmethodID methodID = env->GetMethodID(javahandlerCls, functionName, sig);

        if (!methodID) {
            LOGE("error methodID");
            if (isAttached) {
                g_jvm->DetachCurrentThread();
            }
            env->DeleteLocalRef(javahandlerCls);
            return;
        }
        jobject* value = func(env);
        if (!value) {
            LOGE("error value");
            if (isAttached) {
                g_jvm->DetachCurrentThread();
            }
            env->DeleteLocalRef(javahandlerCls);
            return;
        }

        switch (paramCount) {
            case 1:
                env->CallVoidMethod(g_IMHandlerJavaObj, methodID, value[0]);
                break;
            case 2:
                env->CallVoidMethod(g_IMHandlerJavaObj, methodID, value[0], value[1]);
                break;
            case 3:
                env->CallVoidMethod(g_IMHandlerJavaObj, methodID, value[0], value[1], value[2]);
                break;
            default:
                LOGE("Error paramCount");
                if (isAttached) {
                    g_jvm->DetachCurrentThread();
                }
                env->DeleteLocalRef(javahandlerCls);
                delete[]value;
                return;
        }

        env->DeleteLocalRef(javahandlerCls);

        if (isAttached)
        {
            g_jvm->DetachCurrentThread();
        }
        delete []value;
    }

// 
```