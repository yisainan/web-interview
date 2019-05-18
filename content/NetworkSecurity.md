# [返回主页](../README.md)

<b><details><summary>1. Get/POST的区别</summary></b>

    get参数通过url传递，post放在request body中。

    get请求在url中传递的参数是有长度限制的，而post没有。

    get比post更不安全，因为参数直接暴露在url中，所以不能用来传递敏感信息。

        get请求只能进行url编码，而post支持多种编码方式

        get请求会浏览器主动cache，而post支持多种编码方式。

        get请求参数会被完整保留在浏览历史记录里，而post中的参数不会被保留。

    GET和POST本质上就是TCP链接，并无差别。但是由于HTTP的规定和浏览器/服务器的限制，导致他们在应用过程中体现出一些不同。

    GET产生一个TCP数据包；POST产生两个TCP数据包。

长的说：

对于GET方式的请求，浏览器会把http header和data一并发送出去，服务器响应200（返回数据）；

而对于POST，浏览器先发送header，服务器响应100 continue，浏览器再发送data，服务器响应200 ok（返回数据）。

（据研究，在网络环境好的情况下，发一次包的时间和发两次包的时间差别基本可以无视。而在网络环境差的情况下，两次包的TCP在验证数据包完整性上，有非常大的优点。）

</details>

<b><details><summary>2. Http状态码，Http2是什么</summary></b>

</details>

<b><details><summary>3. Http请求的整个过程</summary></b>

</details>

<b><details><summary>4. http 缓存配置怎么设置</summary></b>

</details>

<b><details><summary>5. 操作系统线程怎么操作</summary></b>

</details>

<b><details><summary>6. 常见的浏览器端的存储技术有哪些， 以及它们的优缺点和使用场景？</summary></b>

</details>

<b><details><summary>7. 最常见的跨域技术方案有哪些？其中 JSONP的原理和缺点是什么？</summary></b>

</details>

<b><details><summary>8. 在HTTP响应 Header 中，set-cookie 选项有哪些，分别代表什么含义？</summary></b>

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

<b><details><summary>17. 浏览器从输入 URL 到页面加载发生了什么</summary></b>

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
