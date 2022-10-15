# CSS知识总结
## 浏览器渲染原理
<pre>浏览器的渲染原理其实就是经过layout(布局)、paint(绘制)、composite(合成)的三种更新过程
</pre>
## 三、transition
1. 作用是：补充中间帧
2. 语法：<pre><pre><pre>属性名(width height....)</pre><pre>时长（s ms)</pre><pre>过渡方式(linear ease ease-in ease-out ease-in-out)<pre>并不是所有属性都能过渡</pre></pre><pre>延迟(s)</pre><pre>例句：transition:width(变化的属性) 1s(变化用时) ease-in(变化样式) 2s(延时后再变化) </pre></pre>
## 四、animation
1. 语法<pre><pre>animation:时长、过渡方式、延迟、次数、方向、填充模式、是否暂停、动画名</pre><pre>时长:1s或者1000ms</pre><pre>过渡方式:跟transition取值一样，如linear</pre><pre>次数:3或者2.4或者infinite</pre><pre>反向:reverse/alternate/alternate-reverse</pre><pre>填充模式:none/forwards/backwards/both</pre><pre>是否暂停:paused/running</pre></pre><pre>@keyframes xxx{
    0%{transform:none;}
    66.6%{transform:translateX(200px)}
    100%{transform:translateX(200px) transform:{translateY(200px)}
    }</pre>