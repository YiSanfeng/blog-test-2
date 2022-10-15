# DOM编程
## 获取元素（也叫获取标签）
* 有很多API（很多种函数）
1. window.idxxx或者直接idxxx
2. document.getElementById('idxxx')
3. document.getElementsByTagName('div')[0]
4. document.getElementsByClassName('div')[0]
5. document.querySelector('#idxxx')//注意加#
6. document.querySelectorAll('.red')[0]
7. //实际中经常用querySelector和querySelectorAll
8. // 2、3、4只有要兼容IE的时候才需要用，不然很垃圾
### 获取特定元素
* 获取html元素
1. document.documentElement
* 获取head元素
1. document.head
* 获取body元素
1. document.body
* 获取窗口
1. window
* 获取所有元素
1. document.all
## 节点node包括以下几种
* 查看标签类型：x.nodeType会得到一个数字
1. 1表示元素Element，也叫标签Tag
2. 3表示文本Text
3. 8表示注释Comment
4. 9表示文档Document
5. 11表示文档片段DocumentFragment
6. //重点记忆1和2条
## DOM的增删改查
### 增
* 创建一个标签节点
1. let div1 = document.createElement('div')
2. document.createElement('style')
3. document.createElement('script')
4. document.createElement('li')
* 创建一个文本节点
1. text1 = document.createTextNode('你好')
* 标签里面插入文本
1. div1.appendChild(text1)
2. div1.innerText = '你好'或者div1.textContent = '你好'
3. 但是不能用div.appendChild('你好')
### 删
* 两种方法
1. 旧方法：parentNode.childChild(childNode)
2. 新方法：childNode.remove()
### 改
#### 改属性
* 写标准属性
1. 改class:div.className = 'red blue'(全覆盖)
2. 改class:div.classList.add('red')
3. 改style：div.style = 'width:100px;color:blue;'
4. 改style的一部分：div.style.width:200px
5. 大小写：div.style.backgroundColor='white'
6. 改data-*属性：div.dataset.x='frank'
* 读标准属性
1. div.classList/a.href
2. div.getAttribute('class')/a.getAttribute('href')
3. 两种方法都可以，但值可能稍微有些不同
#### 改时间处理函数
* div.onclick默认为null
1. 默认点击div不会有任何事情发生
2. 但是如果你把div.onclick改为一个函数fn
3. 那么点击div的时候，浏览器就会调用这个函数
4. 并且是这样调用的fn.call(div,event)
5. div会被当做this
6. event则包含了点击事件的所有信息，如坐标
#### 改内容
* 改文本内容
1. div.innerText='xxx'
2. div.textContent='xxx'
3. 两者几乎没有区别
#### 改HTML内容
1. div.innerHTml='<strong>重要内容</strong>'
#### 改标签
1. div.innerHTML=''//先清空
2. div.appendChild(div2)//再加内容
#### 改父亲元素
1. newParent.appendChild(div)
2. 直接这样就可以了，直接从原来的地方消失
### 查
#### 查爸爸
1. node.parentNode或者node.parentElement
#### 查爷爷
1. node.parentNode.parentNode
#### 查子代
1. node.childNodes或者node.children
#### 查看老大
1. node.firstChild
#### 查看老幺
1. node.lastChild
#### 查看上一个哥哥/姐姐
1. node.previousSibling
#### 查看下一个弟弟/妹妹
1. node.nextSibling
#### * 遍历一个div里面的所有元素
<pre>
travel = (node,fn) => {
    fn(node)
    if(node,children){
        for(let i=o,i < node.children.length;i++){
            travel(node.children[i])
        }
    }
}
travel(div1,(node) => console.log(node))
</pre>
#### 知识点
* 
<pre>
const childNodes = node.childNodes =
const {childNodes} = node //此法为简写
</pre>
