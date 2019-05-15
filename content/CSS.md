# [返回主页](../README.md)

<b><details><summary>1.介绍一下标准的 CSS 的盒子模型？低版本 IE 的盒子模型有什么不同的？</summary></b>

（1）有两种， IE 盒子模型、W3C 盒子模型；

（2）盒模型： 内容(content)、填充(padding)、边界(margin)、 边框(border)；

（3）区 别： IE 的 content 部分把 border 和 padding 计算了进去;

</details>

<b><details><summary>2.CSS 隐藏元素的几种方法（至少说出三种）</summary></b>

Opacity:元素本身依然占据它自己的位置并对网页的布局起作用。它也将响应用户交互;

Visibility:与 opacity 唯一不同的是它不会响应任何用户交互。此外，元素在读屏软件中也会被隐藏;

Display:display 设为 none 任何对该元素直接打用户交互操作都不可能生效。此外，读屏软件也不会读到元素的内容。这种方式产生的效果就像元素完全不存在;

Position:不会影响布局，能让元素保持可以操作;

Clip-path:clip-path 属性还没有在 IE 或者 Edge 下被完全支持。如果要在你的 clip-path 中使用外部的 SVG 文件，浏览器支持度还要低;

</details>

<b><details><summary>3.CSS 清除浮动的几种方法（至少两种）</summary></b>

使用带 clear 属性的空元素

使用 CSS 的 overflow 属性；

使用 CSS 的:after 伪元素；

使用邻接元素处理；

</details>

<b><details><summary>4.页面导入样式时，使用 link 和@import 有什么区别？</summary></b>

link 属于 XHTML 标签，除了加载 CSS 外，还能用于定义 RSS, 定义 rel 连接属性等作用；而@import 是 CSS 提供的，只能用于加载 CSS;
页面被加载的时，link 会同时被加载，而@import 引用的 CSS 会等到页面被加载完再加载;

import 是 CSS2.1 提出的，只在 IE5 以上才能被识别，而 link 是 XHTML 标签，无兼容问题;

</details>

<b><details><summary>5.CSS 选择符有哪些？哪些属性可以继承？优先级算法如何计算？ CSS3 新增伪类有那些？</summary></b>

id 选择器（ # myid）

类选择器（.myclassname）

标签选择器（div, h1, p）

相邻选择器（h1 + p）

子选择器（ul > li）

后代选择器（li a）

通配符选择器（ \* ）

属性选择器（a[rel = “external”]）

伪类选择器（a: hover, li: nth – child）

可继承的样式： font-size font-family color, UL LI DL DD DT;

不可继承的样式：border padding margin width height ;

优先级就近原则，同权重情况下样式定义最近者为准;

优先级为:

!important > id > class > tag

important 比 内联优先级高

</details>

<b><details><summary></summary></b>

</details>

<b><details><summary></summary></b>

</details>

<b><details><summary></summary></b>

</details>

<b><details><summary></summary></b>

</details>

<b><details><summary></summary></b>

</details>

<b><details><summary></summary></b>

</details>

<b><details><summary></summary></b>

</details>

<b><details><summary></summary></b>

</details>

<b><details><summary></summary></b>

</details>

<b><details><summary></summary></b>

</details>

<b><details><summary></summary></b>

</details>
