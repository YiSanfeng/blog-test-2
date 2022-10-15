# CSS定位
## 一、盒模型回顾（从外到内排序）
1. margin(外边距)
2. border(边框)
3. padding(内边距)
4. content(内容)

## 二、如何查看背景的范围是哪到哪？
答：给border的框子设置成半透明验证。
    
    border:1px soild rgba(255,0,0,0.1)；

## 三、一个div的分层（从下到上）
1. 文字内容(不论是哪个元素内的文字，后出现的文字会在先出现的文字上面)
2. 内联子元素
3. 浮动元素(脱离文档流div{float:left})
<pre>float：left脱离文档流之后会比普通的div高一层</pre>

4. 块级子元素(div)
5. border
6. background
## 四、position
1. static 默认值，待在文档流里(文档流中本来的样子，基本上不写)
2. relative 相对定位，升起来，但不脱离文档流
##### 使用场景：
* <pre>用于作为位移(很少用)<pre>top:10px/left:10px</pre></pre>

* <pre>配合z-index使用:<pre>z-index:auto默认值，不创建新的层叠上下文</pre><pre>z-index:0/1/2(正数表示在背景上层，正数越大越上)</pre><pre>z-index:-1/-2(负数表示在背景下方，负数越大越下)</pre></pre>

* <pre>用于给absolute元素做爸爸:<pre>在absolute的父亲元素里要加上{position:relative},让儿子(absolute)元素可以找到父亲(relative)元素</pre></pre>
3. absolute 绝对定位，定位基准是祖先里的非static<pre>需要在父元素里加(position:relative)，他会找祖先元素里最近一个被定位的（(position:relative)）祖先元素进行定位
##### 使用场景：
* <pre>脱离原来的位置，另起一层，比如对话框的关闭按钮</pre>
* <pre>鼠标提示：<pre>button span{display:none;}(此操作让按钮的提示不显示)</pre><pre>button:hover span{display:inline-block;}(按钮被悬浮的时候，它的按钮提示就会显示)</pre></pre>
* <pre>让字体不换行:<pre>white-space</pre></pre>
4. fixed 固定定位，定位基准是viewport(视口)(会因为其他元素而改变自身特性)
<pre>.fixed{display:fixed}</pre>

* 手机上不要用fixed，会有无数的bug
5. sticky 粘滞定位
* 会像excel冻结窗口一样，将此元素冻结在第一行
* 得出结论：sticky兼容性很差
## 五、层叠上下文
1. 理解
* 每个层叠上下文就是一个新的小世界(作用域)
* 这个小世界里面的z-index跟外界无关
* 文字举例：<pre>比如有a和b两个家族，a为老家族，b为新家族，那么按照后来居上原则，b家族所有层级都在a家族的上面，故b2高于a10
* 处在同一个小世界的z-index才能比较<pre>例子：<pre>https://jsbin.com/xurarun/edit?html,css,output</pre></pre>
1. 哪些不正交的属性可以创建层叠上下文
* 详见"层叠上下文MDN"(网上搜)
* 常见的有<pre>z-index/flex/opacity/transform