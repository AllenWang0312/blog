
全站？

前端

vue.js 






服务
node.js
node.js 三方库

jade

express

nodemon

移动
reactnative


工具库

jQuery



基本数据类型:
number string boolean null undefined
object: function array data 
对象中的每个变量 都具有writable enumerable configurable value 
[[proto]]:原型 
[[class]]:表示对象是属于什么种类
[[extensible]]:表示对象是否允许继续添加属性(标签) 
get/set(方法) 

var str=”string”
[1,2]   =   new Array(1,2)
[1,,,4]   =    [1,undefined,undefined,4]
{x:1,y:2}  =   var o=new Object();
               o.x=1,o.y=2;
             o[‘x’]==1==true
方法
var fe =function(){};
(    function(){console.log(‘hello world’);})   )();

创建无参数方法可省略()
new Func(1,2);
new Object;

void 算作一元运算符  永远返回 undefined
var val=(1,2,3);  //val=3  将依次传入数字

delete obj.x  将obj对象x属性置空  undefined
Object.defineProperty(obj,’x’,{configurable:false,value:1})//定义obj的x属性不可更改,值为1
delete obj.x//false
obj.x==1
‘x’ in obj;//true  判断obj是否有x属性
{} instanceof Object //true
typeof 100 //返回字符串 ‘number’

function Foo(){}
Foo.prototype.x=1;
var obj =new Foo();
obj.x==1
obj.hasOwnProperty(‘x’);//false  不是对象的属性而是原型链上的
]//true  通过_proto_拿到原型
var a=b=1;会使b成为全局变量  最好写作var a=1,b=1;

for(p in obj){   //无顺序,原型链enumerable为false不可使用for in
}   
严格模式 ‘use strict’ 
在一个模块下用’use strict’; 使用严格模式执行代码 修复部分语言不足,提供更强的错误检查,并增强安全性
with({x:1}){ Console.log(x);  }//with加对象可在{}中直接使用对象的某个属性,不需要.连接 严格模式会无法编译   已经不建议使用

未申明的变量被赋值 相当于创建了一个全局变量 在严格模式下会报语法错误

!function(a){   //定义一个方法对象
Arguments[0]=100;  //将参数列表第一项设置为100   严格模式不会影响参数a的值(参数Console.log(a);  //为对象的话例外)
}(1);  //参数为1
如果没有传参数 a=undefined 对参数[0]修改操作无效

delete 参数在普通模式下不会报错,返回false删除失败,严格模式会报SyntaxError
delete 不可配置的属性同上
Object.defineProperty(obj,’a’,{fonfigurable:false});delete obj.a//false
对象属性名重复在严格模式下会报错
严格模式不准出现形如0123 的八进制数
严格模式 方法体中eval argument 会变成关键字 不能作为变量或函数名
eval(‘var evalVal=2’); 普通模式下 evalVal可以在当前作用域拿到,严格模式会返回undefined 
