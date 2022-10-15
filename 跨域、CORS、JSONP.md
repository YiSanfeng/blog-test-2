# 跨域、CORS、JSONP
## 同源策略
* 不同源的页面之间，不准互相访问数据
## 实现允许跨域访问
【问题】：浏览器默认不同源之间不能互相访问数据，但这N个网站都是自己的时候
* 解决方法一： CORS
1. 添加一个响应头
```
'Access-Control-Allow-Origin','http://frank.com:9999'//意思是允许访问这个页面
```
* 解决方法二：JSONP(IE只能用此法)
//通过浏览器去访问另一个网站的JS，并拿到JS的数据
1. frank.com 访问 qq.com
2. qq.com 将数据写到 /friends.js
3. frank.com 用 script 标签引用 /friends.js
4. /friends.js 执行，执行什么呢？
5. frank.com 事先定义好 window.xxx 函数
6. /friends.js 执行 window.xxx({frinds:[...]})
7. 然后 frank.com 就通过 window.xxx 获取到数据了
8. window.xxx 就是一个回调啊！


### JSONP总结
* <pre>
  JSONP：创造一个script请求另一个网站的JS，JS把数据夹带过来，然后我们拿到这个JS的数据。
  我们在跨域的时候，由于当前浏览器不支持CORS或者因为某些条件不支持CORS，我们必须使用另外一种方式来跨域。
  于是我们就请求一个JS文件，这个JS文件会执行一个回调，回调里面会有我们的数据。
  回调的名字可以是一个随机数，我们用callback的参数传给后台，后台会把这个函数再次返回给我们再执行。
  优点：1：可以跨域，2：兼容IE
  缺点：由于他是script标签，所以他读不到ajax那么精确的状态码，拿不到herder。由于他是script标签，所以只能发get请求，不支持popst
</pre>

