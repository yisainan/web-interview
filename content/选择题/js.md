# [返回主页](https://github.com/yisainan/web-interview/blob/master/README.md)

<b><details><summary>1.JavaScript 以下哪条语句会产生运行错误 </summary></b>

A. var obj = (); B. var obj = []; C. var obj = {}; D. var obj = //;

答案：AD

</details>

<b><details><summary>2.以下哪些是 javascript 的全局函数：</summary></b>

```
A. escape	函数可对字符串进行编码，这样就可以在所有的计算机上读取该字符串。ECMAScript v3 反对使用该方法，应用使用 decodeURI() 和 decodeURIComponent() 替代它。
B. parseFloat	parseFloat() 函数可解析一个字符串，并返回一个浮点数。
该函数指定字符串中的首个字符是否是数字。如果是，则对字符串进行解析，直到到达数字的末端为止，然后以数字返回该数字，而不是作为字符串。
C. eval	 函数可计算某个字符串，并执行其中的的 JavaScript 代码。
D. setTimeout
E. alert
```

答案：ABC

</details>

<b><details><summary>3.关于 IE 的 window 对象表述正确的有：</summary></b>

```
A. window.opener属性本身就是指向window对象
B. window.reload()方法可以用来刷新当前页面  应该是location.reload或者window.location.reload
C. window.location=”a.html”和window.location.href=”a.html”的作用都是把当前页面替换成a.html页面
D. 定义了全局变量g；可以用window.g的方式来存取该变量
```

答案：ACD

</details>

<b><details><summary>4.描述错误的是</summary></b>

```
A：HTTP状态码302表示暂时性转移
B:domContentLoaded事件早于onload事件
C: IE678不支持事件捕获
D:localStorage 存储的数据在电脑重启后丢失
```

答案：D

解析：

HTTP状态码302表示被请求的资源暂时转移(Moved temporatily)，然后会给出一个转移后的URL，而浏览器在处理服务器返回的302错误时，原则上会重新建立一个TCP连接，然后再取重定向后的URL的页面；但是如果页面存在于缓存中，则不重新获取；

onload事件触发时，页面上所有的DOM，样式表，脚本，图片，flash都已经加载完成了，domContentLoaded事件触发时，仅当DOM加载完成，不包括样式表，图片，flash。

C正确，故选D

</details>

<b><details><summary>5.关于 link 和@import 的区别正确的是</summary></b>

```
A: link属于XHTML标签，而@import是CSS提供的；
B：页面被加载时，link会同时被加载，而后者引用的CSS会等到页面被加载完再加载
C：import只在IE5以上才能识别 而link是XHTML标签，无兼容问题
D: link方式的样式的权重高于@import的权重
```

答案：A

</details>

<b><details><summary>6.下面正确的是</summary></b>

```
A: 跨域问题能通过JsonP方案解决
B：不同子域名间仅能通过修改window.name解决跨域   还可以通过script标签src  jsonp等h5 Java split等
C：只有在IE中可通过iframe嵌套跨域
D：MediaQuery属性是进行视频格式检测的属性是做响应式的
```

答案：A

</details>

<b><details><summary></summary></b>

答案：

</details>

<b><details><summary></summary></b>

答案：

</details>

<b><details><summary></summary></b>

答案：

</details>
