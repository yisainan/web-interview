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

</details>

<b><details><summary>2.NodeJS 的工作原理</summary></b>

答案：事件循环

</details>

<b><details><summary>3.Node 的应用场景</summary></b>

答案：比如：RESTFUL API、实时聊天、客户端逻辑强大的单页 APP，具体的例子比如说：本地化的在线音乐应用，本地化的在线搜索应用，本地化的在线 APP 等。

</details>

<b><details><summary>4.如何用 NodeJS 搭建中间层？</summary></b>

答案：

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
考察面试者对于Node异步操作基本知识的见解

</details>

<b><details><summary>6.如何避免回调函数嵌套？</summary></b>

答案：使用 Promises将回调写成单独的函数

</details>

<b><details><summary>7.Node程序如何监听80端口？</summary></b>

答案：

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

<b><details><summary></summary></b>

答案：

</details>

<b><details><summary></summary></b>

答案：

</details>

<b><details><summary></summary></b>

答案：

</details>
