# 浅析 MVC
## MVC 三个对象分别做什么
1. M
<pre>
const model = {
    data:null,
    init(){}
    create(){}
    delete(){}
    get(){}
</pre>
2. V
<pre>
View = {
    el:null,
    html: `......` //视图模板
    init(){初始化页面},
    render(){ 刷新页面 }
}
</pre>
3. C
<pre>
Controller = {
   init(){
      v.init() // View初始化
      v.render() // 第一次渲染
      c.autoBindEvents() // 自动的事件绑定
      eventBus.on('m:update', () => { v.render() }) // 当eventBus触发'm:update'时View刷新
   },
   events:{ 事件以哈希表方式记录 }，
   method() {
      data = 改变后的新数据
      m.update(data)
   }，
   autoBindEvents() { 自动绑定事件 }
</pre>
## EventBus 有哪些 API，是做什么用的
1. EventBus基本的api有on（监听事件），trigger(emit)（触发事件）,off（取消监听）方法。 用于模块间的通讯，view组件层面，父子组件、兄弟组件通信都可以使eventbus处理
2. API
<pre>
//EventBus.js
class EventBus{
    constructor(){
        this._eventBus =$(window)
    }
    on(eventName, fn){
        return this._eventBus.on(eventName,fn)
    }
    trigger(eventName,data){
        return this._trigger.tiggger(eventName,data)
    }
    off(eventName, fn){
        return this._eventBus.off(eventName,fn)
    }
}
export default EventBus
//new.js
import EventBus from 'EventBus.js'
const e =new EventBus()
e.on()
e.trigger()
e.off()
</pre>

## 3. 表驱动编程是做什么的
1. 表驱动法是一种编程模式，从表(哈希表)里面查找信息而不是使用逻辑语句（if…else…switch，可以减少重复代码，只将重要的信息放在表里，然后利用表来编程，与逻辑语句相比较有着更稳定的复杂度 下面这段代码相似性很高，当我们使用表驱动法后
<pre>
bindEvents(){
    v.el.on('click','#add1',()=>{
    m.data.n +=1
    v.render(m.data.n)
    })
    v.el.on('click','#minus1',()=>{
    m.data.n-=1
    v.render(m.data.n)
    })
    v.el.on('click','#mul2',()=>{
        m.data.n*=2
        v.render(m.data.n)
    })
    v.el.on('click','#divide2',()=>{
        m.data.n/=2
        v.render(m.data.n)
    })
}
</pre>

3. 将事件提取出一个哈希表，使逻辑和数据清晰明了的分离开
<pre>
events:{
    'click #aa1':'add',
    'click #minus1':'minus',
    'click #mul2':'mul',
    'click #divide2':'div'
},
add(){
    m.update( data: {n:m.data.n +1})
},
minus(){
    m.update( data:{n:m.data.n -1})
},
mul(){
    m.update( data: {n:m.data.n *2})
},
div(){
    m.update(data: {n:m.data.n /2})
}
</pre>

##  我是如何理解模块化的
1. 代码模块化之后,无论是代码的整体性还是后期进行代码维护都变的清晰简单了起来。如:与逻辑相关的代码统一放到JS文件中，与视图相关的统一放到html文件中，与样式相关的统一放到css文件中。
2. 模块化可以降低代码耦合度，减少重复代码，提高代码重用性，并且在项目结构上更加清晰，便于维护。
3. 一个模块就是一个独立的文件，该文件内部的所有变量，外部无法获取，如果你希望外部能够读取模块内部的某个变量，就必须使用export命令输出该变量，使用import命令输入其他模块提供的功能。