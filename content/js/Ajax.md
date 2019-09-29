# [返回主页](https://github.com/yisainan/web-interview/blob/master/README.md)

<b><details><summary>1.Ajax 是什么?如何创建一个 Ajax？</summary></b>

答案：Ajax 全称是 asychronous javascript and xml，可以说是已有技术的组合，主要用来实现客户端与服务器端的异步交互，实现页面的局部刷新。

基本步骤 4 步走：（创建对象、建立连接、发送数据、接收数据）

解析：

```

    1：我要创建一个XMLHttpRequest 对象。
    var xhr=new XMLHttpRequest() 创建对象

    2：我要发送请求，我要跟服务器建立一个连接。

    xhr.open("type 提交方式", "url  提交的地址")

    2.1:如果是post请求，需要设置请求头

    xhr.setRequestHeader("Content-Type","application/x-www-form-urlencoded");

    3：我要发送数据给服务器。

    如果说是get 请求，请求的数据在地址的后面。
    xhr.send() 发送数据，这一步不能省略

    4：接收服务器的数据。
        服务端返回数据会调用一个回调函数。
        通过回调函数去接收数据.
    xhr.onreadystatechange=function(){
            if(xhr.readyState==4){ 响应完成了
                    if(xhr.status==200){ //响应成功了
                          responseText 属性接收服务端返回的数据.
                    }
            }
    }

```

[参与互动](https://github.com/yisainan/web-interview/issues/62)

</details>

<b><details><summary>2.同步和异步的区别?</summary></b>

答案：同步：阻塞的；异步：非阻塞的。

解析：

同步：阻塞的

- 张三叫李四去吃饭，李四一直忙得不停，张三一直等着，直到李四忙完两个人一块去吃饭

- 浏览器向服务器请求数据，服务器比较忙，浏览器一直等着（页面白屏），直到服务器返回数据，浏览器才能显示页面

异步：非阻塞的

- 张三叫李四去吃饭，李四在忙，张三说了一声然后自己就去吃饭了，李四忙完后自己去吃

- 浏览器向服务器请求数据，服务器比较忙，浏览器可以自如的干原来的事情（显示页面），服务器返回数据的时候通知浏览器一声，浏览器把返回的数据再渲染到页面，局部更新

[参与互动](https://github.com/yisainan/web-interview/issues/63)

</details>

<b><details><summary>3.如何解决跨域问题?</summary></b>

答案：

1. jsonp ，允许 script 加载第三方资源
2. 反向代理（nginx 服务内部配置 Access-Control-Allow-Origin \*）
3. cors 前后端协作设置请求头部，Access-Control-Allow-Origin 等头部信息
4. iframe 嵌套通讯，postmessage

解析：

理解跨域的概念：协议、域名、端口都相同才同域，否则都是跨域

[参考](https://zhuanlan.zhihu.com/p/41479807)
[跨域资源共享 CORS 阮一峰](http://www.ruanyifeng.com/blog/2016/04/cors.html)

[参与互动](https://github.com/yisainan/web-interview/issues/64)

</details>

<b><details><summary>4.页面编码和被请求的资源编码如果不一致如何处理？</summary></b>

答案：get 请求中的中文需要 encodeURIComponent 编码处理，post 请求不需要进行编码

[参与互动](https://github.com/yisainan/web-interview/issues/65)

</details>

<b><details><summary>5.创建 ajax 过程</summary></b>

答案：

1. 创建 XMLHttpRequest 对象,也就是创建一个异步调用对象

2. 创建一个新的 HTTP 请求,并指定该 HTTP 请求的方法、URL 及验证信息

3. 设置响应 HTTP 请求状态变化的函数

4. 发送 HTTP 请求

5. 获取异步调用返回的数据

6. 使用 JavaScript 和 DOM 实现局部刷新

[参与互动](https://github.com/yisainan/web-interview/issues/66)

</details>

<b><details><summary>6.阐述一下异步加载 JS</summary></b>

答案：

1. 异步加载的方案： 动态插入 script 标签

2. 通过 ajax 去获取 js 代码，然后通过 eval 执行

3. script 标签上添加 defer 或者 async 属性

4. 创建并插入 iframe，让它异步执行 js

[参与互动](https://github.com/yisainan/web-interview/issues/67)

</details>

<b><details><summary>7.请解释一下 JavaScript 的同源策略</summary></b>

答案：同源策略是客户端脚本（尤其是 Javascript）的重要的安全度量标准。它最早出自 Netscape Navigator2.0，其目的是防止某个文档或脚本从多个不同源装载。所谓同源指的是：协议，域名，端口相同，同源策略是一种安全协议，指一段脚本只能读取来自同一来源的窗口和文档的属性。

[参与互动](https://github.com/yisainan/web-interview/issues/68)

</details>

<b><details><summary>8.GET 和 POST 的区别，何时使用 POST？</summary></b>

答案：

GET：一般用于信息获取，使用 URL 传递参数，对所发送信息的数量也有限制，一般在 2000 个字符，有的浏览器是 8000 个字符

POST：一般用于修改服务器上的资源，对所发送的信息没有限制

在以下情况中，请使用 POST 请求：

1. 无法使用缓存文件（更新服务器上的文件或数据库）

2. 向服务器发送大量数据（POST 没有数据量限制）

3. 发送包含未知字符的用户输入时，POST 比 GET 更稳定也更可靠

[参与互动](https://github.com/yisainan/web-interview/issues/69)

</details>

<b><details><summary>9.ajax 的优点</summary></b>

答案：

1.  通过异步模式，提升了用户体验。来自服务器的新内容可以动态更改，无需重新加载整个页面。

2.  优化了浏览器和服务器之间的传输，减少不必要的数据往返，减少了带宽占用

3.  Ajax 在客户端运行，承担了一部分本来由服务器承担的工作，减少了大用户量下的服务器负载。

[参与互动](https://github.com/yisainan/web-interview/issues/70)

</details>

<b><details><summary>10. Ajax 的最大的特点是什么？</summary></b>

答案：

* Ajax 可以实现异步通信效果，实现页面局部刷新，带来更好的用户体验；
* 按需获取数据，节约带宽资源；

[参与互动](https://github.com/yisainan/web-interview/issues/71)

</details>

<b><details><summary>11.ajax 的缺点</summary></b>

答案：

1.ajax 不支持浏览器 back 按钮。

2.安全问题 AJAX 暴露了与服务器交互的细节。

3.对搜索引擎的支持比较弱。

4.破坏了程序的异常机制。

[参与互动](https://github.com/yisainan/web-interview/issues/72)

</details>

<b><details><summary>12.ajax 请求的时候 get 和 post 方式的区别</summary></b>

答案：

get 一般用来进行查询操作，url 地址有长度限制，请求的参数都暴露在 url 地址当中，如果传递中文参数，需要自己进行编码操作，安全性较低。

post 请求方式主要用来提交数据，没有数据长度的限制，提交的数据内容存在于 http 请求体中，数据不会暴漏在 url 地址中。

[参与互动](https://github.com/yisainan/web-interview/issues/73)

</details>

<b><details><summary>13.解释 jsonp 的原理，以及为什么不是真正的 ajax, 以及优缺点</summary></b>

答案：

1.jsonp 是用来解决跨域获取数据的一种解决方案，具体是通过动态创建 script 标签，然后通过标签的 src 属性获取 js 文件中的 js 脚本，该脚本的内容是一个函数调用，参数就是服务器返回的数据，为了处理这些返回的数据，需要事先在页面定义好回调函数，本质上使用的并不是 ajax 技术

2.优缺点

- jsonp 优点:

  - 完美解决在测试或者开发中获取不同域下的数据,用户传递一个 callback 参数给服务端，然后服务端返回数据时会将这个 callback 参数作为函数名来包裹住 JSON 数据，这样客户端就可以随意定制自己的函数来自动处理返回数据了。简单来说数据的格式没有发生很大变化

- jsonp 缺点:

  - 1.jsonp 只支持 get 请求而不支持 post 请求,也即是说如果想传给后台一个 json 格式的数据,此时问题就来了,浏览器会报一个 http 状态码 415 错误,告诉你请求格式不正确,这让我很蛋疼(在登录注册中需要给后台传一大串数据),如果都用参数的形式拼接在 url 后面的话不太现实,后台取值也会显得繁琐,
  - 2.在登录模块中需要用到 session 来判断当前用户的登录状态,这时候由于是跨域的原因,前后台的取到的 session 是不一样的,那么就不能就行 session 来判断.
  - 3.由于 jsonp 存在安全性问题(不知 qq 空间的跨域是怎么解决的,还是另有高招?)，后来考虑到上面的一系列问题,采用的是后台进行设置允许跨域请求(但还是存在缺陷的,实质上还是跨域,如上面说的 session 问题).Header set Access-Control-Allow-Origin \*为了防止 XSS 攻击我们的服务器， 我们可以限制域，比如 Access-Control-Allow-Origin: http://blog.csdn.net

[参与互动](https://github.com/yisainan/web-interview/issues/74)

</details>

<b><details><summary>14.什么是 Ajax 和 JSON，它们的优缺点。</summary></b>

答案：

- Ajax 是全称是 asynchronous JavaScript andXML，即异步 JavaScript 和 xml，用于在 Web 页面中实现异步数据交互，实现页面局部刷新。

  - 优点：可以使得页面不重载全部内容的情况下加载局部内容，降低数据传输量，避免用户不断刷新或者跳转页面，提高用户体验

  - 缺点：对搜索引擎不友好；要实现 ajax 下的前后退功能成本较大；可能造成请求数的增加跨域问题限制；

- JSON 是一种轻量级的数据交换格式，ECMA 的一个子集

  - 优点：轻量级、易于人的阅读和编写，便于机器（JavaScript）解析，支持复合数据类型（数组、对象、字符串、数字）

[参与互动](https://github.com/yisainan/web-interview/issues/75)

</details>

<b><details><summary>15.什么是 json，优缺点</summary></b>

答案：

JSON (JavaScript Object Notation)

优点:

1. 数据格式比较简单, 易于读写, 格式都是压缩的, 占用带宽小
2. 易于解析这种语言, 客户端 javascript 可以简单的通过 eval()进行 JSON 数据的读取搜索
3. 支持多种语言, 包括 ActionScript, C, C#, ColdFusion, Java, JavaScript, Perl, php, Python, Ruby 等语言服务器端语言, 便于服务器端的解析
4. 在 PHP 世界, 已经有 PHP-JSON 和 JSON-PHP 出现了, 便于 PHP 序列化后的程序直接调用. PHP 服务器端的对象、数组等能够直接生 JSON 格式, 便于客户端的访问提取. 另外 PHP 的 PEAR 类已经提出了支持 (http://pear.php.net/pepr/pepr-proposal-show.php?id=198)
5. 因为 JSON 格式能够直接为服务器端代码使用, 大大简化了服务器端和客户端的代码开发量, 但是完成的任务不变, 且易于维护

缺点:

1. 没有 XML 格式这么推广的深入人心和使用广泛, 没有 XML 那么通用性
2. JSON 格式目前在 Web Service 中推广还属于初级阶段 PS: 据说 Google 的 Ajax 是使用 JSON+模板 做的

[参与互动](https://github.com/yisainan/web-interview/issues/76)

</details>

<b><details><summary>16.一个页面从输入 URL 到页面加载显示完成，这个过程中都发生了什么？</summary></b>

答案：

1.浏览器地址栏输入 url

2.浏览器会先查看浏览器缓存--系统缓存--路由缓存，如有存在缓存，就直接显示。如果没有，接着第三步

3.域名解析（DNS）获取相应的 ip

4.浏览器向服务器发起 tcp 连接，与浏览器建立 tcp 三次握手

5.握手成功，浏览器向服务器发送 http 请求，请求数据包

6.服务器请求数据，将数据返回到浏览器

7.浏览器接收响应，读取页面内容，解析 html 源码，生成 DOm 树

8.解析 css 样式.浏览器渲染，js 交互绑定多个域名，数量不限；

[参与互动](https://github.com/yisainan/web-interview/issues/77)

</details>

<b><details><summary>17.XML 和 JSON 的区别？</summary></b>

答案：

(1).数据体积方面。

JSON 相对于 XML 来讲，数据的体积小，传递的速度更快些。

(2).数据交互方面。

JSON 与 JavaScript 的交互更加方便，更容易解析处理，更好的数据交互。

(3).数据描述方面。

JSON 对数据的描述性比 XML 较差。

(4).传输速度方面。

JSON 的速度要远远快于 XML。

[参与互动](https://github.com/yisainan/web-interview/issues/78)

</details>

<b><details><summary>18.ajax 请求时，如何解析 json 数据</summary></b>

答案：使用 eval() 或者 JSON.parse() 鉴于安全性考虑，推荐使用 JSON.parse()更靠谱，对数据的安全性更好。

[参与互动](https://github.com/yisainan/web-interview/issues/79)

</details>

<b><details><summary>19.异步加载和延迟加载</summary></b>

答案：

1.异步加载的方案： 动态插入 script 标签

2.通过 ajax 去获取 js 代码，然后通过 eval 执行

3.script 标签上添加 defer 或者 async 属性

4.创建并插入 iframe，让它异步执行 js

5.延迟加载：有些 js 代码并不是页面初始化的时候就立刻需要的，而稍后的某些情况才需要的。

[参与互动](https://github.com/yisainan/web-interview/issues/80)

</details>

<b><details><summary>20.eval 是做什么的？</summary></b>

答案：它的功能是把对应的字符串解析成 JS 代码并运行；

解析：应该避免使用 eval，不安全，非常耗性能（2 次，一次解析成 js 语句，一次执行）。

[参与互动](https://github.com/yisainan/web-interview/issues/81)

</details>

<b><details><summary>21.AMD 和 CMD 规范的区别</summary></b>

答案：

1.对于依赖的模块，AMD 是提前执行，CMD 是延迟执行

2.CMD 推崇依赖就近，AMD 推崇依赖前置

[参与互动](https://github.com/yisainan/web-interview/issues/82)

</details>

<b><details><summary>22.HTTP 状态码</summary></b>

答案：

100 ?Continue ?继续，一般在发送 post 请求时，已发送了 http header 之后服务端将返回此信息，表示确认，之后发送具体参数信息

200 ?OK ? 正常返回信息

201 ?Created ?请求成功并且服务器创建了新的资源

202 ?Accepted ?服务器已接受请求，但尚未处理

301 ?Moved Permanently ?请求的网页已永久移动到新位置。

302 Found ?临时性重定向。

303 See Other ?临时性重定向，且总是使用 GET 请求新的 URI。

304 ?Not Modified ?自从上次请求后，请求的网页未修改过。

400 Bad Request ?服务器无法理解请求的格式，客户端不应当尝试再次使用相同的内容发起请求。

401 Unauthorized ?请求未授权。

403 Forbidden ?禁止访问。

404 Not Found ?找不到如何与 URI 相匹配的资源。

500 Internal Server Error ?最常见的服务器端错误。

503 Service Unavailable 服务器端暂时无法处理请求（可能是过载或维护）。

[参与互动](https://github.com/yisainan/web-interview/issues/83)

</details>

<b><details><summary>23.栈和队列的区别?</summary></b>

答案：

- 栈的插入和删除操作都是在一端进行的，而队列的操作却是在两端进行的。
- 队列先进先出，栈先进后出。
- 栈只允许在表尾一端进行插入和删除，而队列只允许在表尾一端进行插入，在表头一端进行删除

拓展：

栈和堆的区别？

栈区（stack）—    由编译器自动分配释放，存放函数的参数值，局部变量的值等。

堆区（heap）—    一般由程序员分配释放，若程序员不释放，程序结束时可能由 OS 回收。

堆（数据结构）：堆可以被看成是一棵树，如：堆排序；

栈（数据结构）：一种先进后出的数据结构。

[参与互动](https://github.com/yisainan/web-interview/issues/84)

</details>

<b><details><summary>24.ajax 加载的页面，跳转到另外一个页面再跳转回来，内容相同，如何节约读取请求?</summary></b>

答案：后台做缓存，读取缓存里面的数据、CDN

[参与互动](https://github.com/yisainan/web-interview/issues/85)

</details>

<b><details><summary>25.Ajax 实现的原理</summary></b>

答案：浏览器提供的 XMLHttpRequest 对象

[参与互动](https://github.com/yisainan/web-interview/issues/86)

</details>

<b><details><summary>26.ajax 如何实现，readyState 的五种状态的含义？</summary></b>

答案：

- 0 － （未初始化）还没有调用 send()方法
- 1 － （载入）已调用 send()方法，正在发送请求
- 2 － （载入完成）send()方法执行完成，已经接收到全部响应内容
- 3 － （交互）正在解析响应内容
- 4 － （完成）响应内容解析完成，可以在客户端调用了

解析：

(0)未初始化

此阶段确认 XMLHttpRequest 对象是否创建，并为调用 open()方法进行未初始化作好准备。值为 0 表示对象已经存在，否则浏览器会报错－－对象不存在。

(1)载入

此阶段对 XMLHttpRequest 对象进行初始化，即调用 open()方法，根据参数(method,url,true)完成对象状态的设置。并调用 send()方法开始向服务端发送请求。值为 1 表示正在向服务端发送请求。

(2)载入完成

此阶段接收服务器端的响应数据。但获得的还只是服务端响应的原始数据，并不能直接在客户端使用。值为 2 表示已经接收完全部响应数据。并为下一阶段对数据解析作好准备。

(3)交互

此阶段解析接收到的服务器端响应数据。即根据服务器端响应头部返回的 MIME 类型把数据转换成能通过 responseBody、responseText 或 responseXML 属性存取的格式，为在客户端调用作好准备。状态 3 表示正在解析数据。

(4)完成

此阶段确认全部数据都已经解析为客户端可用的格式，解析已经完成。值为 4 表示数据解析完毕，可以通过 XMLHttpRequest 对象的相应属性取得数据。

[参考](https://blog.csdn.net/u011565547/article/details/78979030)

[参与互动](https://github.com/yisainan/web-interview/issues/87)

</details>

<b><details><summary>27.RESTful</summary></b>

答案：REST 指的是一组架构约束条件和原则。满足这些约束条件和原则的应用程序或设计就是 RESTful。

- GET<br>
  get 方法在 Rest 中主要用于获取资源，能够发送参数，不过有限制，且参数都会以?开头的形 式附加在 URL 尾部。
  规范的 get 方法处理器应该是幂等的，也就是说对一个资源不论发送多少次 get 请求都不会更改数据或造成破坏。
- POST<br>
  post 方法在 Rest 请求中主要用于添加资源，参数信息存放在请求报文的消息体中相对安全，且可发送较大信息
- PUT<br>
  put 方法在 Rest 中主要用于更新资源，因为大多数浏览器不支持 put 和 delete，会自动将 put 和 delete 请求转化为 get 和 post. 因此为了使用 put 和 delete 方法,
  需要以 post 发送请求，在表单中使用隐藏域发送真正的请求。
  put 方法的参数是同 post 一样是存放在消息中的，同样具有安全性，可发送较大信息。
  put 方法是幂等的，对同一 URL 资源做出的同一数据的任意次 put 请求其对数据的改变都是一致的。
- DELETE<br>
  Delete 在 Rest 请求中主要用于删除资源，因为大多数浏览器不支持 put 和 delete，会自动将 put 和 delete 请求转化为 get 和 post。
  因此为了使用 put 和 delete 方法,需要以 post 发送请求，在表单中使用隐藏域发送真正的请求。
  Delete 方法的参数同 post 一样存放在消息体中,具有安全性，可发送较大信息 Delete 方法是幂等的，不论对同一个资源进行多少次 delete 请求都不会破坏数据

解析：[参考](https://blog.csdn.net/jnshu_it/article/details/80203696)

[参与互动](https://github.com/yisainan/web-interview/issues/88)

</details>

<b><details><summary>28.Ajax 和 Fetch 区别</summary></b>

答案：

- ajax 是使用 XMLHttpRequest 对象发起的，但是用起来很麻烦，所以 ES6 新规范就有了 fetch，fetch 发一个请求不用像 ajax 那样写一大堆代码。
- 使用 fetch 无法取消一个请求，这是因为 fetch 基于 Promise，而 Promise 无法做到这一点。
- 在默认情况下，fetch 不会接受或者发送 cookies
- fetch 没有办法原生监测请求的进度，而 XMLHttpRequest 可以
- fetch 只对网络请求报错，对 400，500 都当做成功的请求，需要封装去处理
- fetch 由于是 ES6 规范，兼容性上比不上 XMLHttpRequest

[参与互动](https://github.com/yisainan/web-interview/issues/89)

</details>
