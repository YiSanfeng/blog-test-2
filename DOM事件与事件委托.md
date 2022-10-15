# DOM事件与事件委托
## 面试题：请简述 DOM 事件模型或 DOM 事件机制
* 答：
1. 捕获：
<pre>
捕获可以理解为是从父元素依次找到子元素的一个过程
</pre>
2. 冒泡：
<pre>
冒泡可以理解为是从子元素依次找到父元素的一个过程
</pre>
3. 捕获和冒泡谁先执行？
<pre>
一律是捕获先执行，然后执行冒泡，且捕获不可中断或取消，但冒泡不同，它可以中断或取消
</pre>
## 面试题：简述事件委托
* 答：
1. 当我们需要监听一万个元素的时候，那么我们不可能添加一万个监听器，这样会浪费9999个监听器的内存，这时候可以用一个方法省去这9999个监听器的内存，这个方法就是监听这一万个元素的祖元素；还有一个情况可以使用监听祖元素的方法，那就是需要监听目前不存在的元素的时候，我们监听祖元素，然后在点击所要监听的元素的时候，进行一个判断，看是不是我们需要监听的元素
## 【下方为学习笔记】
## 绑定事件Api
1. IE 5*
<pre>
x.attachEvent('onclick',fn) //冒泡
</pre>
2. 网景
<pre>
x.addEventListener('click',fn) //捕获
</pre>
3. W3C
<pre>
x.addEventListener('click',fn,bool) //不填或falsy，bool默认为IE冒泡，填写true认为是网景捕获
</pre>
</pre>

## target 与 currentTarget
* 区别
1. e.target - 用户操作的元素
2. e.currentTarget  - 程序员监听的元素
3. this 是 e.currentTarget，不推荐使用

* 捕获不可以取消，冒泡可以
1. e.stopPropagation()可中断冒泡，浏览器不再向上走
2. 通俗来讲：有人打我，我自己解决，别告诉我老子
3. 一般用于封装某些独立的组件
## 事件的特性(用bool来确定)
1. Bubbles表示是否可以冒泡
2. Cancelable表示是否支持开发者取消冒泡
3. 如scroll不支持取消冒泡
### 如何阻止滚动
* scroll 事件不可取消冒泡
1. 阻止scroll默认动作没用，因先有滚动才有滚动事件
2. 要阻止滚动，可阻止wheel和touchstart的默认动作
3. 注意需要找准滚动条所在的元素
4. 但是滚动条还能用，可用CSS让滚动条
<pre>
::-webkit-scrollbar{
    width:0 ! important
}
</pre>
* CSS也行
1. 使用overflow：hidden可以直接取消滚动条
2. 但此时JS依然可以修改scrollTop