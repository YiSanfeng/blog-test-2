# CSS动画
## 一、浏览器渲染过程
步骤：
* 根据HTML构建HTML树（DOM）
* 根据CSS构建CSS树（CSSOM）
* 将两棵树合并成功一颗渲染树（render tree）
* Layout布局（文档流、盒模型、计算大小和位置）
* Paint绘制（把边框颜色、文字颜色、阴影等画出来）
* Compose合成（根据层叠关系展示画面）
  
#### 三种更新方式
* 第一种，全走(JS/CSS>样式>布局>绘制>合成)<pre>JS>Style>Layout>Paint>Composite</pre><pre>div.remove()会触发当前消失，其他元素relayout</pre>
* 第二种，跳过layout(JS/CSS>样式>绘制>合成)<pre>JS/CSS>Style>Paint>Composite</pre><pre>改变背景颜色，直接repaint+composite</pre>
* 第三种，跳过layout和paint(JS/CSS>样式>合成)<pre>JS/CSS>Style>Composite</pre><pre>改变transform,只需composite</pre><pre>注意必须全屏查看效果，在iframe里看问题</pre>
## 二、transform全解
1. 位移translate
2. 缩放scale
3. 旋转rotate
4. 倾斜skew
## 三、transition
1. 作用是：补充中间帧
2. 语法：<pre><pre><pre>属性名(width height....)</pre><pre>时长（s ms)</pre><pre>过渡方式(linear ease ease-in ease-out ease-in-out)<pre>并不是所有属性都能过渡</pre></pre><pre>延迟(s)</pre><pre>例句：transition:width(变化的属性) 1s(变化用时) ease-in(变化样式) 2s(延时后再变化) </pre></pre>
## 四、animation
1. 语法<pre><pre>animation:时长、过渡方式、延迟、次数、方向、填充模式、是否暂停、动画名</pre><pre>时长:1s或者1000ms</pre><pre>过渡方式:跟transition取值一样，如linear</pre><pre>次数:3或者2.4或者infinite</pre><pre>反向:reverse/alternate/alternate-reverse</pre><pre>填充模式:none/forwards/backwards/both</pre><pre>是否暂停:paused/running</pre></pre><pre>@keyframes xxx{
    0%{transform:none;}
    66.6%{transform:translateX(200px)}
    100%{transform:translateX(200px) transform:{translateY(200px)}
    }</pre>