# HTTP的请求和响应&Node.js Server
## 代码逻辑
* ``这种字符串里面可以回车
* ''这种字符串里面要回车只能用/n表示
## 逻辑
* 每次收到请求都会把中间的代码执行一遍
* 用if else判断路径，并返回响应<pre>else if(path === '/')</pre>
* 如果是已知路径，一律返回200
* 如果是未知路径，一律返回404
* Content-Type表示内容的【类型/语法】<pre>response.setHeader('Content-Type', 'text/html;charset=utf-8')</pre>
* response.write()可以填写返回的内容<pre><pre><link rel="stylesheet"href="/x"></pre><pre>相当于加了个超链接，将else if里面的内容结合起来</pre></pre>
* response.end()表示响应可以发给用户了<pre>可不写内容，起到结束响应的作用就行</pre>
# HTTP基础概念
## 请求
* （请求行）请求动词 路径加查询参数 协议名/版本（要求背诵）
* （请求头）Host：域名或IP
* （请求头）Accept：text/html
* （请求头）Content-Type：请求体的格式
* 回车（请求头和请求体要用回车隔开，否则区分不了哪是哪）
* 请求体（也就是上传内容）
### 细节
* 三部分：请求行、请求头、请求体（要求背诵）
* 请求动词有GET（获取内容）/POST（上传内容）/PUT/PATCH/DELETE等
* 请求体在GET请求中一般为空
* 文档位于RFC 2612 第五章
* 大小写不敏感（随意）
## 响应
* （状态行）协议名/版本 状态码 状态字符串（要求背诵）
* （响应头）Content-Type:响应体的格式
* 回车
* （响应体）响应体（也就是下载内容）
### 细节
* 三部分：状态行、响应头、响应体
* 常见的状态码是考点
* 文档位于RFC 2612 第六章
# 用curl -v http://127.0.0.1:8888
## 设置请求动词
* -X POST
* 注意大小写
## 设置路径和查询参数
* 直接在curl后面加
## 设置请求头
* -H'Name:Value'或者--header'Name:Value'
## 设置请求体
* -d'内容'或者--data'内容'
## 用node.js读取请求
* 读取请求动词<pre>request.method</pre>
* 读取路径<pre>request.url路径，带查询参数</pre><pre>path春路径，不带查询参数</pre><pre>query只有查询参数</pre>
* 读取请求头<pre>request.headers['accept']
## console.log调试大法

## 阿里云服务器部署-启动应用
* 运行sh ./start 得到一个进程号 pid
* tail log 看 log 内容
* kill -9 pid 可以关掉进程
* killall node 可以关掉所有 node 进程
## 如何重启应用
### 上传代码
* 在本地改完代码
* git push
### 下载代码
* shh frank@aliyun1
* cd nodejs-text
* git pull
* killall node （因为忘了进程号，实际上可以记下来）
* sh ./start
* 重启完毕