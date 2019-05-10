# web-interview

<b><details><summary>💡 关于</summary></b>

📚 本仓库是面向 <b>web 前端</b> 方向校招求职者、初学者的基础知识总结

🙏 仓库内容如有错误或改进欢迎 issue 或 pr。由于本人水平有限，仓库中的知识点有来自本人原创、读书笔记、书籍、博文等，非原创均已标明出处，如有遗漏，请 issue 提出。本仓库遵循 CC BY-NC-SA 4.0 协议，转载请注明出处。

</details>

<b><details><summary>➕ HTML</summary></b>

- <details><summary>1.简述一下你对HTML语义化的理解？</summary>

  用正确的标签做正确的事情。

  html 语义化让页面的内容结构化，结构更清晰，便于对浏览器、搜索引擎解析;即使在没有样式 CSS 情况下也以一种文档格式显示，并且是容易阅读的;

  搜索引擎的爬虫也依赖于 HTML 标记来确定上下文和各个关键字的权重，利于 SEO;

  使阅读源代码的人对网站更容易将网站分块，便于阅读维护理解。

  </details>

- <details><summary>2.Label的作用是什么？是怎么用的？</summary>

  label 标签来定义表单控制间的关系,当用户选择该标签时，浏览器会自动将焦点转到和标签相关的表单控件上。

  ```

  <label for="Name">Number:</label>

  <input type=“text“name="Name" id="Name"/>

  <label>Date:<input type="text" name="B"/></label>

  ```

  </details>

- <details><summary>3.iframe有那些缺点？</summary>

  - iframe 会阻塞主页面的 Onload 事件；

  - 搜索引擎的检索程序无法解读这种页面，不利于 SEO;

  - iframe 和主页面共享连接池，而浏览器对相同域的连接有限制，所以会影响页面的并行加载。

  使用 iframe 之前需要考虑这两个缺点。如果需要使用 iframe，最好是通过 javascript。动态给 iframe 添加 src 属性值，这样可以绕开以上两个问题。

  </details>

- <details><summary>4.HTML与XHTML —— 二者有什么区别，你觉得应该使用哪一个并说出理由。</summary>

  ```

  1.XHTML 元素必须被正确地嵌套。

  错误：<p><span>this is example.</p></span>

  正确：<p><span>this is example.</span></p>

  2.XHTML 元素必须被关闭。

  错误：<p>this is example.

  正确：<p>this is example.</p>

  3.标签名必须用小写字母。

  错误：<P>this is example.<P>

  正确：<p>this is example.</p>

  3.1空标签也必须被关闭

  错误：<br>

  正确：<br/>

  4.XHTML 文档必须拥有根元素。

  所有的 XHTML 元素必须被嵌套于 <html> 根元素中。

  ```

  </details>

- <details><summary>5.常见的浏览器内核有哪些？</summary>

  Trident 内核：IE,MaxThon,TT,The World,360,搜狗浏览器等。[又称 MSHTML]

  Gecko 内核：Netscape6 及以上版本，FF,MozillaSuite/SeaMonkey 等

  Presto 内核：Opera7 及以上。 [Opera 内核原为：Presto，现为：Blink;]

  Webkit 内核：Safari,Chrome 等。 [ Chrome 的：Blink（WebKit 的分支）]

  </details>

- <details><summary>6.HTML5的form如何关闭自动完成功能？</summary>

  给不想要提示的 form 或某个 input 设置为 autocomplete=off。

  </details>

- <details><summary>8.实现不使用 border 画出1px高的线，在不同浏览器的标准模式与怪异模式下都能保持一致的效果。</summary>

  ```

  <div style="height:1px;overflow:hidden;background:red"></div>

  ```

  </details>

- <details><summary>9.title与h1的区别、b与strong的区别、i与em的区别？</summary>

  ```

  title属性没有明确意义只表示是个标题，H1则表示层次明确的标题，对页面信息的抓取也有很大的影响；

  strong是标明重点内容，有语气加强的含义，使用阅读设备阅读网络时：<strong>会重读，而<B>是展示强调内容。

  i内容展示为斜体，em表示强调的文本；

  Physical Style Elements -- 自然样式标签

  b, i, u, s, pre

  Semantic Style Elements -- 语义样式标签

  strong, em, ins, del, code

  应该准确使用语义样式标签, 但不能滥用, 如果不能确定时首选使用自然样式标签。

  ```

  </details>

- <details><summary>10.请描述下SEO中的TDK？</summary>

  在 SEO 中，所谓的 TDK 其实就是 title、description、keywords 这三个标签，这三个标签在网站的优化过程中

  title 标题标签，description 描述标签，keywords 关键词标签

  </details>

- <details><summary>13.前端页面有哪三层构成，分别是什么？作用是什么？</summary>

  分成：结构层、表示层、行为层。

  结构层（structural layer）

  由 HTML 或 XHTML 之类的标记语言负责创建。标签，也就是那些出现在尖括号里的单词，对网页内容的语义含义做出了描述，但这些标签不包含任何关于如何显示有关内容的信息。例如，P 标签表达了这样一种语义：“这是一个文本段。”

  表示层（presentation layer）

  由 CSS 负责创建。 CSS 对“如何显示有关内容”的问题做出了回答。

  行为层（behaviorlayer）

  负责回答“内容应该如何对事件做出反应”这一问题。这是 Javascript 语言和 DOM 主宰的领域。

  </details>

- <details><summary>14.每个HTML文件头里都有个很重要的东西，Doctype，知道这是干什么的么？</summary>

  <!DOCTYPE> 声明位于文档中的最前面的位置，处于 <html> 标签之前。

  作用：

  1.告知浏览器文档使用哪种 HTML 或 XHTML 规范。

  2.告诉浏览器按照何种规范解析页（如果你的页面没有 DOCTYPE 的声明，那么 compatMode 默认就是 BackCompat,浏览器按照自己的方式解析渲染页面）

  </details>

- <details><summary>16.为什么用多个域名存储网站资源更有效？</summary>

  1、CDN 缓存更方便

  2、突破浏览器并发限制

  3、节约 cookie 带宽

  4、节约主域名的连接数，优化页面响应速度

  5、防止不必要的安全问题

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

</details>

<b><details><summary>📦 CSS</summary></b>

- <details><summary>1.介绍一下标准的CSS的盒子模型？低版本IE的盒子模型有什么不同的？</summary>

  （1）有两种， IE 盒子模型、W3C 盒子模型；

  （2）盒模型： 内容(content)、填充(padding)、边界(margin)、 边框(border)；

  （3）区 别： IE 的 content 部分把 border 和 padding 计算了进去;

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

</details>

<b><details><summary>〽️ JS</summary></b>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

</details>

<b><details><summary>⚡️ Vue</summary></b>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

</details>

<b><details><summary>❓ React</summary></b>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

</details>

<b><details><summary>💻 操作系统</summary></b>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

</details>

<b><details><summary>☁️ 计算机网络</summary></b>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

</details>

<b><details><summary>🌩 网络编程</summary></b>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

</details>

<b><details><summary>💾 数据库</summary></b>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

</details>

<b><details><summary>📏 设计模式</summary></b>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

</details>

<b><details><summary>⚙️ 链接装载库</summary></b>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

</details>

<b><details><summary>📚 书籍</summary></b>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

</details>

<b><details><summary>🔱 C/C++ 发展方向</summary></b>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

</details>

<b><details><summary>👬 贡献者</summary></b>

包括勘误的 Issue、PR，排序按照贡献时间。

[tamarous](https://github.com/tamarous)

</details>

<b><details><summary>📜 License</summary></b>

本仓库遵循 CC BY-NC-SA 4.0（署名 - 非商业性使用） 协议，转载请注明出处。

[![CC BY-NC-SA 4.0](https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png)](LICENSE)

</details>
