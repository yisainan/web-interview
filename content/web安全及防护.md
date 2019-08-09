# [返回主页](https://github.com/yisainan/web-interview/blob/master/README.md)

<b><details><summary>1.sql 注入原理</summary></b>

答案：就是通过把 SQL 命令插入到 Web 表单递交或输入域名或页面请求的查询字符串，最终达到欺骗服务器执行恶意的 SQL 命令。

总的来说有以下几点：

1. 永远不要信任用户的输入，要对用户的输入进行校验，可以通过正则表达式，或限制长度，对单引号和双"-"进行转换等。

2. 永远不要使用动态拼装 SQL，可以使用参数化的 SQL 或者直接使用存储过程进行数据查询存取。

3. 永远不要使用管理员权限的数据库连接，为每个应用使用单独的权限有限的数据库连接。

4. 不要把机密信息明文存放，请加密或者 hash 掉密码和敏感的信息。

</details>

<b><details><summary>2.XSS 原理及防范</summary></b>

答案：

Xss(cross-site scripting)攻击指的是攻击者往 Web 页面里插入恶意 html 标签或者 javascript 代码。比如：攻击者在论坛中放一个看似安全的链接，骗取用户点击后，窃取 cookie 中的用户私密信息；或者攻击者在论坛中加一个恶意表单，当用户提交表单的时候，却把信息传送到攻击者的服务器中，而不是用户原本以为的信任站点。

</details>

<b><details><summary>3.XSS 防范方法</summary></b>

答案：

首先代码里对用户输入的地方和变量都需要仔细检查长度和对”<”,”>”,”;”,”’”等字符做过滤；其次任何内容写到页面之前都必须加以 encode，避免不小心把 html tag 弄出来。这一个层面做好，至少可以堵住超过一半的 XSS 攻击。

首先，避免直接在 cookie 中泄露用户隐私，例如 email、密码等等。

其次，通过使 cookie 和系统 ip 绑定来降低 cookie 泄露后的危险。这样攻击者得到的 cookie 没有实际价值，不可能拿来重放。

如果网站不需要再浏览器端对 cookie 进行操作，可以在 Set-Cookie 末尾加上 HttpOnly 来防止 javascript 代码直接获取 cookie 。

尽量采用 POST 而非 GET 提交表单

</details>

<b><details><summary>4.XSS 与 CSRF 有什么区别吗？</summary></b>

答案：

XSS 是获取信息，不需要提前知道其他用户页面的代码和数据包。CSRF 是代替用户完成指定的动作，需要知道其他用户页面的代码和数据包。

要完成一次 CSRF 攻击，受害者必须依次完成两个步骤：

- 登录受信任网站 A，并在本地生成 Cookie。
- 在不登出 A 的情况下，访问危险网站 B。

</details>

<b><details><summary>5.CSRF 的防御</summary></b>

答案：

- 服务端的 CSRF 方式方法很多样，但总的思想都是一致的，就是在客户端页面增加伪随机数。
- 通过验证码的方法

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
