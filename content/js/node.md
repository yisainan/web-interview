# [返回主页](https://github.com/yisainan/web-interview/blob/master/README.md)

<b><details><summary>1.为什么用 Nodejs,它有哪些缺点？</summary></b>

答案：

- 事件驱动，通过闭包很容易实现客户端的生命活期。
- 不用担心多线程，锁，并行计算的问题
- V8 引擎速度非常快
- 对于游戏来说，写一遍游戏逻辑代码，前端后端通用

当然 Nodejs 也有一些缺点：

- nodejs 更新很快，可能会出现版本兼容
- nodejs 还不算成熟，还没有大制作
- nodejs 不像其他的服务器，对于不同的链接，不支持进程和线程操作

[参与互动](https://github.com/yisainan/web-interview/issues/371)

</details>

<b><details><summary>2.NodeJS 的工作原理</summary></b>

答案：事件循环

[参与互动](https://github.com/yisainan/web-interview/issues/372)

</details>

<b><details><summary>3.Node 的应用场景</summary></b>

答案：比如：RESTFUL API、实时聊天、客户端逻辑强大的单页 APP，具体的例子比如说：本地化的在线音乐应用，本地化的在线搜索应用，本地化的在线 APP 等。

- 实时应用：如在线聊天，实时通知推送等等（如 socket.io）
- 分布式应用：通过高效的并行 I/O 使用已有的数据
- 工具类应用：海量的工具，小到前端压缩部署（如 grunt），大到桌面图形界面应用程序
- 游戏类应用：游戏领域对实时和并发有很高的要求（如网易的 pomelo 框架）
- 利用稳定接口提升 Web 渲染能力
- 前后端编程语言环境统一：前端开发人员可以非常快速地切入到服务器端的开发（如著名的纯 Javascript 全栈式 MEAN 架构）

[参与互动](https://github.com/yisainan/web-interview/issues/373)

</details>

<b><details><summary>4.如何用 NodeJS 搭建中间层？</summary></b>

答案：

[参与互动](https://github.com/yisainan/web-interview/issues/374)

</details>

<b><details><summary>5.什么是 error-first callback ？</summary></b>

答案：error-first callback 用来传递错误和数据。第一个参数永远是一个错误对象（error-object），回调函数必须检查它。余下的参数用不过来传递数据。

解析：

```js
fs.readFile(filePath, function(err, data) {
  if (err) {
    //处理出现错误的情况
  }
  //处理数据
});
```

考察面试者对于 Node 异步操作基本知识的见解

[参与互动](https://github.com/yisainan/web-interview/issues/375)

</details>

<b><details><summary>6.如何避免回调函数嵌套？</summary></b>

答案：使用 Promises 将回调写成单独的函数

[参与互动](https://github.com/yisainan/web-interview/issues/376)

</details>

<b><details><summary>7.Node 程序如何监听 80 端口？</summary></b>

答案：脑筋急转弯！你不应该直接使用 Node 监听 80 端口（在\*nix 系统中），这样做需要 root 权限，对于运行程序来说这不是一个好主意。

不过，你可以使 Node 监听 1024 以上的端口，然后在 Node 前面部署 nginx 反向代理。

解析：[参考](https://blog.csdn.net/newborn2012/article/details/23860687)

[参与互动](https://github.com/yisainan/web-interview/issues/377)

</details>

<b><details><summary>8.什么是事件循环（event loop）？</summary></b>

答案：至少从开发者的角度来看，Node.js 是单线程运行的。底层使用 libuv 使用多线程。
每一个 I/O 操作都需要一个回调，一旦操作完成会被事件循环执行

解析：[参考](http://blog.csdn.net/yanghua_kobe/article/details/12145537)

[参与互动](https://github.com/yisainan/web-interview/issues/378)

</details>

<b><details><summary>9.使用什么工具检查代码风格？</summary></b>

答案：

- JSLint by Douglas Crockford
- JSHint
- ESLint
- JSCS
  开发团队项目时，强制指定代码风格和使用静态分析，捕捉常见的错误，这些工具都非常有用。

[参与互动](https://github.com/yisainan/web-interview/issues/379)

</details>

<b><details><summary>10.操作错误和程序错误的区别是什么？</summary></b>

答案：操作错误不是 bug，是系统的问题，例如超时或者硬件故障。
另一方面，程序错误（programmer errors）是实际的错误。

[参与互动](https://github.com/yisainan/web-interview/issues/380)

</details>

<b><details><summary>11.为什么 npmshrinkwarp 非常有用？</summary></b>

答案：这个命令在部署 Node.js 应用时是非常有用的——它可以保证所部属的版本就是依赖的版本。

解析：[参考](http://www.tuicool.com/articles/EBVNV37)

[参与互动](https://github.com/yisainan/web-interview/issues/381)

</details>

<b><details><summary>12.什么是 stub？说出他的用途？举个使用场景？</summary></b>

答案：Stubs 是模拟模块或组件行为的程序。
Stubs 提供已知的答案来调用函数，另外你还可以断言哪个 stubs 被调用

[参与互动](https://github.com/yisainan/web-interview/issues/382)

</details>

<b><details><summary>13.什么是测试金字塔？在做 HTTP API 的时候要怎么实现？</summary></b>

答案：测试金字塔意思是在写测试时应该编写的底层但愿测试要多于高级的端到端测试。
对于 HTTP APIs，应该归结为：

- 对你的模型多很多单元测试
- 在你的模型与其他交互时更少的集成测试
- 更少的验收测试，在 HTTP 端

[参与互动](https://github.com/yisainan/web-interview/issues/383)

</details>

<b><details><summary>14.你最熟悉的 Node 框架是什么？为什么？</summary></b>

答案：[参考](http://ourjs.com/detail/15%E4%B8%AA%E6%9C%80%E5%A5%BD%E7%94%A8%E7%9A%84node-js%E5%90%8E%E7%AB%AF%E6%A1%86%E6%9E%B6)

[参与互动](https://github.com/yisainan/web-interview/issues/384)

</details>

<b><details><summary>15.你最喜欢的 HTTP 框架，并说明原因？</summary></b>

答案：LiteHttp 好多的优点
单线程 灵活的架构 轻量级 多文件上传 自动重定向 禁用一种或多种网络

解析：[参考](http://blog.csdn.net/kymjs/article/details/45716797)

[参与互动](https://github.com/yisainan/web-interview/issues/385)

</details>

<b><details><summary>16. 对 Node 的优点和缺点提出了自己的看法</summary></b>

答案：

- （优点）因为 Node 是基于事件驱动和无阻塞的，所以非常适合处理并发请求，
  因此构建在 Node 上的代理服务器相比其他技术实现（如 Ruby）的服务器表现要好得多。
  此外，与 Node 代理服务器交互的客户端代码是由 javascript 语言编写的，
  因此客户端和服务器端都用同一种语言编写，这是非常美妙的事情。

- （缺点）Node 是一个相对新的开源项目，所以不太稳定，它总是一直在变，
  而且缺少足够多的第三方库支持。看起来，就像是 Ruby/Rails 当年的样子。

[参与互动](https://github.com/yisainan/web-interview/issues/386)

</details>

<b><details><summary>17.需求：实现一个页面操作不会整页刷新的网站，并且能在浏览器前进、后退时正确响应。给出你的技术实现方案？</summary></b>

答案：至少给出自己的思路（url-hash,可以使用已有的一些框架 history.js 等）

[参与互动](https://github.com/yisainan/web-interview/issues/387)

</details>

<b><details><summary>18.(如果会用 node)知道 route, middleware, cluster, nodemon, pm2, server-side rendering 么?</summary></b>

答案：

[参与互动](https://github.com/yisainan/web-interview/issues/388)

</details>

<b><details><summary>19.解释一下 Backbone 的 MVC 实现方式？</summary></b>

答案：

[参与互动](https://github.com/yisainan/web-interview/issues/389)

</details>

<b><details><summary>20.什么是“前端路由”?什么时候适合使用“前端路由”? “前端路由”有哪些优点和缺点?</summary></b>

答案：

[参与互动](https://github.com/yisainan/web-interview/issues/390)

</details>

<b><details><summary>21.对 Node 的优点和缺点提出了自己的看法？</summary></b>

答案：

优点：

1. 因为 Node 是基于事件驱动和无阻塞的，所以非常适合处理并发请求，因此构建在 Node 上的代理服务器相比其他技术实现（如 Ruby）的服务器表现要好得多。
2. 与 Node 代理服务器交互的客户端代码是由 javascript 语言编写的，因此客户端和服务器端都用同一种语言编写，这是非常美妙的事情。

缺点：

1. Node 是一个相对新的开源项目，所以不太稳定，它总是一直在变。
2. 缺少足够多的第三方库支持。看起来，就像是 Ruby/Rails 当年的样子（第三方库现在已经很丰富了，所以这个缺点可以说不存在了）。

[参与互动](https://github.com/yisainan/web-interview/issues/391)

</details>