# [返回主页](../README.md)

<b><details><summary>2. Http 状态码，Http2 是什么</summary></b>

200 欢迎回来，主人 （正常；请求已完成。）

301 人家搬家了 （已移动 — 请求的数据具有新的位置且更改是永久的。）

307 不是这里，换个地方啦 （重新请求的 URL，客户端自动重新请求新的地址）

400 不要把奇怪的东西给人家嘛 （错误请求 — 请求中有语法问题，或不能满足请求。）

403 这里不可以啦！（禁止 — 即使有授权也不需要访问。）

404 这里什么都没有 --- 人家是平的啦。 （找不到 — 服务器找不到给定的资源；文档不存在。）

405 打开方式不对 （资源被禁止）

414 这... 太长了啦 （请求 - URI 太长）

500 服务姬坏掉了啦 （内部错误 — 因为意外情况，服务器不能完成请求。）

503 不要...人家还没准备好啦 （无法获得服务 — 由于临时过载或维护，服务器无法处理请求。）

101 服务姬傲娇中 （服务器将遵从客户的请求转换到另外一种协议）

100 人家... 还要... （初始的请求已经接受，客户应当继续发送请求的其余部分。）

HTTP/2（超文本传输协议第 2 版，最初命名为 HTTP 2.0），是 HTTP 协议的的第二个主要版本，使用于万维网。HTTP/2 是 HTTP 协议自 1999 年 HTTP 1.1 发布后的首个更新，主要基于 SPDY 协议（是 Google 开发的基于 TCP 的应用层协议，用以最小化网络延迟，提升网络速度，优化用户的网络使用体验）。

与 HTTP 1.1 相比，主要区别包括
HTTP/2 采用二进制格式而非文本格式
HTTP/2 是完全多路复用的，而非有序并阻塞的——只需一个连接即可实现并行
使用报头压缩，HTTP/2 降低了开销
HTTP/2 让服务器可以将响应主动“推送”到客户端缓存中

</details>

<b><details><summary>3. Http 请求的整个过程</summary></b>

简洁版：
1.域名解析 --> 
2.发起 TCP 的 3 次握手 --> 
3.建立 TCP 连接后发起 http 请求 --> 
4.服务器响应 http 请求，浏览器得到 html 代码 --> 
5.浏览器解析 html 代码，并请求 html 代码中的资源（如 js、css、图片等） --> 
6.浏览器对页面进行渲染呈现给用户

</details>

<b><details><summary>4. http 缓存配置怎么设置</summary></b>

答：前端设置 http 缓存,前端设置 html 页面缓存方法：静态的 html 页面想要设置使用缓存需要通过 HTTP 的 META 设置 expires 和 cache-control

设置如下网页元信息:

```

 <meta http-equiv="Cache-Control" content="max-age=7200" />
 <meta http-equiv="Expires" content="Mon, 20 Jul 2013 23:00:00 GMT" />

```

解答:
cache-control：||no-cache||no-store||max-age

1.no-cache：

表面意为“数据内容不被缓存”，而实际数据是被缓存到本地的，只是每次请求时候直接绕过缓存这一环节直接向服务器请求最新资源，由于浏览器解释不一样，

例如 ie 中我们设置了 no-cache 之后，请求虽然不会直接使用缓存，但是还会用缓存数据与服务器数据进行一致性检测(也就是说还是有几率会用到缓存的),

firefox 中则完全无视 no-cache 存在，详细解释见 no-store;

2.no-store：

指示缓存不存储此次请求的响应部分。与 no-cache 比较来说，一个是不用缓存，一个是不存储缓存;按理来说这个设置更加粗暴直接禁用缓存，

但是具体实现起来 浏览器之间差异却特别大，一般不会直接用该字段进行设置，不过 no-store 是为了防止缓存被恶意修改存储路径导致信息被泄露而设置的，

毕竟有它的用处，在 firefox 中实现缓存是通过文件另存为将缓存副本保存到本地，直接利用 no-cache 对其是无效的，如果加上 no-store 设置的话 则可以起到与 no-cache 一样的效果;

即：cache-control:no-cache,no-store;可以确保在支持 http1.1 版本中各大浏览器回车后退刷新无缓存；

再加上 Pragma: no-cache 设置兼容版本 1.0 即可(不过为了防止一致性检测时候的万一我们还是最好加上一致性检测的内容，如下所示几种方式)；

3.max-age：

例如 Cache-control: max-age=3；表示此次请求成功后 3 秒之内发送同样请求不会去服务器重新请求，而是使用本地缓存；同样我们如果设置 max-age=0 表示立即抛弃缓存直接发送请求到服务器

以下内容来自:http://www.runoob.com/tags/att-meta-http-equiv.html

HTML <meta> http-equiv 属性
HTML meta 标签参考手册 HTML <meta> 标签

实例
每隔 30 秒刷新一次文档：

```

<head>
<meta http-equiv="refresh" content="30">
</head>

```

扩展：

与缓存有关的 header
我们来看看每个 header 的具体含义。

Request

Cache-Control: max-age=0 以秒为单位
If-Modified-Since: Mon, 19 Nov 2012 08:38:01 GMT 缓存文件的最后修改时间。
If-None-Match: "0693f67a67cc1:0" 缓存文件的 Etag 值
Cache-Control: no-cache 不使用缓存
Pragma: no-cache 不使用缓存

Response

Cache-Control: public 响应被缓存，并且在多用户间共享，  （公有缓存和私有缓存的区别，请看另一节）
Cache-Control: private 响应只能作为私有缓存，不能在用户之间共享
Cache-Control:no-cache 提醒浏览器要从服务器提取文档进行验证
Cache-Control:no-store 绝对禁止缓存（用于机密，敏感文件）
Cache-Control: max-age=60 60 秒之后缓存过期（相对时间）
Date: Mon, 19 Nov 2012 08:39:00 GMT 当前 response 发送的时间
Expires: Mon, 19 Nov 2012 08:40:01 GMT 缓存过期的时间（绝对时间）
Last-Modified: Mon, 19 Nov 2012 08:38:01 GMT 服务器端文件的最后修改时间
ETag: "20b1add7ec1cd1:0" 服务器端文件的 Etag 值

</details>

<b><details><summary>6. 常见的浏览器端的存储技术有哪些， 以及它们的优缺点和使用场景？</summary></b>

1. cookie

h5 之前，存储主要用 cookies，缺点是在请求头上带着数据，导致流量增加。大小限制 4k

操作方式：

```

document.cookie = "username=John Doe; expires=Thu, 18 Dec 2013 12:00:00 GMT; path=/" // 设置 cookie
document.cookie = "username=; expires=Thu, 01 Jan 1970 00:00:00 GMT" // 删除 cookie

```

设置 cookie 的方法比较简单，其中有几个参数可以添加

expires
过期时间，当过了到期日期时，浏览器会自动删除该 cookie，如果想删除一个 cookie，只需要把它过期时间设置成过去的时间即可
比如希望设置过期时间一年：new Date().getTime() + 365 _ 24 _ 60 _ 60 _ 1000

如果不设置过期时间，则表示这个 cookie 生命周期为浏览器会话期间，只要关闭浏览器窗口，cookie 就消失了。

path
路径，值可以是一个目录，或者是一个路径。

如果 cc.com/test/index.html 建立了一个 cookie，那么在 cc.com/test/目录里的所有页面，以及该目录下面任何子目录里的页面都可以访问这个 cookie。因此在 cc.com/test/test2/test3 里的任何页面都可以访问 cc.com/test/index.html 建立的 cookie。若 cc.com/test/ 若想访问 cc.com/test/index.html 设置的 cookes，需要把 cookies 的 path 属性设置成“/”。
在指定路径的时候，凡是来自同一服务器，URL 里有相同路径的所有 WEB 页面都可以共享 cookies。

domain
主机名，是指同一个域下的不同主机，例如：www.baidu.com 和 map.baidu.com 就是两个不同的主机名。默认情况下，一个主机中创建的 cookie 在另一个主机下是不能被访问的，但可以通过 domain 参数来实现对其的控制：document.cookie = "name=value;domain=.baidu.com"
这样，所有\*.baidu.com 的主机都可以访问该 cookie。

2. localStorage

以键值对(Key-Value)的方式存储，永久存储，永不失效，除非手动删除。IE8+支持，每个域名限制 5M

打开同域的新页面也能访问得到

操作方式：

window.localStorage.username = 'hehe' // 设置
window.localStorage.setItem('username', 'hehe') // 设置
window.localStorage.getItem('username') // 读取
window.localStorage.removeItem('username') // 删除
window.localStorage.key(1) // 读取索引为 1 的值
window.localStorage.clear() // 清除所有
可以存储数组、数字、对象等可以被序列化为字符串的内容

3. sessionStorage

sessionStorage 操作的方法与 localStroage 是一样的，区别在于 sessionStorage 在关闭页面后即被清空，而 localStorage 则会一直保存。很多时候数据只需要在用户浏览一组页面期间使用，关闭窗口后数据就可以丢弃了，这种情况使用 sessionStorage 就比较方便。

注意，刷新页面 sessionStorage 不会清除，但是打开同域新页面访问不到

4. cookie、localStorage、sessionStorage 之间的区别

他们都是保存在浏览器端的存储方式，他们之间的区别：

cookie 数据始终在同源的 http 请求中携带（即使不需要），即 cookie 在浏览器和服务器间来回传递。而 sessionStorage 和 localStorage 不会自动把数据发给服务器，仅在本地保存。cookie 数据还有路径（path）的概念，可以限制 cookie 只属于某个路径下。
存储大小限制不同，cookie 数据不能超过 4k，同时因为每次 http 请求都会携带 cookie，所以 cookie 只适合保存很小的数据，如会话标识。sessionStorage 和 localStorage 虽然也有存储大小的限制，但比 cookie 大得多，可以达到 5M 或更大。
数据有效期不同，sessionStorage：仅在当前浏览器窗口关闭前有效，自然也就不可能持久保持；localStorage：始终有效，窗口或浏览器关闭也一直保存，因此用作持久数据；cookie 只在设置的 cookie 过期时间之前一直有效，即使窗口或浏览器关闭。
作用域不同，sessionStorage 不在不同的浏览器页面中共享，即使是同一个页面；localStorage 在所有同源窗口中都是共享的；cookie 也是在所有同源窗口中都是共享的。
Web Storage 支持事件通知机制，可以将数据更新的通知发送给监听者。
Web Storage 的 api 接口使用更方便，cookie 的原生接口不友好，需要自己封装。

5. 安全性

需要注意的是，不是什么数据都适合放在 Cookie、localStorage 和 sessionStorage 中的，因为它们保存在本地容易被篡改，使用它们的时候，需要时刻注意是否有代码存在 XSS 注入的风险。所以千万不要用它们存储你系统中的敏感数据。

</details>

<b><details><summary>8. 在 HTTP 响应 Header 中，set-cookie 选项有哪些，分别代表什么含义？</summary></b>

</details>

<b><details><summary>9. 何为跨域？ 跨域请求数据有几种方式？图片/脚本 等资源有什么跨域问题。如何解决？跨域请求时如何携带 cookie</summary></b>

</details>

<b><details><summary>10. 简要描述 HTTPS 的安全机制，以及在 web 服务工程实践中需要注意的问题。描述 http2 和 https 的关系</summary></b>

</details>

<b><details><summary>11. 什么是点击劫持？如何防范？</summary></b>

</details>

<b><details><summary>12. 什么是 CSRF, 怎么造成的， 有什么防御方法？</summary></b>

</details>

<b><details><summary>13. cookie 和 Session 有什么区别？</summary></b>

</details>

<b><details><summary>14. 请简述如何在 HTML 中开启和关闭 DNS 预读取?</summary></b>

</details>

<b><details><summary>15. DNS 回源策略</summary></b>

</details>

<b><details><summary>16. https 实现原理</summary></b>

</details>

<b><details><summary>18. 怎么理解离线存储？大致描述一下怎么使用？</summary></b>

</details>

<b><details><summary>19. XSS 怎么解决？</summary></b>

</details>

<b><details><summary>20. CSRF cookie 问题？</summary></b>

</details>

<b><details><summary>21. CDN 原理</summary></b>

</details>

<b><details><summary></summary></b>

</details>

<b><details><summary></summary></b>

</details>

<b><details><summary></summary></b>

</details>
