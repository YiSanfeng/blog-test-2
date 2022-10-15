# 构造函数
## 总结
* new X()自动做了四件事
1. 自动创建空对象
2. 自动为空对象关联原型，原型地址指定为X.prototype
3. 自动将空对象作为this关键字运行构造函数
4. 自动return this
5. 普通写法
<pre>
function cerateSquare(width){
    let obj = Object.create(createSquare.squareprototype)
    return obj
}
createSquare.squarepeototype={
    getArea(){
        return this.width * this.width
    },
    getLength(){
        return this.width * 4
    },
    constructor:createSquare
}
let square = createSquare(5)
</pre>
6. new写法
<pre>
function square(width){
    this.width = width
}
Square.prototype.getArea = function(){
    return this.width * this.width
}
Square.prototype.getLength = function(){
    return this.width * 4
}
let square = new Square()
</pre>
## class语法
<pre>
class Square{
    constructor(width){
        this.width = width
    }
    getArea(){
        return this.width * this.width
    }
    getLength(){
        return this.width * 4
    }
}

