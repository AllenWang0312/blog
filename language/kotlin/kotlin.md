#kotlin学习笔记

存疑关键词:

anko  inline 内联函数  sealed 封装类 data数据类 运算符重载 中缀表达式
>示例代码
~~~
//open 代表这个类可以被继承 
class open Person(private var name: String) {

    private var description: String? = null
    
    init {
        name = "Zhang Tao"
    }

    constructor(name: String, description: String) : this(name) {
        this.description = description
    }
    //internal访问范围为模块 不写表示public 
    internal fun sayHello() {
        println("hello $name")
    }
}
~~~
##基本语法
~~~ 
var price: Double = 20.3

~~~
### in关键字
~~~
if(x in 1..y-1) //如果x 在区间内

if(x!in 0..array.lastIndex) //x不在array中

for(x in 1..5) //从1 到 5


~~~
###when
~~~(java)
fun cases(obj: Any){
 when (obj){
    1          -> print("--")  //obj==1
    "hello"    -> print("--")//obj.eques("hello")
    is Long    -> print("--") //obj instances of Long
    !is String -> print("--") //obg !instance of String
    else       -> print("--")  //default
 } 
}
~~~
### 空值检测
~~~
println(files?.size) //只会在files不为空时执行
   data?.let{ }  //
~~~

### 函数
~~~
关键字  函数名 形参   类型  返回值类型
fun     say   (str: String):String {
return str
}
~~~
~~~
//等同于
fun say (str: String);String = str
~~~
~~~
//加上默认值
fun say (str: String = "hello"):String =str
~~~
~~~
//vararg 表示多参数 下面类似于 java String...
fun hasEmpty(vararg strArray:String?):Boolean{
for(str in strArray){
if("".equals(str)\\str==null)
return true
}
return false
}
~~~
####Unit 
函数也是对象 类似 javascript {  }
 Unit 代表{ return;} 空函数  什么也不会发生
####Nothing
如果一个方法的返回值为Nothing 类型 通常在返回之前必然报错 
####嵌套函数
~~~
fun function() {
  val valuesInTheOuterScope = "Kotlin is awesome!"
  
  fun theFunctionInside(int: Int = 10) {
    println(valuesInTheOuterScope)
    if (int >= 5) theFunctionInside(int - 1)
  }
  theFunctionInside()
}
~~~
与内部类有些类似，内部函数可以直接访问外部函数的局部变量、常量，这种写法通常使用在 会在某些条件下触发递归的方法内，在一般情况下是不推荐使用嵌套函数的。


###扩展函数
~~~
fun Activity.toast(message: CharSequence, duration: Int = Toast.LENGTH_SHORT){
Toast.makeText(this,message,duration).show()
}
~~~
###将函数作为参数
~~~
fun lock<T>(lock: Lock,body:() -> T): T {
lock.lock()
try{
return body()
}finally{
lock.unlock()
}
}
~~~
##运算符重载
~~~
fun main(args: Array<String>) {
  for (i in 1..100 step 20) {
    print("$i ")
  }
}
这段函数将会输出 1 21 41 61 81
~~~

##java kotlin 混编
~~~
var str = some?.s?.d?:"" //混淆会报错
var str = some?.s?.d?: String() //这样可以混淆
~~~
###kotlin 中调用java
如果一个 Java 方法返回 void，对应的在 Kotlin 代码中它将返回 Unit。关于 Unit，本书将在 第五章函数部分着重讲解。 
现在你只需要知道在Java 中返回为 void 的函数，在 Kotlin 中可以省略这个返回类型。

###关键字冲突
Java 有 static 关键字，在 Kotlin 中没有这个关键字，你需要使用@JvmStatic替代这个关键字。
同样，在 Kotlin 中也有很多的关键字是 Java 中是没有的。例如 in,is,data等。如果 Java 中使用了这些关键字，需要加上反引号(`)转义来避免冲突。

###java调用kotlin

在 Kotlin 中没有 static关键字,那么如果在 Java 代码中想要通过类名调用一个 Kotlin 类的方法，你需要给这个方法加入@JvmStatic注解

~~~
object StringUtils {
    @JvmStatic fun isEmpty(str: String): Boolean {
        return "" == str
    }

    fun isEmpty2(str: String): Boolean {
        return "" == str
    }
}
~~~
~~~
class StringUtils {
    companion object {
       fun isEmpty(str: String): Boolean {
	        return "" == str
	    }
    }
}
~~~
companion object表示外部类的一个伴生对象，你可以把他理解为外部类自动创建了一个对象作为自己的field。
与上面的类似，Java 在调用时，可以这样写：StringUtils.Companion. isEmpty();
关于伴生对象

###包级别函数
与 Java 不同，Kotlin 允许函数独立存在，而不必依赖于某个类，这类函数我们称之为包级别函数(Package-Level Functions)。
为了兼容 Java，Kotlin 默认会将所有的包级别函数放在一个自动生成的叫ExampleKt的类中， 在 Java 中想要调用包级别函数时，需要通过这个类来调用。 
当然，也是可以自定义的，你只需要通过注解@file:JvmName("Example")即可将当前文件中的所有包级别函数放到一个自动生成的名为 Example 的类中。
###空安全性
在 Java 中，如果你调用的 kotlin 方法参数声明了非空类型，如果你在 Java 代码中传入一个空值，将在运行时抛出NullPointerException。其内部原因在于 Kotlin 为每个非空类型加了断言，如果传入空值则会立刻抛出异常。 
同样，如果你使用 null 对象去调用一个 kotlin 方法，将会立刻抛出NullPointerException（就算是调用普通 java 方法也是一样会抛出 NullPointerException ）