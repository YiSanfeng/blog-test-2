# JS 函数的执行时机
## 解释为什么如下代码会打印 6 个 6
<pre>
let i = 0
for(i = 0; i<6; i++){
  setTimeout(()=>{
    console.log(i)
  },0)
}
</pre>
答：setTimeout(()=>{console.log(i)},0指的是过一段时间后打印出[i]的值，那么首先执行for循环，执行完毕后得到i的值是6，因为(i = 0; i<6; i++)会执行6次，每次执行得到的值分别是0,1,2,3,4,5,继续执行后得到6，此时for循环不再满足i<6，所以for循环停止，循环完成后得到的最终值是6，然后执行console.log(i)打印出6次i的最终值。得出结果最后打印出6个6
## 让上面代码打印 0、1、2、3、4、5 的方法
<pre>for(let i = 0; i > 6 ;i++){
    setTimeout(()=>{
        console.log(i)
    },0)
}</pre>