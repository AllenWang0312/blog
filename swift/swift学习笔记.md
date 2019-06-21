##swift学习笔记


###Part3
####文档
###Part1

####集合
Array Dictionary<String,Int> Set


>
> /**
> - Parameters
>   - item1;
>   - item2:
> - Returns: 
> - Throws:
> -(Author,Authors,Copyright,Date,Since,Version)
> -(Precondition,Postcondition,Requires,Invariant,Complexity,Important,Warning,Attention,Note,Remark)
> */

//MARK: -Methods  为类视图添加分割线
//TODO: offer...  在类视图中添加TODO快速索引
//FIXME: 在类视图中添加FIXME快速索引 可以标注在方法体内部
###Part4
 概念 Subscripts Protocol Operator Overloading Delegation Extension Error Handling Nested Type Memory Management Generic Type Casting
 
 
 关键词 - repet{}while()
        - &(取地址)
        - init deinit
        - final(声明 此类没有任何子类 不可被继承)
        - convenience (声明 便利构造函数)
        - required (声明子类必须实现这个方法)
        - inout(修饰方法参数,表示该参数可以在方法体内部改变,一般没有返回值) 
        - mutating(结构体如果想改变自身 方法中要加)
        - subscript(索引:为结构体的属性添加下标) 
        - 
        - prefix postfix(重载运算符时 告诉编译器运算符作为前缀)
        - operator(声明自定义[]运算符)
        - infix operator(声明双目[左右]运算符) 
        - associativity(声明自定义运算符的结合性,left表示从左边开始连续相加)
        - precedence (声明运算符的优先级 0~255 140 加法 150 乘法)
        - extension(扩展类 可扩展方法 便利构造函数 计算型属性 嵌套类型[枚举 类..] 下标) 
        - typealias (别名)
        - associatedtype(协议内部需要用户在遵守协议的时候需要指定一个别名  )
        - @objc (当一个协议存在optional 的method时 需要暴露给c语言)
        - protocol (协议 类似java interface) 可以规定方法入参 表示入参需要同时实现多个协议
        - optional 子类可选实现
        - 
        - assert(1>0,"error message")断言
        - assertionFailure("")强制终止  都只在debug环境有效
        - precondition(1>0,"message")//相当于assert 可用于release
        - fatalError()
        -
        - try! try? do{}catch{}
        - defer
        - weak var T?   约等于 unowned  不可以是可选型
        - 捕获列表 闭包对self强引用 使用 {[unowned/weak self] value in  return self.oldValue} 解除强引用循环
        - is 
 特殊类
    - NSArray oc 数组 可以存放不同类的对象       
    - NSDate 表示时间
    - (包含func)Any>(可以看做是 void* 指针)AnyObject > NSObject > SwiftObject
 自定义运算符
 postfix operator +++{}
 infix operator ^{associativity left}
 