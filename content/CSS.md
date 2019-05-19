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

Link 属于 html 标签，而@import 是 CSS 中提供的

在页面加载的时候，link 会同时被加载，而@import 引用的 CSS 会在页面加载完成后才会加载引用的 CSS

@import 只有在 ie5 以上才可以被识别，而 link 是 html 标签，不存在浏览器兼容性问题

Link 引入样式的权重大于@import 的引用（@import 是将引用的样式导入到当前的页面中）

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

<b><details><summary>6. CSS 中可以通过哪些属性定义，使得一个 DOM 元素不显示在浏览器可视范围内？</summary></b>

最基本的：

设置 display 属性为 none，或者设置 visibility 属性为 hidden

技巧性：

设置宽高为 0，设置透明度为 0，设置 z-index 位置在-1000em

</details>

<b><details><summary>7. 超链接访问过后 hover 样式就不出现的问题是什么？如何解决？</summary></b>

答案：被点击访问过的超链接样式不在具有 hover 和 active 了,解决方法是改变 CSS 属性的排列顺序: L-V-H-A（link,visited,hover,active）

</details>

<b><details><summary>8. 什么是 Css Hack？ie6,7,8 的 hack 分别是什么？</summary></b>

答案：针对不同的浏览器写不同的 CSS code 的过程，就是 CSS hack。

示例如下：

```

#test{

    width:300px;

    height:300px;

    background-color:blue;      /_firefox_/

    background-color:red\9;      /_all ie_/

    background-color:yellow;    /_ie8_/

    +background-color:pink;        /_ie7_/

    \_background-color:orange;       /_ie6_/   

}

 :root #test { background-color:purple\9; }  /*ie9*/

@media all and (min-width:0px)

     { #test {background-color:black;} }  /*opera*/

@media screen and (-webkit-min-device-pixel-ratio:0)

{ #test {background-color:gray;} }       /*chrome and safari*/


```

</details>

<b><details><summary>9. 行内元素和块级元素的具体区别是什么？行内元素的 padding 和 margin 可设置吗？</summary></b>

块级元素(block)特性：

总是独占一行，表现为另起一行开始，而且其后的元素也必须另起一行显示;

宽度(width)、高度(height)、内边距(padding)和外边距(margin)都可控制;

内联元素(inline)特性：

和相邻的内联元素在同一行;

宽度(width)、高度(height)、内边距的 top/bottom(padding-top/padding-bottom)和外边距的 top/bottom(margin-top/margin-bottom)都不可改变（也就是 padding 和 margin 的 left 和 right 是可以设置的），就是里面文字或图片的大小。

那么问题来了，浏览器还有默认的天生 inline-block 元素（拥有内在尺寸，可设置高宽，但不会自动换行），有哪些？

答案：`<input> 、<img> 、<button> 、<texterea> 、<label>。`

</details>

<b><details><summary>10. 什么是外边距重叠？重叠的结果是什么？</summary></b>

外边距重叠就是 margin-collapse。

在 CSS 当中，相邻的两个盒子（可能是兄弟关系也可能是祖先关系）的外边距可以结合成一个单独的外边距。这种合并外边距的方式被称为折叠，并且因而所结合成的外边距称为折叠外边距。

折叠结果遵循下列计算规则：

两个相邻的外边距都是正数时，折叠结果是它们两者之间较大的值。

两个相邻的外边距都是负数时，折叠结果是两者绝对值的较大值。

两个外边距一正一负时，折叠结果是两者的相加的和。

</details>

<b><details><summary>11. rgba()和 opacity 的透明效果有什么不同？</summary></b>

rgba()和 opacity 都能实现透明效果，但最大的不同是 opacity 作用于元素，以及元素内的所有内容的透明度，

而 rgba()只作用于元素的颜色或其背景色。（设置 rgba 透明的元素的子元素不会继承透明效果！）

</details>

<b><details><summary>12. css 中可以让文字在垂直和水平方向上重叠的两个属性是什么？</summary></b>

垂直方向：line-height

水平方向：letter-spacing

那么问题来了，关于 letter-spacing 的妙用知道有哪些么？

答案:可以用于消除 inline-block 元素间的换行符空格间隙问题。

</details>

<b><details><summary>13. 如何垂直居中一个浮动元素？</summary></b>

```

// 方法一：已知元素的高宽

#div1{

    background-color:#6699FF;

    width:200px;

    height:200px;

    position: absolute;        //父元素需要相对定位

    top: 50%;

    left: 50%;

    margin-top:-100px ;   //二分之一的height，width

    margin-left: -100px;

    }

 

//方法二:未知元素的高宽

 

  #div1{

    width: 200px;

    height: 200px;

    background-color: #6699FF;

 

    margin:auto;

    position: absolute;        //父元素需要相对定位

    left: 0;

    top: 0;

    right: 0;

    bottom: 0;

    }

```

那么问题来了，如何垂直居中一个`<img>?`（用更简便的方法。）

```

#container     //<img>的容器设置如下

{

    display:table-cell;

    text-align:center;

    vertical-align:middle;

}

```

</details>

<b><details><summary>14. px 和 em 的区别。</summary></b>

px 和 em 都是长度单位，区别是，px 的值是固定的，指定是多少就是多少，计算比较容易。em 得值不是固定的，并且 em 会继承父级元素的字体大小。

浏览器的默认字体高都是 16px。所以未经调整的浏览器都符合: 1em=16px。那么 12px=0.75em, 10px=0.625em。

</details>

<b><details><summary>15. 描述一个”reset”的 CSS 文件并如何使用它。知道 normalize.css 吗？你了解他们的不同之处？</summary></b>

重置样式非常多，凡是一个前端开发人员肯定有一个常用的重置 CSS 文件并知道如何使用它们。他们是盲目的在做还是知道为什么这么做呢？原因是不同的浏览器对一些元素有不同的默认样式，如果你不处理，在不同的浏览器下会存在必要的风险，或者更有戏剧性的性发生。

你可能会用 Normalize 来代替你的重置样式文件。它没有重置所有的样式风格，但仅提供了一套合理的默认样式值。既能让众多浏览器达到一致和合理，但又不扰乱其他的东西（如粗体的标题）。

在这一方面，无法做每一个复位重置。它也确实有些超过一个重置，它处理了你永远都不用考虑的怪癖，像 HTML 的 audio 元素不一致或 line-height 不一致。

</details>

<b><details><summary>16. Sass、LESS 是什么？大家为什么要使用他们？</summary></b>

他们是 CSS 预处理器。他是 CSS 上的一种抽象层。他们是一种特殊的语法/语言编译成 CSS。

例如 Less 是一种动态样式语言. 将 CSS 赋予了动态语言的特性，如变量，继承，运算， 函数. LESS 既可以在客户端上运行 (支持 IE 6+, Webkit, Firefox)，也可一在服务端运行 (借助 Node.js)。

为什么要使用它们？

结构清晰，便于扩展。

可以方便地屏蔽浏览器私有语法差异。这个不用多说，封装对浏览器语法差异的重复处理，减少无意义的机械劳动。

可以轻松实现多重继承。

完全兼容 CSS 代码，可以方便地应用到老项目中。LESS 只是在 CSS 语法上做了扩展，所以老的 CSS 代码也可以与 LESS 代码一同编译。

</details>

<b><details><summary>17. display:none 与 visibility:hidden 的区别是什么？</summary></b>

display :  隐藏对应的元素但不挤占该元素原来的空间。

visibility:  隐藏对应的元素并且挤占该元素原来的空间。

即是，使用 CSS display:none 属性后，HTML 元素（对象）的宽度、高度等各种属性值都将“丢失”;而使用 visibility:hidden 属性后，HTML 元素（对象）仅仅是在视觉上看不见（完全透明），而它所占据的空间位置仍然存在。

</details>

<b><details><summary>18. BFC 是什么?</summary></b>

BFC（块级格式化上下文），一个创建了新的 BFC 的盒子是独立布局的，盒子内元素的布局不会影响盒子外面的元素。在同一个 BFC 中的两个相邻的盒子在垂直方向发生 margin 重叠的问题

BFC 是指浏览器中创建了一个独立的渲染区域，该区域内所有元素的布局不会影响到区域外元素的布局，这个渲染区域只对块级元素起作用

</details>

<b><details><summary>19. 哪些 css 属性可以继承？</summary></b>

可继承： font-size font-family color, ul li dl dd dt;

不可继承 ：border padding margin width height ;

</details>

<b><details><summary>20. css优先级算法如何计算？</summary></b>

!important >  id > class > 标签

  !important 比 内联优先级高

  *优先级就近原则，样式定义最近者为准;

  *以最后载入的样式为准;

</details>

<b><details><summary>21. b标签和strong标签,i标签和em标签的区别？</summary></b>

后者有语义，前者则无。

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
