

### 示例代码
栈stack  堆heap

  ```objectivec
  @interface RPoint//内存 指针分配在栈上 指向堆中的内存地址保存值
  @property (原子性atomic/nonatomic)int x self.x
  @property(readonly) NSString y
  @property(weak) Empolee e
  @property(copy) Empolee e//赋值时拷贝内存再赋值   操作不会影响原对象
  -(void)print;
  + (void) log; 类型方法 相当于静态方法
  @end
    
    typedef struct{//定义typedef 结构体(值)struct 内存直接分配在栈上
    int x;
    int y; 
    }SPoint;
    
    int main(int argc,const char * argv[]){
        @autoreleasepool{//自动回收
         RPoint* rp1 = [[RPoint alloc]init]//分配内存alloc 初始化init
         
        SPoint sp1;//(不需要手动初始化)
        sp1.x=10
        sp1.y=20
        }
        return 0
    }
    ```
### 关键字 
0. import <第三方类库> "自己写的文件"
1. .h 声明接口interface 接口属性 property 
2. .m 实现implementation class(对象)
3. objectc  



### 类型系统
1. 引用类型 reference type
    * 类 class
    * 指针 pointer 
    * 块 block 
2. 值类型 value type
    * 基础数值类型
    * 结构 struct
    * 枚举 enum
3. 类型装饰
    * 协议 protocol
    * 类别 category
    * 扩展 extension