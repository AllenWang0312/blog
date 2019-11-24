##python
###语言特点：
* 方法也是对象，方法可以返回方法（类似js）
###基本数据类型 
字符串 ‘’“” 都可以
Boolean True False
空 None
声明基本数据类型的变量不需要关键字

No运算符 and or not

语法 
if u1<u2:
        return -1;
    if u1>u2:
        return 1;
return 0

命令
Print ‘100+200’，100+200
\n 表示换行
\t 表示一个制表符
\\ 表示 \ 字符本身
#不需要转义的字符串
r'\(~_~)/ \(~_~)/'
#多行字符串
'''Line 1
Line 2
Line 3'''


注释 #
定义方法 def add（x,y,f）:
return 0

基本函数 

range(1,101);
?返回一个前包后不包的数组
sorted([1,2,5,7,3,5,7],reversed_cmp)
对数组进行排序 reversed_cmp传入两个参数 x,y 若x应该在y左边则返回1，反之返回-1
math.sqrt()
开根号
char.upper() char.lower(
英文字符转大写 小写
strip()
删除字符串中的元素，没有参数则删除空格
高阶函数
map(f,[1,2,3,4])
根据变换依次操作一个数组 返回一个新的数组 包括所有元素变换后的值

reduce(f,[1,2,3,4])
依次执行f(1,2) 并将结果带入到下一次计算f(f(1,2),3)….
filter(is_odd,[1,4,6,7,9,12,17])
对所有元素过滤，判断标准为is_odd(合格返回True的函数)
