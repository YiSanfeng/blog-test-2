# JS数组和JS函数
## 创建一个数组（数组是一种特殊的对象）
* 新建
1. let arr = [1,2,3]
2. let arr = new Array(1,2,3)
3. let arr = new Array(3)
### 类型VS类
* 类型
1. 类型是JS数据的分类，有7种
2. 四基两空一对象
* 类
1. 类是针对与对象的分类，有无数种
2. 常见的有Array、Function、Date、RegExp
### 数组对象
* 创建一个数组
1. let arr =[1,2,3]
2. let arr = new Array(1,2,3)//元素为1，2，3
3. let arr = new Array(3)//新数组长度为3
* 数组对象的自身属性
1. '0','1','2','length'
2. 属性名都是字符串，并没有数字
* 数组对象的共用属性
1. let arr1 = new Array(1,2,3)
2. push用法
<pre>
arr1.push(4) //添加数字4
arr1 = [1,2,3,4]
</pre>
3. pop用法
<pre>
arr1.pop() //弹出数组中上一个添加的元素
4
</pre>
4. shift用法
<pre>
arr1.shift()//会弹出数组里第一个元素
1
</pre>
5. unshift用法
<pre>
arr1.unshift(6)//将数字6添加为数组的第一个元素
[6,2,3]
</pre>
* join用法
<pre>
let arr2 = [6,6,6,6]
arr2.join('方') //数组中间用字符串'方'连接起来
[6方6方6方6方]
</pre>
## 函数对象
* 定义一个函数
1. function fn(x,y){return x+y}
2. let fn2=function fn(x+y){return x+y}
3. let fn = (x,y)=>x+y
4. let fn = new Function('x','y','return x+y')
* 函数对象自身属性
1. 'name'/'length'
## JS的数组不是典型的数组
* 典型数组
1. 元素的数据类型相同
2. 使用连续的内存储存
3. 通过数字下标获取元素
* 但JS的数组不这样
1. 元素的数据类型可以不同
2. 内存不一定是连续的（对象是随机存储的）
3. 不能通过数字下标，而是通过字符串下标
4. 这意味着数组可以有任何key
* 转化(字符串转化为数组)
1. let arr = '1,2,3'.split(',')
<pre>
得到['1','2','3']
</pre>
2. let arr = '123'.split('')
<pre>
得到['1','2','3']
</pre>
3. 把字符串编程数组：Array.form('1,2,3') //从什么地方得到一个数组
<pre>
得到['1','2','3']
</pre>
4. 理解：转化的前提是要有（0123）这样的下标或有length属性
5. 在
<pre>
let array = [1:'a',2:'b',3:'c',length:1]
array = [1:'a']
</pre>
转化过程中，如果下标和length的长度不一致，则采用length来转化数组的长度
6. 
* 伪数组
1. let divList = document.querySelectorAll('div')
2. 伪数组的原型链中并没有数组的原型
3. 没有数组共用属性的数组就是伪数组
* 合并两个数组，得到新数组
1. arr1.concat(arr2) //数组1连接数组2，合成一个新的数组，这个数组包含原来两个数组的内容
<pre> 
let arr1 = [1]
let arr2 = [2,2]
arr1.concat(arr2)
arr1 = [1,2,2]
</pre>
* 截取一个数组的一部分
1. arr5.slice(3) //括号内表示从哪个下标开始切（括号内的下标不会被切除）
<pre>
let arr5 = [1,2,3,4,5,6]
arr5.slice(3)
arr5 = [3,4,5,6]
切割完成后不会改变原来的数组
</pre>
1. arr6.slice(0)
<pre>
let arr6 = arr5.slice(0)//从第0个下标开始复制
arr5 = [1,2,3,4,5,6]
</pre>
3. JS只提供浅拷贝
## 删元素
* 跟对象是一样的操作（此法不推荐）
<pre>
let arr =['a','b','c']//设置一个数组，有abc三个元素
delete arr['0']//删除第一个下标元素（0是第一个）
arr = [empty,'b','c']//第一个元素虽然被删除，但是位置还保留着
delete arr[1]
delete arr[2]
arr = [empty * 3]//没有对应下标的数组叫做稀疏数组
</pre>
* length可以直接设置要保留的元素（此法不推荐）
<pre>
let arr = [1,2,3,4,5]
arr.length=1 //(只保留1个长度)
arr = [1] //只剩下第一个下标元素
不要随便用修改length的方法来修改数组的长度
</pre>
* shift法删除头部元素(会改变原数组)
<pre>
let arr = [1,2,3,4]
arr.shift() //（）里不用写东西，此法会删掉arr里的第一个元素
1 //返回被删除的元素
</pre>
* pop法删除尾部元素(会改变原数组)
<pre>
let arr = [1,2,3,4]
arr.pop() //（）里不用写东西，此法会删掉arr里的最后一个元素
4 //返回被删除的元素
</pre>
* 删除中间的元素
<pre>
let arr = [1,2,3,4]
arr.splice(2,2)//括号内第一个数表示从第几个下标开始删，第二个数字是删除几个元素。本句表示从第二个下标（含第二个），往后删除3个元素
arr = [1,4] //2，3倍删掉了
<pre>
或者arr.splice(2,1,666)//（从第二个下标（含），删除一个，改为新元素）
arr.splice(2,1,666,777,888)//添加新元素进当前数组,括号内第三个数字开始(含),就是新添加进去的数字
</pre>
</pre>

# 查看所有元素
* 查看所有属性名
<pre>
let arr = [1,2,3,4,5]
arr.x='xxx'
Object.keys(arr)
for(let i in arr){console.log(i)}
'1','2','3','4','5','x' //会打印出数组所有的属性
此方法不适用数组，多半适用于对象
</pre>
* 查看数字（字符串）属性名和值
<pre>
let arr = [1,2,3,4,5]
arr.x = 'xxx'
for(let i = 0,i < arr.length;i++){
    console.log(`${1} : ${[1]}`)
}
0:1
1:2
2:3
3:4
4:5//最后的x:xxx不会打印出来，因为循环不可能会加到x
</pre>
1. 自己要控制i 从0增长到length-1
<pre>
arr.forEach(function(xxx,yyy，zzz){
    console.log(`${xxx} : ${yyy}`)
   })
   //xxx表示数组的元素，yyy表示下标，zzz是数组本身（可加可不加）
</pre>
* for let 和 forEach的区别
1. for let 支持break，但forEach不支持
* 查看单个属性
# 查看单个属性
* 跟查看对象一样
<pre>
let arr = [111,222,333]//声明一个数组
arr[0]//查看数组的以一个下标属性
111
</pre>
* 索引越界
1. arr[arr.length]===undefined//访问了数组没有的属性
2. arr[-1] === undefined
* 举例
<pre>
for(let i = 0;i <= arr.length;i++){
    console.log(arr[i].toString())
}
</pre>
1. 报错：Canont read property 'toString' of undefined//意思是读取了 undefined的toString属性
* 查看某个元素是否在数组里
1. arr.indexOf(item)//（）里写你要查找的元素，存在就返回查找的元素的下标，否则就返回-1
2. 使用条件查找元素
<pre>
arr.find(function(x){
    return x%2===0)
    }）
    //返回第一个x除以2的余数为0的元素
  </pre>
3. 使用条件查找元素的索引
<pre>
find查找法（只返回对应的元素）：
let arr = [12,23,13,222,45,16]
arr.find(function(x)){
    return x%5 === 0//返回第一个是5的倍数的数字
}
45//返回值
</pre>
<pre>
findIndex查找法（返回符合条件元素的下标）：
arr.findIndex(function(x)){
    return x%2 === 0 //找到第一个偶数的索引下标
    }
</pre>
## 增加数组中的元素
* 在尾部增加元素
1. arr.push(newItem)//修改arr，返回新的长度（括号里写你要添加的内容）
2. arr.push(newItem1,newItem2)//修改arr，返回新长度
* 在头部增加元素
1. arr.unshift(newItem)//修改arr，返回新长度
2. arr.unshift(newItem1,newItem2)//修改arr，返回新长度
* 在中间添加元素
1. arr.splice(3,0,x)//在第三个下标删除0个元素，添加x
2. arr.splice(3,0,x,y)//在第三个下标删除0个元素，添加x和y
## 修改数组中的元素 
* 反转顺序
1. arr.reverse() //颠倒原数组的排序
* 自定义顺序
1. arr.sort用法
<pre>
let arr = [4,5,2,1,3]
arr.sort()
arr = [1,2,3,4,5]
</pre>
1. arr.sort自定义排序
<pre>
靠下标-1，0，1来判别
arr.sort(function(a,b){
    if(a>b){  //如果a大
        return 1 //下标1表示放到后面
    }else if(a===b){ 如果相等，位置不变
        return 0
    }else{ //如果a小
        return -1 //放到前面，下标-1在前
    }
})
</pre>
### 数组变换
* map（不会改变原数组）
1. n变n
<pre>
let arr = [1,2,3,4,5,6]
arr.map(item=>item*item)//item一一映射
(6) [1, 4, 9, 16, 25, 36]//得到的结果
</pre>
* filter（做筛选）（不会改变原数组）
1. n变少
<pre>
arr.filter(item => item%2 === 0)
(3) [2, 4, 6]//数组内的数字是2的倍数的结果
</pre>
* reduce（不会改变原数组）
1. n变1
<pre>
arr.reduce((sum,item)=>{return sum+item},0) //sum的初始值的0，然后依次且每次让初始值和数组元素相加，相加后改变sum，直到加完为止
</pre>
<pre>
arr.reduce((a,b)=>{return a.concat(b*b)},[])//用reduce的方式实现数组元素平方
</pre>

