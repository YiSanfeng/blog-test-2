# JS函数
## 定义一个函数
* 具名函数
<pre>
function 函数名(形式参数1，形式参数2){
    语句
    return 返回值
}
</pre>
* 匿名函数
1. 
<pre>
function (形式参数1，形式参数2){
    语句
    return 返回值
}
相比具名函数缺少一个函数名
</pre>
2. 
<pre>
let a = function(x,y){return x+y}
</pre>
1. 等于号左边是将某某赋值，等于号右边也叫函数表达式
* 箭头函数
1.  
<pre>
let f1 = x => x*x
</pre>
2. 
<pre>
let f2 = (x,y) => x+y //圆括号不能省
</pre>
3. 
<pre>
let f3 =(x,y) => {return x+y} //花括号不能省
</pre>
4. 
<pre>
let f4 = (x,y) => ({name:x,age:y}) //直接返回对象会出错，需要加个圆括号
</pre>
5. 
<pre>
let f = (x,y)=>{
console.log('hi')
    return x*y
}
</pre>
## 函数的要素
* 调用时机
1. 
<pre>
let i = 0
for(i=0;i< 6;i++){
    setTimeout(()=>{
        console.log(i)
    },0)
}
会打印出6个6
</pre>
2. 
<pre>
for(let i = 0;i< 6;i++){
    setTimeout(()=>{
        console.log(i)
    },0)
}
把 let i=0放在圆括号里面的时候，每次循环会多创建一个i
</pre>
* 作用域
1. 要点：就近原则
* 闭包
<pre>
function f1(){
    let a = 1
    function f2(){
        let a = 2           //
        function f3(){      //
            console.log(a)  //左边的a和f3组成了闭包
        }                   //
        a = 22
        f3()
    }
    console.log(a)
    a = 100
    f2()
}
//如果一个函数用到了外部的变量，那么这个函数加这个变量就叫做闭包
</pre>
* 形式参数
* * 形式参数的意思就是非实际参数
<pre>
function add(x,y){
    return x+y
}
//其中 x 和 y 就是形参，因为并不是实际的参数add(1,2)
//调用 add 时，1 和 2 是实际参数，会赋值给 x y
</pre>
* 形参的本质就是变量声明
//上面代码近乎等价于下面代码
<pre>
function add(){
    var x = arguments[0]
    var y = arguments[1]
    return x+y
}
//比上面代码麻烦，需要多声明 x 和 y 
//形参可以不全部声明完，可以在后面声明一个arguments
</pre>
* 返回值
* * 每个函数都有返回值
* 
1. 递归函数
<pre>
function f(n){
    return n !==1 ? n* f(n-1) : 1
}
</pre>
2. 理解递归
<pre>
f(4)
= 4 *  f(3)
= 4 * (3 * f(2))
= 4 * (3 * (2 * f(1)))
= 4 * (3* (2 * (1)))
= 4 * (3* (2))
= 4 * (6)
24
</pre>
* 调用栈
1. JS引擎在调用一个函数前
2. 需要把函数所在的环境推push到一个数组里
3. 这个数组叫做调用栈
4. 等函数执行完了，就会把环境弹pop出来
5. 然后return 到之前的环境，继续执行后续代码
* 函数提升
* * 什么是函数提升
1. function fu(){}
2. 不管你把这个函数写在什么位置，他都会跑到第一行
<pre>
add(1,2)
function add(x,y){  //函数永远会跑到第一行
    return x+y
}
</pre>
* arguments (除了箭头函数没有)
<pre>
代码：
function fn(){
    console.log(arguments)
    console.log(this)
}
</pre>
* * 如何传arguments
1. 调用fn即可传arguments
2. fun(1,2,3)那么arguments就是[1,2,3]数组
* this
1. 如果不给任何的条件，this默认指向window
* * 如何传this
1. 目前可以用fn.call(xxx,1,2,3)传this和arguments
2. 而且xxx会被自动转化为对象
### this的两种使用方法
* 隐式传递
1. fn(1,2) //等价于fn.call(undefined,1,2)
2. obj.child.fn(1) //等价于obj.child.fn.call(obj.child,1)
* 显示传递
1. fn.call(undefined,1,2)
2. fn.apply(undefined,[1,2])
* 立即调用时机
1. 
<pre>
function fn(){
    var a = 2
    console.log(a)
}
</pee>
<pre>
- function (){   //取消全局函数fn
    var a= 2
    console.log(a)
}()            //立即调用这个隐式函数
</pre>