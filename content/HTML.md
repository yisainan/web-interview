# [返回主页](https://github.com/yisainan/web-interview/blob/master/README.md)

<b><details><summary>1.简述一下你对 HTML 语义化的理解？</summary></b>

答案：

①**用正确的标签做正确的事情。**

②html 语义化让页面的**内容结构化，结构更清晰**，便于对浏览器、搜索引擎解析；即使在没有样式 CSS 情况下也以一种文档格式显示，并且是容易阅读的;

③ 搜索引擎的爬虫也依赖于 HTML 标记来确定上下文和各个关键字的权重，**利于 SEO**;

④ 使阅读源代码的人对网站更容易将网站分块，**便于阅读维护理解**。

</details>

<b><details><summary>2.Label 的作用是什么？是怎么用的？</summary></b>

答案：label 标签来定义表单控制间的关系,**当用户选择该标签时，浏览器会自动将焦点转到和标签相关的表单控件上**。

解析：两种用法：**一种是 id 绑定，一种是嵌套**

```html
<label for="Name">Number:</label>

<input type=“text“name="Name" id="Name"/>

<label>Date:<input type="text" name="B"/></label>
```

</details>

<b><details><summary>3.iframe 有那些缺点？</summary></b>

答案：

- iframe 会阻塞主页面的 Onload 事件；

- 搜索引擎的检索程序无法解读这种页面，不利于 SEO;

- iframe 和主页面共享连接池，而浏览器对相同域的连接有限制，所以会影响页面的并行加载。

使用 iframe 之前需要考虑这两个缺点。如果需要使用 iframe，最好是通过 javascript。动态给 iframe 添加 src 属性值，这样可以绕开以上两个问题。

</details>

<b><details><summary>4.HTML 与 XHTML —— 二者有什么区别，你觉得应该使用哪一个并说出理由。</summary></b>

答案：

```

应该使用XHTML，因为XHTML是XML重写了HTML的规范，比HTML更加严格，表现如下：

1、XHTML中所有的标记都必须有一个相应的结束标签；

2、XHTML所有标签的元素和属性的名字都必须使用小写；

3、所有的XML标记都必须合理嵌套；

4、所有的属性都必须用引号“”括起来；

5、把所有<和&特殊符号用编码表示；

6、给所有属性附一个值；

7、不要在注释内容中使用“--”；

8、图片必须使用说明文字。

```

</details>

<b><details><summary>5.HTML5 的 form 如何关闭自动完成功能？</summary></b>

答案：给不想要提示的 form 或某个 input 设置为 autocomplete=off。

</details>

<b><details><summary>6.title 与 h1 的区别、b 与 strong 的区别、i 与 em 的区别？</summary></b>

答案：

```

①title用于网站信息标题，突出网站标题或关键字，一个网站可以有多个title，seo权重高于H1；H1概括的是文章主题，一个页面最好只用一个H1，seo权重低于title。


解析：

A.从网站角度而言，title则重于网站信息标题，突出网站标题或关键字用title，一篇文章，一个页面最好只

用一个H1，H1用得太多，会稀释主题；一个网站可以有多个title，最好一个单页用一个title以便突出网站页面

主题信息。

B.从文章角度而言，H1则概括的是文章主题，突出文章主题，用H1，面对的用户，要突出其视觉效果。

C.从SEO角度而言，title的权重高于H1，其适用性要比H1广。


②b为了加粗而加粗，strong为了标明重点而加粗


解析：

A.b这个标签对应 bold，即文本加粗，其目的仅仅是为了加粗显示文本，是一种样式／风格需求；

B.strong这个标签意思是加强字符的语气，表示该文本比较重要，提醒读者／终端注意。为了达到这个目的，浏览器等终端将其加粗显示；


③ 同②i为了斜体而斜体，em为了标明重点而斜体，且对于搜索引擎来说strong和em比b和i要重视的多

```

</details>

<b><details><summary>7.请描述下 SEO 中的 TDK？</summary></b>

答案：在 SEO 中，所谓的 TDK 其实就是 title、description、keywords 这三个标签，title 标题标签，description 描述标签，keywords 关键词标签

</details>

<b><details><summary>8.每个 HTML 文件头里都有个很重要的东西，Doctype，知道这是干什么的么？</summary></b>

答案：`<!DOCTYPE>` 声明位于文档中的最前面的位置，处于 `<html>` 标签之前。

1.告知浏览器文档使用哪种 HTML 或 XHTML 规范。

2.告诉浏览器按照何种规范解析页（如果你的页面没有 DOCTYPE 的声明，那么 compatMode 默认就是 BackCompat,浏览器按照自己的方式解析渲染页面）

</details>

<b><details><summary>9. 简述一下 src 与 href 的区别。</summary></b>

答案：src 用于替换当前元素，href 用于在当前文档和引用资源之间确立联系。

</details>

<b><details><summary>10.严格模式与混杂模式</summary></b>

答案：

严格模式：以浏览器支持的最高标准运行

混杂模式：页面以宽松向下兼容的方式显示，模拟老式浏览器的行为

</details>

<b><details><summary>11.对于 WEB 标准以及 W3C 的理解与认识问题</summary></b>

答案：

<b>web 标准</b>简单来说可以分为<b>结构、表现和行为</b>。其中结构主要是有 HTML 标签组成。或许通俗点说，在页面 body 里面我们写入的标签都是为了页面的结构。表现即指 css 样式表，通过 css 可以是页面的结构标签更具美感。行为是指页面和用户具有一定的交互，同时页面结构或者表现发生变化，主要是有 js 组成。

web 标准一般是将该三部分独立分开，使其更具有模块化。但一般产生行为时，就会有结构或者表现的变化，也使这三者的界限并不那么清晰。

W3C 对 web 标准提出了规范化的要求，也就是在实际编程中的一些代码规范：包含如下几点

1.对于结构要求：（标签规范可以提高搜索引擎对页面的抓取效率，对 SEO 很有帮助）

1）标签字母要小写

2）标签要闭合

3）标签不允许随意嵌套

2.对于 css 和 js 来说

1）尽量使用外链 css 样式表和 js 脚本。是结构、表现和行为分为三块，符合规范。同时提高页面渲染速度，提高用户的体验。

2）样式尽量少用行间样式表，使结构与表现分离，标签的 id 和 class 等属性命名要做到见文知义，标签越少，加载越快，用户体验提高，代码维护简单，便于改版

3）不需要变动页面内容，便可提供打印版本而不需要复制内容，提高网站易用性。

</details>

<b><details><summary>12.列举 IE 与其他浏览器不一样的特性？</summary></b>

答案：

a. IE 的排版引擎是 Trident （又称为 MSHTML）

b. Trident 内核曾经几乎与 W3C 标准脱节（2005 年）

c. Trident 内核的大量 Bug 等安全性问题没有得到及时解决

d. JS 方面，有很多独立的方法，例如绑定事件的 attachEvent、创建事件的 createEventObject 等

e. CSS 方面，也有自己独有的处理方式，例如设置透明，低版本 IE 中使用滤镜的方式

</details>

<b><details><summary>13.前端页面有哪三层构成，分别是什么？作用是什么？</summary></b>

答案：分成：结构层、表示层、行为层。

1. 结构层（structural layer）

由 HTML 或 XHTML 之类的标记语言负责创建。标签，也就是那些出现在尖括号里的单词，对网页内容的语义含义做出了描述，但这些标签不包含任何关于如何显示有关内容的信息。例如，P 标签表达了这样一种语义：“这是一个文本段。”

2. 表示层（presentation layer）

由 CSS 负责创建。 CSS 对“如何显示有关内容”的问题做出了回答。

3. 行为层（behaviorlayer）

负责回答“内容应该如何对事件做出反应”这一问题。这是 Javascript 语言和 DOM 主宰的领域。

</details>

<b><details><summary>14. 网页验证码是干嘛的，是为了解决什么安全问题？</summary></b>

答案：

- 区分用户是计算机还是人的公共全自动程序。可以防止恶意破解密码、刷票、论坛灌水
- 有效防止黑客对某一个特定注册用户用特定程序暴力破解方式进行不断的登陆尝试

</details>

<b><details><summary>15.为什么用多个域名存储网站资源更有效？</summary></b>

答案：

1、CDN 缓存更方便

2、突破浏览器并发限制

3、节约 cookie 带宽

4、节约主域名的连接数，优化页面响应速度

5、防止不必要的安全问题

</details>

<b><details><summary>16. 页面可见性（Page Visibility）API 可以有哪些用途？</summary></b>

答案：

页面可见性： 就是对于用户来说，页面是显示还是隐藏, 所谓显示的页面，就是我们正在看的页面；隐藏的页面，就是我们没有看的页面。 因为，我们一次可以打开好多标签页面来回切换着，始终只有一个页面在我们眼前，其他页面就是隐藏的，还有一种就是.........，(把浏览器最小化，所有的页面就都不可见了)。

API 很简单，document.hidden 就返回一个布尔值，如果是 true, 表示页面可见，false 则表示，页面隐藏。 不同页面之间来回切换，触发 visibilitychange 事件。 还有一个 document.visibilityState, 表示页面所处的状态，取值：visible, hidden 等四个。

```js
document.addEventListener("visibilitychange", function() {
  if (document.hidden) {
    document.title = "hidden";
  } else {
    document.title = "visibile";
  }
});
```

我们打开这个页面，然后再打开另一个页面，来回点击这两个页面，当我们看到这个页面时，标题显示 visiable ,当我们看另一个页面时，标题显示 hidden;

动画，视频，音频都可以在页面显示时打开，在页面隐藏时关闭

解析：[参考](https://www.cnblogs.com/king18181753985/p/6510315.html)

</details>

<b><details><summary>17. Quirks(怪癖）模式是什么？它和 Standards（标准）模式有什么区别</summary></b>

答案：

1 以 ie6 为例，如果写了 DTD，就意味着这个页面将采用对 CSS 支持更好的布局，而如果没有，则采用兼容之前的布局方式。这就是 Quirks 模式（怪癖模式，诡异模式，怪异模式）。

2 区别：总体会有布局、样式解析和脚本执行三个方面的区别。

设置一个元素的宽度和高度

给`<span>`等行内元素设置 width 和 height

用 margin:0 auto 设置水平居中

从 IE6 开始，引入了 Standards 模式，标准模式中，浏览器尝试给符合标准的文档在规范上的正确处理达到在指定浏览器中的程度。

在 IE6 之前 CSS 还不够成熟，所以 IE5 等之前的浏览器对 CSS 的支持很差， IE6 将对 CSS 提供更好的支持，然而这时的问题就来了，因为有很多页面是基于旧的布局方式写的，而如果 IE6  支持 CSS 则将令这些页面显示不正常，如何在即保证不破坏现有页面，又提供新的渲染机制呢？

在写程序时我们也会经常遇到这样的问题，如何保证原来的接口不变，又提供更强大的功能，尤其是新功能不兼容旧功能时。遇到这种问题时的一个常见做法是增加参数和分支，即当某个参数为真时，我们就使用新功能，而如果这个参数   不为真时，就使用旧功能，这样就能不破坏原有的程序，又提供新功能。IE6 也是类似这样做的，它将 DTD（文档类型定义）当成了这个“参数”，因为以前的页面大家都不会去写 DTD，所以 IE6 就假定   如果写了 DTD，就意味着这个页面将采用对 CSS 支持更好的布局，而如果没有，则采用兼容之前的布局方式。这就是 Quirks 模式（怪癖模式，诡异模式，怪异模式）。

区别：

总体会有布局、样式解析和脚本执行三个方面的区别。

盒模型：在 W3C 标准中，如果设置一个元素的宽度和高度，指的是元素内容的宽度和高度，而在 Quirks  模式下，IE 的宽度和高度还包含了 padding 和 border。

设置行内元素的高宽：在 Standards 模式下，给`<span>`等行内元素设置 wdith 和 height 都不会生效，而在 quirks 模式下，则会生效。

设置百分比的高度：在 standards 模式下，一个元素的高度是由其包含的内容来决定的，如果父元素没有设置百分比的高度，子元素设置一个百分比的高度是无效的

用 margin:0 auto 设置水平居中：使用 margin:0 auto 在 standards 模式下可以使元素水平居中，但在 quirks 模式下却会失效。

（还有很多，答出什么不重要，关键是看他答出的这些是不是自己经验遇到的，还是说都是看文章看的，甚至完全不知道。）

</details>

<b><details><summary>18. div+css 的布局较 table 布局有什么优点？</summary></b>

答案：分离 方便改版 快清晰简洁 seo

1.改版的时候更方便 只要改 css 文件。

2.页面加载速度更快、结构化清晰、页面显示简洁。

3.表现与结构相分离。

4.易于优化（seo）搜索引擎更友好，排名更容易靠前。

</details>

<b><details><summary>19. 你能描述一下渐进增强和优雅降级之间的不同吗?</summary></b>

答案：

渐进增强  progressive enhancement：针对低版本浏览器进行构建页面，保证最基本的功能，然后再针对高级浏览器进行效果、交互等改进和追加功能达到更好的用户体验。

（一开始保证最基本的功能，再改进和追加功能）

优雅降级  graceful degradation：一开始就构建完整的功能，然后再针对低版本浏览器进行兼容。

（一开始就构建完整的功能，再针对低版本浏览器进行兼容。）

区别：优雅降级是从复杂的现状开始，并试图减少用户体验的供给，而渐进增强则是从一个非常基础的，能够起作用的版本开始，并不断扩充，以适应未来环境的需要。降级（功能衰减）意味着往回看；而渐进增强则意味着朝前看，同时保证其根基处于安全地带。

</details>

<b><details><summary>20. 请谈一下你对网页标准和标准制定机构重要性的理解。</summary></b>

答案：降低开发难度及开发成本，减少各种 BUG、安全问题， 提高网站易用性

</details>

<b><details><summary>21. 知道什么是微格式吗？谈谈理解。在前端构建中应该考虑微格式吗？</summary></b>

答案：微格式（Microformats）是一种让机器可读的语义化 XHTML 词汇的集合，是结构化数据的开放标准。是为特殊应用而制定的特殊格式。

优点：将智能数据添加到网页上，让网站内容在搜索引擎结果界面可以显示额外的提示。（应用范例：豆瓣，有兴趣自行 google）

</details>

<b><details><summary>22. 一个页面上有大量的图片（大型电商网站），加载很慢，你有哪些方法优化这些图片的加载，给用户更好的体验。</summary></b>

答案：

图片懒加载，在页面上的未可视区域可以添加一个滚动条事件，判断图片位置与浏览器顶端的距离与页面的距离，如果前者小于后者，优先加载。

如果为幻灯片、相册等，可以使用图片预加载技术，将当前展示图片的前一张和后一张优先下载。

如果图片为 css 图片，可以使用 CSSsprite，SVGsprite，Iconfont、Base64 等技术。

如果图片过大，可以使用特殊编码的图片，加载时会先加载一张压缩的特别厉害的缩略图，以提高用户体验。

如果图片展示区域小于图片的真实大小，则因在服务器端根据业务需要先行进行图片压缩，图片压缩后大小与展示一致。

</details>

<b><details><summary>23. html 常见兼容性问题？</summary></b>

答案：

1.双边距 BUG float 引起的   使用 display

2.3 像素问题 使用 float 引起的 使用 dislpay:inline -3px

3.超链接 hover 点击后失效   使用正确的书写顺序 link visited hover active

4.Ie z-index 问题 给父级添加 position:relative

5.Png 透明 使用 js 代码 改

6.Min-height 最小高度 ！Important 解决’

7.select 在 ie6 下遮盖 使用 iframe 嵌套

8.为什么没有办法定义 1px 左右的宽度容器（IE6 默认的行高造成的，使用 over:hidden,zoom:0.08 line-height:1px）

9.IE5-8 不支持 opacity，解决办法：

```css
.opacity {
  opacity: 0.4;
  filter: alpha(opacity=60); /_ for IE5-7 _/
  -ms-filter: "progid:DXImageTransform.Microsoft.Alpha(Opacity=60)"; /_ for IE 8_/
}
```

10.IE6 不支持 PNG 透明背景，解决办法: IE6 下使用 gif 图片

</details>

<b><details><summary>24. 对 WEB 标准以及 W3C 的理解与认识</summary></b>

答案：标签闭合、标签小写、不乱嵌套、提高搜索机器人搜索几率、使用外 链 css 和 js 脚本、结构行为表现的分离、文件下载与页面速度更快、内容能被更多的用户所访问、内容能被更广泛的设备所访问、更少的代码和组件，容易维 护、改版方便，不需要变动页面内容、提供打印版本而不需要复制内容、提高网站易用性。

</details>

<b><details><summary>25. webSocket 如何兼容低版本浏览器？</summary></b>

答案：对于低端不支持 websocket 的浏览器，一般有几个解决方案

1. 使用轮询或长连接的方式实现伪 websocket 的通信

2. 使用 flash 或其他方法实现一个 websocket 客户端 ：

[参考](https://segmentfault.com/q/1010000005000671/a-1020000005003936)
[参考](https://blog.csdn.net/u011925826/article/details/17532465)

</details>

<b><details><summary>26. 如何在页面上实现一个圆形的可点击区域？</summary></b>

答案：css3、js、map 加 area

一.border-radius (css3)

对于圆形，最直接的方法想到的就是 css3 的圆角属性，这个属性可以将 html 元素的形状设置为圆形，这之后你想对该圆形区域设置什么事件就设置什么事件(当然包括点击)。（这里就不做具体的 test 了）

二.通过事件坐标来实现（js）

也就是通过 js 来进行一个区域判断，进而简介地的形成可点区域，以下给出主要的 js 测试代码：

```js
// 获取目标元素
var box = document.getElementById("box");

// 对目标元素target的圆形区域进行一个点击事件绑定
function bindClickOnCircleArea(target, callback) {
  target.onclick = function(e) {
    e = e || window.event;

    // target中心点的坐标
    var x1 = 100;
    var y1 = 100;

    // 事件源坐标
    var x2 = e.offsetX;
    var y2 = e.offsetY;

    // 校验是否在圆形点击区，在的话就执行callback回调
    // 计算事件触发点与target中心的位置
    var len = Math.abs(Math.sqrt(Math.pow(x2 - x1, 2) + Math.pow(y2 - y1, 2)));
    // 通过半径进行校验
    if (len <= 100) {
      callback();
    } else {
      alert("死鬼，跑哪去啊，你老婆我是黄皮肤还是白皮肤都分不清了吗");
    }
  };
}

// 执行
bindClickOnCircleArea(box, function() {
  alert("老婆，你让我好找啊，呜呜呜");
});
```

三.通过 map 加 area

```html
<img src="../imgs/test.jpg" width="200" border="0" usemap="#Map" />
<map name="Map" id="Map">
  <area
    shape="circle"
    coords="100,100,100"
    href="http://www.baidu.com"
    target="_blank"
  />
</map>
```

[参考](https://zhuanlan.zhihu.com/p/48168812)

</details>

<b><details><summary>27.前端需要注意哪些SEO</summary></b>

答案：

</details>

<b><details><summary>28.html5有哪些新特性、移除了那些元素？</summary></b>

答案：

</details>

<b><details><summary>29.HTML5的离线储存怎么使用，工作原理能不能解释一下？</summary></b> 

答案：

</details>

<b><details><summary>30.浏览器是怎么对HTML5的离线储存资源进行管理和加载的呢</summary></b> 

答案：

</details>

<b><details><summary>31.HTML全局属性(global attribute)有哪些</summary></b> 

答案：

</details>

<b><details><summary>32.Canvas和SVG有什么区别？</summary></b> 

答案：

</details>

<b><details><summary>33.HTML5 为什么只需要写 `<!DOCTYPE HTML>`？</summary></b> 

答案：

</details>

<b><details><summary>34.viewport</summary></b> 

答案：

</details>

<b><details><summary>35.渲染优化</summary></b> 

答案：

</details>

<b><details><summary>36.对web标准、可用性、可访问性的理解</summary></b> 

答案：

</details>

<b><details><summary>37.meta viewport原理是什么？</summary></b> 

答案：

</details>

<b><details><summary>38.精灵图和base64如何选择？</summary></b> 

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