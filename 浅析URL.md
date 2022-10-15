# URL介绍
## curl命令

## URL包含的内容及其作用
* 协议+域名或IP+端口号+路径+查询字符串+锚点
* 几个特殊的IP
1. 127.0.01表示自己
2. localhost通过hosts指定为自己
3. 0.0.0.0不表示任何设备
* IP和端口缺一不可
* 用curl向发出HTTP请求的用法<pre>curl -v http://baidu.com</pre><pre>curl-s-v--https://baidu.com</pre>
## DNS的作用，nslookup命令的使用
* 作用：使域名和IP连接起来
* <pre>nslookup的使用：nslookup xiedaimala.com</pre>
## IP的作用，ping命令的使用
* IP的作用：每个网络设备都会有一个IP，路由器以内的设备称为内网，通过路由器访问外网；路由器以外的设备称为外网，可以将内网的设备和外网以外的设备连接
* <pre>ping的用法：ping xiedaimala.com</pre>
## 域名是什么及域名的分类
* 域名就是对ip的别称
* 分类：com cn org io

