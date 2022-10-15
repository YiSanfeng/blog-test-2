# JS数据类型
## 二进制
* 10转2
 <pre>x=y*2^5+y*2^4+y*2^3+y*2^2+y*2^1+y*2^0</pre>

* 2转10
1. 从右往左（最右边是第0位），第几位就乘2的几次方，然后加起来即可
2. 除0以外的任何数的0次方都得0
## 用十六进制表示二进制
1. 用8421从右往左对应xxxx
2. 8421代表2^3+2^2+2^1+2^0
3. 十六进制数字排序：0、2、3、4、5、6、7、8、9、a、b、c、d、e、f
4. 计算器程序员模式：HEX表示16进制，BIN表示2进制，OCT表示8进制，DEC表示10进制

## JS中的数据类型
* 7种（大小写无所谓）（前六种属于简单类型，后一种属于复杂类型）
1. 数字 number
2. 字符串 string
3. 布尔 bool
4. 符号 symbol
5. 空 undefined
6. 空 null
7. 对象 object、
8. 四基两空一对象
* 以下不是数据类型
1. 数组、函数、日期
2. 它们都属于object
## 转义
1. \'表示'
2. \"表示"
3. \n表示换行
4. \r表示回车
5. \t表示tab制表符
6. \ \表示\
7. \uFFFF表示对应的Unicode字符
8. \xFF表示前256个Unicode字符
## 通过下标读取字符（举例）
1. let s = 'hello'
2. s[0] // "h"
3. s[1] // "e"
4. s[4] // "0"
5. 字符的第一位的下标从0开始算
## base64 转码
1. 转码写法：<pre>window.atob('要转的内容')</pre>
2. 反编码写法：<pre>window.btoa('要转的内容')</pre>
## 五个falsy值（相当于false但又不是false的值）
1. 分别是undefined、null、0、NaN、''
2. <pre>if(hello){ //这里的hello就是真值，如果是真值就会执行当前花括号里的内容
    }else{ //如果if后面的圆括号内是undefined、null、0、NaN、''这些假值，就会跳过if后面的内容，然后去执行else里花括号
    }
## 变量声明var、let、const
* 三种声明方式
1. var a = 1
2. let a = 1
3. const a = 1
4. a = 1
* 区别
1. var是过时的、不好用的方式（此方式不允许用）
2. let（变量声明时用）是新的，更合理的方式
3. const（常量声明时用）是声明时必须赋值，且不能再改的方式
4. 最后这种方式是错误的，不准这样声明
### let声明
* 规则
1. 遵循块作用域，即使用范围不能超出{}
2. 不能重复声明
3. 可以赋值，也可以不赋值
4. 必须先声明在使用，否则报错
5. 全局声明的let变量，不会编程window属性，这点与var相反
6. for循环配合let有奇效
### const声明
* 规则
1. 跟let几乎一样
2. 只有一条不一样：声明时就要赋值，赋值后不能更改（一次赋值就定死）
## 类型转换
* number转string（以n为例）
1. String（n）//注意是大写
2. n + ''（把n加上一个空的字符串，此法前端程序员常用方法）
* string转number（以s为例）
1. Number（s）
2. s -0（此法前端程序员常用方法）
3. +s（此法前端程序员常用方法）
4. parseInt(s)/parseFloat(s)
* x=>bool(以x为例)
1. Boolean(x)
2. !!x
* x=>string
1. String(x)
2. x.toString() //1..toString合法，1.toString不合法，因为JS认为1.是个小数，后面会接数字
## 对象object
* *定义
1. 是无序的数据集合
2. 键值对的集合（键和值组成一对）
3. 键名(也叫属性名key)是字符串，不是标识符，可以包含任意字符
4. 引号可以省略（非英文的特殊字符不建议省略），省略之后就只能写标识符
5. 就算引号省略了，键名也还是字符串（重要）
6. Object.keys(obj)可以得到所有的obj的所有key
* *写法
1. <pre>let obj={'name':'frank','age':'18'}</pre>
2. <pre>let obj=new Object({'name':'frank'})
  console.log({'name':'frank','age':'18'})</pre>
## 变量做属性名
* 如何用变量做属性名
1. 之前都是用常量做属性名
2. let p1='name'
3. let obj={p1:'frank'}这样写，属性名为'p1'
4. let obj={[p1]:'frank'}这样写，属性名为'name'
* 对比
1. 不加[ ]的属性名会自动变成字符串
2. 加了[ ]则会当作变量求值
3. 值如果不是字符串，则会自动变成字符串
# 对象的增删改查
## 
### 删除属性(delete只能用来删除属性)
* delete obj.xxx或delete obj[ 'xxx' ] (同时删除属性名和属性值)
* obj.xxx=undefined（没有删除属性名，只删除了属性值）//此方法不适用于查看当前对象是否存在这个属性，因为就算没有这个属性JS也是不会报错的，想查看就要用in
* 查看对象里是否存在某个属性名
1. 'xxx' in obj ===false（不存在）/true（存在）
* 'xxx' in obj && obj.xxx===undefined
1. 注意obj.xxx===undefined
### 查看属性
* 查看自身所有属性
1. 查看所有keys:Object keys(xxx)
2. 查看所有值（values）:Object values(xxx)
3. 查看所有属性（keys）和值（values）:Object entries(xxx)
* 查看自身+共有属性
1. console.dir(xxx)
* 判断一个属性是自身的还是共有的
1. obj.hasOwnProperty('toString')
* 两种方法查看属性（新人推荐使用中括号法）
1. 中括号语法：obj[ 'key' ]
2. 点语法：obj.key
#### 补充点
1. <pre>obj.name等价于obj.['name']</pre>
2. <pre>obj.name不等价于obj.[name]</pre>
* 注释：<pre>[] 里的'name'是字符串，而[]里的name是变量，所以不相等</pre>
3. <pre>let name = 'frank'
   obj[name]等价于obj['frank']
   因为已经声明了变量name等于字符串'frank'</pre>
### 写属性
* 直接赋值
1. let obj = {name: 'frank'}// 是字符串
2. obj.name = 'frank'//name是字符串
3. obj[ 'name' ]='frank'
4. obj['na' + 'me']='frank'
5. let key = 'name';obj[ key ]= 'frank'

* 批量赋值<pre>Object.assign(obj,{age:18,gender:'man'})</pre>
### 修改或增加共有属性
* 无法通过自身修改或增加来改变共有属性（如果进行此操作，只会在自身对象里修改或增加此属性，并不会影响共有属性）
1. let obj={},obj2={}//共有toString
2. obj.toString='xxx'只会更改obj自身属性
3. obj2.toString还是在原型上，toString的值并不是'xxx'
### 修改隐藏属性
1. 不推荐使用__proto__(会降低性能)
2. 推荐使用Object.create
* <pre>
  let common(name='frank') //首先增加一个变量，并声明他的属性
  let obj=Object.create(common) //引用common的属性作为obj的原型
  </pre>
* 注释：规范大概的意思是，要改就一开始就改，别后来再改

