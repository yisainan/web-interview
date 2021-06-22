# [返回主页](https://github.com/yisainan/web-interview/blob/master/README.md)

<b><details><summary>1. JavaScript 以下哪条语句会产生运行错误 </summary></b>

A. var obj = (); B. var obj = []; C. var obj = {}; D. var obj = //; 

答案：AD

[参与互动](https://github.com/yisainan/web-interview/issues/543)

</details>

<b><details><summary>2. 以下哪些是 javascript 的全局函数</summary></b>

```
A. escape	函数可对字符串进行编码，这样就可以在所有的计算机上读取该字符串。ECMAScript v3 反对使用该方法，应用使用 decodeURI() 和 decodeURIComponent() 替代它。
B. parseFloat	parseFloat() 函数可解析一个字符串，并返回一个浮点数。
该函数指定字符串中的首个字符是否是数字。如果是，则对字符串进行解析，直到到达数字的末端为止，然后以数字返回该数字，而不是作为字符串。
C. eval	 函数可计算某个字符串，并执行其中的的 JavaScript 代码。
D. setTimeout
E. alert
```

答案：ABC

[参与互动](https://github.com/yisainan/web-interview/issues/544)

</details>

<b><details><summary>3. 关于 IE 的 window 对象表述正确的有</summary></b>

```
A. window.opener属性本身就是指向window对象
B. window.reload()方法可以用来刷新当前页面  应该是location.reload或者window.location.reload
C. window.location="a.html"和window.location.href="a.html"的作用都是把当前页面替换成a.html页面
D. 定义了全局变量g;可以用window.g的方式来存取该变量
```

答案：ACD

[参与互动](https://github.com/yisainan/web-interview/issues/545)

</details>

<b><details><summary>4. 描述错误的是</summary></b>

```
A：HTTP状态码302表示暂时性转移
B:domContentLoaded事件早于onload事件
C: IE678不支持事件捕获
D:localStorage 存储的数据在电脑重启后丢失
```

答案：D

解析：

HTTP 状态码 302 表示被请求的资源暂时转移(Moved temporatily)，然后会给出一个转移后的 URL，而浏览器在处理服务器返回的 302 错误时，原则上会重新建立一个 TCP 连接，然后再取重定向后的 URL 的页面; 但是如果页面存在于缓存中，则不重新获取; 

onload 事件触发时，页面上所有的 DOM，样式表，脚本，图片，flash 都已经加载完成了，domContentLoaded 事件触发时，仅当 DOM 加载完成，不包括样式表，图片，flash。

C 正确，故选 D

[参与互动](https://github.com/yisainan/web-interview/issues/546)

</details>

<b><details><summary>5. 关于 link 和@import 的区别正确的是</summary></b>

```
A: link属于XHTML标签，而@import是CSS提供的;
B：页面被加载时，link会同时被加载，而后者引用的CSS会等到页面被加载完再加载
C：import只在IE5以上才能识别 而link是XHTML标签，无兼容问题
D: link方式的样式的权重高于@import的权重
```

答案：ABCD

[参与互动](https://github.com/yisainan/web-interview/issues/547)

</details>

<b><details><summary>6. 下面正确的是</summary></b>

```
A: 跨域问题能通过JsonP方案解决
B：不同子域名间仅能通过修改window.name解决跨域   还可以通过script标签src  jsonp等h5 Java split等
C：只有在IE中可通过iframe嵌套跨域
D：MediaQuery属性是进行视频格式检测的属性是做响应式的
```

答案：A

[参与互动](https://github.com/yisainan/web-interview/issues/548)

</details>

<b><details><summary>7. 一个.php 后缀的文件，可以在什么环境下执行</summary></b>

```
A mysql 数据库
B 浏览器
C apache 服务器
D Windows 系统
```

答案: C

解析:php 运行环境 apache

[参与互动](https://github.com/yisainan/web-interview/issues/603)

</details>

<b><details><summary>8.http 协议的默认端口号是</summary></b>

```
A 80
B 8888
C 8080
D 3306
```

答案: A

解析: 服务器安装好之后，默认端口号是 80

[参与互动](https://github.com/yisainan/web-interview/issues/604)

</details>

<b><details><summary>9.ajax 跨域的前端解决方案是哪个</summary></b>

```
A cors
B jsonp
C 服务器代理
D promise
```

答案: B

解析:jsonp 是使用标签的 src 属性链接资源接口，在 url 中传递回调函数，实现跨域请求

[参与互动](https://github.com/yisainan/web-interview/issues/605)

</details>

<b><details><summary>10.foo 对象有 att 属性，那么获取 att 属性的值，以下哪些做法是可以的</summary></b>

```
A foo("att")
B foo["att"]
C foo{"att"}
D foo[att]
```

答案: B

[参与互动](https://github.com/yisainan/web-interview/issues/606)

</details>

<b><details><summary>11. 下面说法正确的是</summary></b>

```
A setTimeout 函数是同步的
B setInterval 函数是异步的
C setTimeout(function( ) { } ,100) 会立即同步执行
D setInterval 函数会立即执行
```

答案: B

[参与互动](https://github.com/yisainan/web-interview/issues/607)

</details>

<b><details><summary>12. 下面哪个方法不属于数组操作方法?</summary></b>

```
A shift()
B pop()
C push()
D replace()
```

答案: D

[参与互动](https://github.com/yisainan/web-interview/issues/608)

</details>

<b><details><summary>13. 下面表示鼠标单击事件的是</summary></b>

```
A onclick
B onmouseover
C onmouseout
D onmousemove
```

答案: A

[参与互动](https://github.com/yisainan/web-interview/issues/609)

</details>

<b><details><summary>14. 以下代码, 当调用函数 func1 时，代码中打两个问号的地方，会弹出什么</summary></b>

```js
var v1 = 250;

function func1() {
    alert(v1); //？？
    var v1 = 350;
}
```

```
A 250
B 350
C undefined
D 以上都不对
```

答案: C

解析: 函数内部的 var v1 声明会提升到当前作用域顶部，但是赋值不会提升，所以 alert 的时候首先弹出当前作用域的 v1，值位 undefined

[参与互动](https://github.com/yisainan/web-interview/issues/610)

</details>

<b><details><summary>15. 下面哪个不是 js 的数据类型？</summary></b>

```
A int
B number
C string
D boolean
```

答案: A

[参与互动](https://github.com/yisainan/web-interview/issues/611)

</details>

<b><details><summary>16. 在 Javascript 中，需要声明一个整数类型的变量 num，以下哪个语句能实现上述要求？</summary></b>

```
A int num
B number num
C var num
D Integer num
```

答案: C

解析: var 关键字声明变量

[参与互动](https://github.com/yisainan/web-interview/issues/612)

</details>

<b><details><summary>17. 关于 Javascript 中数组的说法中，不正确的是：</summary></b>

```
A 数组的长度必须在创建时给定，之后便不能改变
B 由于数组是对象，因此创建数组时可以使用 new 运算符 当然也可以不用的
C 数组内元素的类型可以不同
D 数组可以在声明的同时进行初始化
```

答案: A

解析: js 数组长度是可以变化的

[参与互动](https://github.com/yisainan/web-interview/issues/613)

</details>

<b><details><summary>18. 以下关于 Javascript 中事件的描述中，不正确的是：</summary></b>

```
A onclick–鼠标单击事件
B onfocus–获取焦点事件
C onmouseover–鼠标指针移动到事件源对象上时触发的事件
D onsubmit–选择字段时触发的事件
```

答案: D

解析: change 需要选择的字段发生变化时才触发的事件

[参与互动](https://github.com/yisainan/web-interview/issues/614)

</details>

<b><details><summary>19. 表示表单提交事件的是：</summary></b>

```
A onmousemove
B onchange
C onclick
D onsubmit
```

答案: D

[参与互动](https://github.com/yisainan/web-interview/issues/615)

</details>

<b><details><summary>20.array 为数组对象，下面不是数组方法的为</summary></b>

```
A array.zero()
B array.map()
C array.filter()
D array.push()
```

答案: A

[参与互动](https://github.com/yisainan/web-interview/issues/616)

</details>

<b><details><summary>21. 使用 offsetWidth 获取 `<div style="border：1px solid red; width:200px"; >` 正确的数值为</summary></b>

```
A 199
B 197
C 198
D 202
```

答案: D

解析: offsetWidth 获取的时候包括了边框 并且不带 px 单位

[参与互动](https://github.com/yisainan/web-interview/issues/617)

</details>

<b><details><summary>22. 以下方法 1s 以后弹出 n 的值为( )</summary></b>

```js
var n = 10;
setInterval(function() {
    alert(n);
    var n = 100;
}, 1000);
```

```
A 10
B 100
C undefined
D 报错
```

答案: C

解析:
计时函数中，定义的变量 n 有声明提升，被提升到函数作用域顶部，即在 alert()之前，只提升声明，变量赋值位置不变，所以为 undefined

[参与互动](https://github.com/yisainan/web-interview/issues/618)

</details>

<b><details><summary>23. 选出有兼容性的方法或者属性( )</summary></b>

```
A event.cancelBubble
B getElementById
C getElementsByTagName
D nodeType
```

答案: A

解析: event.cancelBubble 是 IE 老版本取消事件冒泡的方式

[参与互动](https://github.com/yisainan/web-interview/issues/619)

</details>

<b><details><summary>24. 关于函数参数说法正确的是：（ ）</summary></b>

```
A 函数必须有参数
B 函数体中可以使用 arguments 来获取传递的实际参数值
C 函数必须有返回值
D 函数体中可以使用 parameters 来获取传递的实际参数
```

答案: B

解析: 可使用 arguments 在函数体中获取函数调用时的参数列表，在函数调用时，实参个数和形参个数可以不一致。

[参与互动](https://github.com/yisainan/web-interview/issues/620)

</details>

<b><details><summary>25. 以下代码 var t = 0 || 5，t 的值是( )</summary></b>

```
A true
B false
C 5
D 0
```

答案: C

解析: 逻辑或的应用 0 位 false

[参与互动](https://github.com/yisainan/web-interview/issues/621)

</details>

<b><details><summary>26. 下面不是用于创建一个新的对象的语句是</summary></b>

```
A var d = new Date();
B var f = ( );
C var o = new Object();
D var o = {title: "hello", author: "Tom"};
```

答案: B

[参与互动](https://github.com/yisainan/web-interview/issues/622)

</details>

<b><details><summary>27. 事件委托的好处是( )</summary></b>

```
A 减少了事件绑定的数量;对后来动态创建的元素依然有效
B 和普通事件的执行没什么区别
C 降低了程序执行效率
D 以上都不对
```

答案: A

[参与互动](https://github.com/yisainan/web-interview/issues/623)

</details>

<b><details><summary>28. 以下( )表达式产生一个 0~7 之间(含 0, 7)的随机整数</summary></b>

```
A Math.floor(Math.random()*6)
B Math.floor(Math.random()*7)
C Math. floor(Math.random()\*8)
D Math.ceil(Math.random()8)
```

答案: C

解析:
生成 min ~ max （包含 max）的随机数公式：
Math.floor(Math.random()(max - min+1) + min)

[参与互动](https://github.com/yisainan/web-interview/issues/624)

</details>

<b><details><summary>29. 要实现拖拽效果，需要用到以下哪些事件除了</summary></b>

```
A onmousedown
B onmouseup
C onmouseover
D onmousemove
```

答案: C

解析:
鼠标按下（onmousedown），鼠标移动（onmousemove），鼠标抬起（onmouseup）

[参与互动](https://github.com/yisainan/web-interview/issues/625)

</details>

<b><details><summary>30. 要检测值是否为 NaN，应使用 （ ）函数</summary></b>

```
A Number( )
B parseInt ( )
C IsNaN( )
D isNaN( )
```

答案: D

[参与互动](https://github.com/yisainan/web-interview/issues/626)

</details>

<b><details><summary>31. 下面哪个方法可以匹配数组是否含有某个值？</summary></b>

```
A sort()
B push()
C join()
D indexOf()
```

答案: D

[参与互动](https://github.com/yisainan/web-interview/issues/627)

</details>

<b><details><summary>32. 在 JavaScript 中, 执行下面的代码后，num 的值是 ( )</summary></b>

```js
var num = 0;
var t = num++ + num++;
```

```
A -1
B 0
C 2
D 13
```

答案: C

解析:
这个代码跟变量 t 没有关系，表达式中完成了两次 num 的自增，所以，结果是 2

[参与互动](https://github.com/yisainan/web-interview/issues/628)

</details>

<b><details><summary>33. 在 HTML 页面中，CSS 样式的属性名为 background-image 对应的 style 对象的属性名是( )</summary></b>

```
A background-image
B backgroundImage
C image
D background
```

答案: B

解析: 省略中间的-，后面的单词，首字母大写

[参与互动](https://github.com/yisainan/web-interview/issues/629)

</details>
