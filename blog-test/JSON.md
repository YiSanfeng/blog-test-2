# JSON
## JSON语法
<pre>
{
    "name":"frank",
    "age":"18"
}
</pre>
* 读取数据
1. fs.readFileSync('x').toString()  // 将这个文件变成一个字符串
2. 然后JSON.parse() //反序列化，得到一个数组
* 储存数据
1. 先JSON.stringify()  // 序列化，得到一个字符串
2. 然后fs.writeFileSync(x) // 写入数据
  