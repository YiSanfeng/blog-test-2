# JS 对象基本用法
## 声明对象的两种语法
1. <pre>let obj={'name':'xxx','age':'yyy'}</pre>
2. <pre>let obj=new Object({'xxx':'yyy'})
   console.log({'xxx':'frank','yyy':'18'})</pre>
## 如何删除对象的属性
1. <pre>delete obj.xxx或delete obj[ 'xxx' ] </pre>(同时删除属性名和属性值)
2. <pre>obj.xxx=undefined</pre>（没有删除属性名，只删除了属性值）
## 如何查看对象的属性
1. 查看自身所有属性
* 查看所有keys:<pre>Object keys(xxx)</pre>
* 查看所有values:<pre>Object values(xxx)</pre>
* 查看所有keys和values:<pre>Object entries(xxx)</pre>
2. 查看自身+共有属性
* <pre>console.dir(xxx)</pre>
## 如何修改或增加对象的属性
1. <pre>let obj = {
   'name':'jack'
   }</pre>
## 'name' in obj和obj.hasOwnProperty('name') 的区别
1. <pre>'name' in obj</pre>可以查看自身属性和共有属性
2. <pre>obj.hasOwnProperty('name')</pre>只能查看自身属性