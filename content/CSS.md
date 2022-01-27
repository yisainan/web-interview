# [返回主页](https://github.com/yisainan/web-interview/blob/master/README.md)

<b><details><summary>1. 实现不使用 border 画出 1px 高的线，在不同浏览器的标准模式与怪异模式下都能保持一致的效果。</summary></b>

参考答案：

``` html
<div style="height:1px;overflow:hidden;background:red"></div>
```

[参与互动](https://github.com/yisainan/web-interview/issues/22)

</details>

<b><details><summary>2. 介绍一下标准的 CSS 的盒子模型？低版本 IE 的盒子模型有什么不同的？</summary></b>

参考答案：

（1）有两种， IE 盒子模型、W3C 盒子模型；

（2）盒模型： 内容(content)、填充(padding)、边界(margin)、 边框(border)；

（3）区 别： IE 的 content 部分把 border 和 padding 计算了进去; 

相关知识点：

```
（1）有两种盒子模型：IE盒模型（border-box）、W3C标准盒模型（content-box）
（2）盒模型：分为内容（content）、填充（padding）、边界（margin）、边框（border）四个部分

IE盒模型和W3C标准盒模型的区别：

（1）W3C标准盒模型：属性width，height只包含内容content，不包含border和padding
（2）IE盒模型：属性width，height包含content、border和padding，指的是content
+padding+border。

在ie8+浏览器中使用哪个盒模型可以由box-sizing（CSS新增的属性）控制，默认值为content-box，即标准盒模型；
如果将box-sizing设为border-box则用的是IE盒模型。如果在ie6，7，8中DOCTYPE缺失会将盒子模型解释为IE
盒子模型。若在页面中声明了DOCTYPE类型，所有的浏览器都会把盒模型解释为W3C盒模型。
```

回答：

```
盒模型都是由四个部分组成的，分别是margin、border、padding和content。

标准盒模型和IE盒模型的区别在于设置width和height时，所对应的范围不同。标准盒模型的width和height属性的
范围只包含了content，而IE盒模型的width和height属性的范围包含了border、padding和content。

一般来说，我们可以通过修改元素的box-sizing属性来改变元素的盒模型。
```

详细的资料可以参考：
[《CSS 盒模型详解》](https://juejin.im/post/59ef72f5f265da4320026f76)

[参与互动](https://github.com/yisainan/web-interview/issues/23)

</details>

<b><details><summary>3. CSS 隐藏元素的几种方法（至少说出三种）</summary></b>

参考答案：

Opacity: 元素本身依然占据它自己的位置并对网页的布局起作用。它也将响应用户交互; 

Visibility: 与 opacity 唯一不同的是它不会响应任何用户交互。此外，元素在读屏软件中也会被隐藏; 

Display:display 设为 none 任何对该元素直接打用户交互操作都不可能生效。此外，读屏软件也不会读到元素的内容。这种方式产生的效果就像元素完全不存在; 

Position: 不会影响布局，能让元素保持可以操作; 

Clip-path:clip-path 属性还没有在 IE 或者 Edge 下被完全支持。如果要在你的 clip-path 中使用外部的 SVG 文件，浏览器支持度还要低; 

[参与互动](https://github.com/yisainan/web-interview/issues/24)

</details>

<b><details><summary>4. CSS 清除浮动的几种方法（至少两种）</summary></b>

参考答案：

``` 
清除浮动： 核心：clear:both;

1.使用额外标签法（不推荐使用）

在浮动的盒子下面再放一个标签，使用 clear:both;来清除浮动

a 内部标签：会将父盒子的高度重新撑开

b 外部标签：只能将浮动盒子的影响清除，但是不会撑开盒子

2.使用 overflow 清除浮动（不推荐使用）

先找到浮动盒子的父元素，给父元素添加一个属性：overflow:hidden;就会清除子元素对页面的影响

3.使用伪元素清除浮动(用的最多)

伪元素：在页面上不存在的元素，但是可以通过 css 添加上去

种类：
      :after(在。。。之后)
      :before(在。。。之前)

注意：每个元素都有自己的伪元素

.clearfix:after {
    content:"";
    height:0;
    line-height:0;
    display:block;
    clear:both;
    visibility:hidden;  /_将元素隐藏起来_/ 
      在页面的 clearfix 元素后面添加了一个空的块级元素
     （这个元素的高为 0 行高也为 0   并且这个元素清除了浮动）
}
.clearfix {
  zoom:1;/_为了兼容 IE6_/
}
```

[参与互动](https://github.com/yisainan/web-interview/issues/25)

</details>

<b><details><summary>5. 页面导入样式时，使用 link 和@import 有什么区别？</summary></b>

参考答案：

1\. Link 属于 html 标签，而@import 是 CSS 中提供的

2\. 在页面加载的时候，link 会同时被加载，而@import 引用的 CSS 会在页面加载完成后才会加载引用的 CSS

3\. @import 只有在 ie5 以上才可以被识别，而 link 是 html 标签，不存在浏览器兼容性问题

4\. Link 引入样式的权重大于@import 的引用（@import 是将引用的样式导入到当前的页面中）

[参与互动](https://github.com/yisainan/web-interview/issues/26)

</details>

<b><details><summary>6. 伪元素和伪类的区别？</summary></b>

参考答案：

1、伪元素使用 2 个冒号，常见的有：::before，::after，::first-line，::first-letter，::selection、::placeholder 等；

      伪类使用1个冒号，常见的有：:hover，:link，:active，:target，:not()，:focus等。

2、伪元素添加了一个页面中没有的元素（只是从视觉效果上添加了，不是在文档树中添加）；

      伪类是给页面中已经存在的元素添加一个类。

解析：

CSS 伪元素是添加到选择器的关键字，去选择元素的特定部分。它们可以用于装饰（ `:first-line` ， `:first-letter` ）或将元素添加到标记中（与 content:... 组合），而不必修改标记（ `:before` ， `:after` ）。

* `:first-line` 和 `:first-letter` 可以用来修饰文字。
* 上面提到的 `.clearfix` 方法中，使用 `clear: both` 来添加不占空间的元素。
* 使用 `:before` 和 `after` 展示提示中的三角箭头。鼓励关注点分离，因为三角被视为样式的一部分，而不是真正的 DOM。如果不使用额外的 HTML 元素，只用 CSS 样式绘制三角形是不太可能的。

[参考](https://css-tricks.com/almanac/selectors/a/after-and-before/)

[参与互动](https://github.com/yisainan/web-interview/issues/27)

</details>

<b><details><summary>7. CSS 选择符有哪些？哪些属性可以继承？优先级算法如何计算？ CSS3 新增伪类有那些？</summary></b>

参考答案：

``` 

（1）id选择器（#myid）
（2）类选择器（.myclassname）
（3）标签选择器（div,h1,p）
（4）后代选择器（h1 p）
（5）相邻后代选择器（子）选择器（ul>li）
（6）兄弟选择器（li~a）
（7）相邻兄弟选择器（li+a）
（8）属性选择器（a[rel="external"]）
（9）伪类选择器（a:hover,li:nth-child）
（10）伪元素选择器（::before、::after）
（11）通配符选择器（*）

 * 继承： font-size font-family color, UL LI DL DD DT;

 * 不可继承 ：border padding margin width height ;

 * 优先级就近原则，样式定义最近者为准;

 * 载入样式以最后载入的定位为准;

优先级为:

       !important >  id > class > tag  

       important 比 内联优先级高

CSS3新增伪类举例：

    p:first-of-type 选择属于其父元素的首个 <p> 元素的每个 <p> 元素。

    p:last-of-type  选择属于其父元素的最后 <p> 元素的每个 <p> 元素。

    p:only-of-type  选择属于其父元素唯一的 <p> 元素的每个 <p> 元素。

    p:only-child    选择属于其父元素的唯一子元素的每个 <p> 元素。

    p:nth-child(2)  选择属于其父元素的第二个子元素的每个 <p> 元素。

    :enabled、:disabled 控制表单控件的禁用状态。

    :checked，单选框或复选框被选中。

```

[参与互动](https://github.com/yisainan/web-interview/issues/28)

</details>

<b><details><summary>8. 行内元素和块级元素的具体区别是什么？行内元素的 padding 和 margin 可设置吗？</summary></b>

参考答案：

* 块级元素(block)特性：

  + 总是独占一行，表现为另起一行开始，而且其后的元素也必须另起一行显示; 
  + 宽度(width)、高度(height)、内边距(padding)和外边距(margin)都可控制; 

* 内联元素(inline)特性：
  + 和相邻的内联元素在同一行; 
  + 宽度(width)、高度(height)、内边距的 top/bottom(padding-top/padding-bottom)和外边距的 top/bottom(margin-top/margin-bottom)都不可改变（也就是 padding 和 margin 的 left 和 right 是可以设置的），就是里面文字或图片的大小。

那么问题来了，浏览器还有默认的天生 inline-block 元素（拥有内在尺寸，可设置高宽，但不会自动换行），有哪些？

参考答案： `<input> 、<img> 、<button> 、<texterea> 、<label>。` 

[参与互动](https://github.com/yisainan/web-interview/issues/29)

</details>

<b><details><summary>9. 什么是外边距重叠？重叠的结果是什么？</summary></b>

参考答案：

外边距重叠就是 margin-collapse。

在 CSS 当中，相邻的两个盒子（可能是兄弟关系也可能是祖先关系）的外边距可以结合成一个单独的外边距。这种合并外边距的方式被称为折叠，并且因而所结合成的外边距称为折叠外边距。

折叠结果遵循下列计算规则：

1\. 两个相邻的外边距都是正数时，折叠结果是它们两者之间较大的值。

2\. 两个相邻的外边距都是负数时，折叠结果是两者绝对值的较大值。

3\. 两个外边距一正一负时，折叠结果是两者的相加的和。

[参与互动](https://github.com/yisainan/web-interview/issues/30)

</details>

<b><details><summary>10. rgba()和 opacity 的透明效果有什么不同？</summary></b>

参考答案：

rgba()和 opacity 都能实现透明效果，但最大的不同是 opacity 作用于元素，以及元素内的所有内容的透明度，

而 rgba()只作用于元素的颜色或其背景色。（设置 rgba 透明的元素的子元素不会继承透明效果！）

[参与互动](https://github.com/yisainan/web-interview/issues/31)

</details>

<b><details><summary>11. css 中可以让文字在垂直和水平方向上重叠的两个属性是什么？</summary></b>

参考答案：

垂直方向：line-height

水平方向：letter-spacing

那么问题来了，关于 letter-spacing 的妙用知道有哪些么？

参考答案: 可以用于消除 inline-block 元素间的换行符空格间隙问题。

[参与互动](https://github.com/yisainan/web-interview/issues/32)

</details>

<b><details><summary>12. px 和 em 的区别。</summary></b>

参考答案：px 和 em 都是长度单位，区别是，px 的值是固定的，指定是多少就是多少，计算比较容易。em 得值不是固定的，并且 em 会继承父级元素的字体大小。

浏览器的默认字体高都是 16px。所以未经调整的浏览器都符合: 1em=16px。那么 12px=0. 75em, 10px=0. 625em。

[参与互动](https://github.com/yisainan/web-interview/issues/33)

</details>

<b><details><summary>13. 如何垂直居中一个元素？</summary></b>

参考答案：

方法一：绝对定位居中（原始版之已知元素的高宽）

``` css
.content {
    width: 200px;
    height: 200px;
    background-color: #6699ff;
    position: absolute;
    /*父元素需要相对定位*/
    top: 50%;
    left: 50%;
    margin-top: -100px;
    /*设为高度的1/2*/
    margin-left: -100px;
    /*设为宽度的1/2*/
}
```

方法二：绝对定位居中（改进版之一未知元素的高宽）

``` css
.content {
    width: 200px;
    height: 200px;
    background-color: #6699ff;
    position: absolute;
    /*父元素需要相对定位*/
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    /*在水平和垂直方向上各偏移-50%*/
}
```

方法三：绝对定位居中（改进版之二未知元素的高宽）

``` css
.content {
    width: 200px;
    height: 200px;
    background-color: #6699ff;
    margin: auto;
    /*很关键的一步*/
    position: absolute;
    /*父元素需要相对定位*/
    left: 0;
    top: 0;
    right: 0;
    bottom: 0;
    /*让四个定位属性都为0*/
}
```

方法四：flex 布局居中

``` css
body {
    display: flex;
    /*设置外层盒子display为flex*/
    align-items: center;
    /*设置内层盒子的垂直居中*/
    justify-content: center;

    /*设置内层盒子的水平居中*/
    .content {
        width: 200px;
        height: 200px;
        background-color: #6699ff;
    }
}
```

那么问题来了，如何垂直居中一个 img（用更简便的方法。）

``` css
.content {
    //img的容器设置如下
    display: table-cell;
    text-align: center;
    vertical-align: middle;
}
```

[参与互动](https://github.com/yisainan/web-interview/issues/34)

</details>

<b><details><summary>14. BFC </summary></b>

参考答案：

* 什么是 BFC

  BFC（Block Formatting Context）格式化上下文，是 Web 页面中盒模型布局的 CSS 渲染模式，指一个独立的渲染区域或者说是一个隔离的独立容器。

* 形成 BFC 的条件

  + 浮动元素，float 除 none 以外的值
  + 定位元素，position（absolute，fixed）
  + display 为以下其中之一的值 inline-block，table-cell，table-caption
  + overflow 除了 visible 以外的值（hidden，auto，scroll）

* BFC 的特性
  + 内部的 Box 会在垂直方向上一个接一个的放置。
  + 垂直方向上的距离由 margin 决定
  + bfc 的区域不会与 float 的元素区域重叠。
  + 计算 bfc 的高度时，浮动元素也参与计算
  + bfc 就是页面上的一个独立容器，容器里面的子元素不会影响外面元素。

[参与互动](https://github.com/yisainan/web-interview/issues/35)

</details>

<b><details><summary>15. 用纯 CSS 创建一个三角形的原理是什么？ </summary></b>

参考答案：

``` css
span {
    width: 0;
    height: 0;
    border-top: 40px solid transparent;
    border-left: 40px solid transparent;
    border-right: 40px solid transparent;
    border-bottom: 40px solid #ff0000;
}
```

![css_001](../images/css_001.jpg)

[参与互动](https://github.com/yisainan/web-interview/issues/36)

</details>

<b><details><summary>16. Sass、LESS 是什么？大家为什么要使用他们？</summary></b>

参考答案：他们是 CSS 预处理器。他是 CSS 上的一种抽象层。他们是一种特殊的语法/语言编译成 CSS。

例如 Less 是一种动态样式语言. 将 CSS 赋予了动态语言的特性，如变量，继承，运算， 函数. LESS 既可以在客户端上运行 (支持 IE 6+, Webkit, Firefox)，也可一在服务端运行 (借助 Node. js)。

为什么要使用它们？

结构清晰，便于扩展。

可以方便地屏蔽浏览器私有语法差异。这个不用多说，封装对浏览器语法差异的重复处理，减少无意义的机械劳动。

可以轻松实现多重继承。

完全兼容 CSS 代码，可以方便地应用到老项目中。LESS 只是在 CSS 语法上做了扩展，所以老的 CSS 代码也可以与 LESS 代码一同编译。

[参与互动](https://github.com/yisainan/web-interview/issues/37)

</details>

<b><details><summary>17. display:none 与 visibility:hidden 的区别是什么？</summary></b>

参考答案：

display :  隐藏对应的元素但不挤占该元素原来的空间。

visibility:  隐藏对应的元素并且挤占该元素原来的空间。

即是，使用 CSS display:none 属性后，HTML 元素（对象）的宽度、高度等各种属性值都将“丢失”; 而使用 visibility:hidden 属性后，HTML 元素（对象）仅仅是在视觉上看不见（完全透明），而它所占据的空间位置仍然存在。

[参与互动](https://github.com/yisainan/web-interview/issues/38)

</details>

<b><details><summary>18. 移动端 1px 问题的解决办法</summary></b>

参考答案：推荐解决方法：媒体查询 + transfrom

``` 
/* 2倍屏 */
@media only screen and (-webkit-min-device-pixel-ratio: 2.0) {
    .border-bottom::after {
        -webkit-transform: scaleY(0.5);
        transform: scaleY(0.5);
    }
}
/* 3倍屏 */
@media only screen and (-webkit-min-device-pixel-ratio: 3.0) {
    .border-bottom::after {
        -webkit-transform: scaleY(0.33);
        transform: scaleY(0.33);
    }
}
```

[其他解决方案参考](https://www.jianshu.com/p/31f8907637a6)

[参与互动](https://github.com/yisainan/web-interview/issues/39)

</details>

<b><details><summary>19. 哪些 css 属性可以继承？</summary></b>

参考答案：

可继承： font-size font-family color, ul li dl dd dt; 

不可继承 ：border padding margin width height ; 

[参与互动](https://github.com/yisainan/web-interview/issues/40)

</details>

<b><details><summary>20. 几种常见的 CSS 布局</summary></b>

参考答案：

* 单列布局
* 两列自适应布局
* 圣杯布局和双飞翼布局
* 伪等高布局
* 粘连布局

[参与互动](https://github.com/yisainan/web-interview/issues/41)

</details>

<b><details><summary>21. li 与 li 之间有看不见的空白间隔是什么原因引起的？有什么解决办法？</summary></b>

参考答案：浏览器的默认行为是把 inline 元素间的空白字符（空格换行 tab）渲染成一个空格，也就是我们上面的代码<li>换行后会产生换行字符，而它会变成一个空格，当然空格就占用一个字符的宽度。

解决方案：

方法一：既然是因为 `<li>` 换行导致的，那就可以将 `<li>` 代码全部写在一排，如下

``` html
<div class="wrap">
    <h3>li标签空白测试</h3>
    <ul>
        <li class="part1"></li>
        <li class="part2"></li>
        <li class="part3"></li>
        <li class="part4"></li>
    </ul>
</div>
```

方法二：我们为了代码美观以及方便修改，很多时候我们不可能将 `<li>` 全部写在一排，那怎么办？既然是空格占一个字符的宽度，那我们索性就将 `<ul>` 内的字符尺寸直接设为 0，将下面样式放入样式表，问题解决。

``` css
.wrap ul {
    font-size: 0px;
}
```

但随着而来的就是 `<ul>` 中的其他文字就不见了，因为其尺寸被设为 0px 了，我们只好将他们重新设定字符尺寸。
方法三：本来以为方法二能够完全解决问题，但经测试，将 li 父级标签字符设置为 0 在 Safari 浏览器依然出现间隔空白；既然设置字符大小为 0 不行，那咱就将间隔消除了，将下面代码替换方法二的代码，目前测试完美解决。同样随来而来的问题是 li 内的字符间隔也被设置了，我们需要将 li 内的字符间隔设为默认。

``` css
.wrap ul {
    letter-spacing: -5px;
}
```

之后记得设置 li 内字符间隔

``` css
.wrap ul li {
    letter-spacing: normal;
}
```

[参与互动](https://github.com/yisainan/web-interview/issues/90)

</details>

<b><details><summary>22. 设置元素浮动后，该元素的 display 值是多少？</summary></b>

参考答案：

自动变成 display:block

[参与互动](https://github.com/yisainan/web-interview/issues/91)

</details>

<b><details><summary>23. 怎么让 Chrome 支持小于 12px 的文字？</summary></b>

参考答案：

css3 的 transform 属性，设置值为 scale(x, y) 定义 2D 缩放转换

示例：

-webkit-transform: scale(0. 50); 

[参与互动](https://github.com/yisainan/web-interview/issues/92)

</details>

<b><details><summary>24. display:inline-block 什么时候会显示间隙？</summary></b>

参考答案：间隙产生的原因是因为，换行或空格会占据一定的位置

推荐解决方法：

父元素中设置
font-size:0; letter-spaceing:-4px; 

[参与互动](https://github.com/yisainan/web-interview/issues/93)

</details>

<b><details><summary>25.png、jpg、gif 这些图片格式解释一下，分别什么时候用？，webp 呢</summary></b>

参考答案：

gif 图形交换格式，索引颜色格式，颜色少的情况下，产生的文件极小，支持背景透明，动画，图形渐进，无损压缩（适合线条，图标等），缺点只有 256 种颜色

jpg 支持上百万种颜色，有损压缩，压缩比可达 180：1，而且质量受损不明显，不支持图形渐进与背景透明，不支持动画

png 为替代 gif 产生的，位图文件，支持透明，半透明，不透明。不支持动画，无损图像格式。Png8 简单说是静态 gif，也只有 256 色，png24 不透明，但不止 256 色。

webp 谷歌开发的旨在加快图片加载速度的图片格式，图片压缩体积是 jpeg 的 2/3，有损压缩。高版本的 W3C 浏览器才支持，google39+，safari7+

[参与互动](https://github.com/yisainan/web-interview/issues/94)

</details>

<b><details><summary>26. style 标签写在 body 后与 body 前有什么区别？</summary></b>

参考答案：

从上向下加载，加载顺序不同

[参与互动](https://github.com/yisainan/web-interview/issues/95)

</details>

<b><details><summary>27. 超链接访问过后 hover 样式就不出现的问题是什么？如何解决？</summary></b>

参考答案：被点击访问过的超链接样式不在具有 hover 和 active 了, 解决方法是改变 CSS 属性的排列顺序: L-V-H-A（link, visited, hover, active）

[参与互动](https://github.com/yisainan/web-interview/issues/96)

</details>

<b><details><summary>28. 什么是 Css Hack？ie6, 7, 8 的 hack 分别是什么？</summary></b>

参考答案：针对不同的浏览器写不同的 CSS code 的过程，就是 CSS hack。

示例如下：

``` css
#test {
    width: 300px;
    height: 300px;
    background-color: blue;/_firefox_/ background-color: red\9;/_all ie_/ background-color: yellow;/_ie8_/+background-color: pink;/_ie7_/ \_background-color: orange;/_ie6_/
}

:root #test {
    background-color: purple\9;
}

/*ie9*/

@media all and (min-width:0px) {
    #test {
        background-color: black;
    }
}

/*opera*/

@media screen and (-webkit-min-device-pixel-ratio:0) {
    #test {
        background-color: gray;
    }
}

/*chrome and safari*/
```

[参与互动](https://github.com/yisainan/web-interview/issues/97)

</details>

<b><details><summary>29. 重置（resetting）CSS 和 标准化（normalizing）CSS 的区别是什么？你会选择哪种方式，为什么？</summary></b>

参考答案：

* **重置（Resetting）**： 重置意味着除去所有的浏览器默认样式。对于页面所有的元素，像 `margin` 、 `padding` 、 `font-size` 这些样式全部置成一样。你将必须重新定义各种元素的样式。
* **标准化（Normalizing）**： 标准化没有去掉所有的默认样式，而是保留了有用的一部分，同时还纠正了一些常见错误。

当需要实现非常个性化的网页设计时，我会选择重置的方式，因为我要写很多自定义的样式以满足设计需求，这时候就不再需要标准化的默认样式了。

解析：[参考](https://stackoverflow.com/questions/6887336/what-is-the-difference-between-normalize-css-and-reset-css)

[参与互动](https://github.com/yisainan/web-interview/issues/98)

</details>

<b><details><summary>30. css sprite 是什么, 有什么优缺点</summary></b>

参考答案：概念：将多个小图片拼接到一个图片中。通过 background-position 和元素尺寸调节需要显示的背景图案。

优点：

* 减少 HTTP 请求数，极大地提高页面加载速度。
* 增加图片信息重复度，提高压缩比，减少图片大小。
* 更换风格方便，只需在一张或几张图片上修改颜色或样式即可实现。

缺点：

* 图片合并麻烦。
* 维护麻烦，修改一个图片可能需要从新布局整个图片，样式。

[参与互动](https://github.com/yisainan/web-interview/issues/99)

</details>

<b><details><summary>31. 什么是 FOUC? 如何避免</summary></b>

参考答案：

1\. 什么是 Fouc\(文档样式短暂失效\)？

在引用 css 的过程中，如果方法不当或者位置引用不对，会导致某些页面在 windows 下的 ie 出现一些奇怪的现象，以无样式显示页面内容的瞬间闪烁，这种现象称之为文档样式短暂失效，简称 FOCU。

2\. 原因大致为：

* 使用 import 方法导入样式表
* 将样式表放在页面底部
* 有几个样式表，放在 html 结构的不同位置。

3\. 其实原理很清楚：当样式表晚于结构性 html 加载，当加载到此样式表时，页面将停止之前的渲染。此样式表被下载和解析后，将重新渲染页面，也就出现了短暂的花屏现象。

4\. 解决方法：使用 link 标签将样式表放在文档 head 中。

[参与互动](https://github.com/yisainan/web-interview/issues/100)

</details>

<b><details><summary>32. css3 有哪些新特性</summary></b>

参考答案：

1\. 选择器

* E:last-child 匹配父元素的最后一个子元素 E。
* E:nth-child(n)匹配父元素的第 n 个子元素 E。
* E:nth-last-child(n) CSS3 匹配父元素的倒数第 n 个子元素 E。

2\. RGBA

回答此问题，面试官很可能继续问：rgba()和 opacity 的透明效果有什么不同？

3\. 多栏布局

``` html
<div class="mul-col">
    <div>
        <h3>新手上路</h3>
        <p>新手专区 消费警示 交易安全 24小时在线帮助 免费开店</p>
    </div>
    <div>
        <h3>付款方式</h3>
        <p>快捷支付 信用卡 余额宝 蚂蚁花呗 货到付款</p>
    </div>
    <div>
        <h3>淘宝特色</h3>
        <p>手机淘宝 旺信 大众评审 B格指南</p>
    </div>
</div>
```

``` css
.mul-col {
    column-count: 3;
    column-gap: 5px;
    column-rule: 1px solid gray;
    border-radius: 5px;
    border: 1px solid gray;
    padding: 10px;
}
```

4\. 多背景图

``` css
/* backgroundimage:url('1.jpg),url('2.jpg') */
```

5\. CSS3 word-wrap 属性

``` css
p.test {
    word-wrap: break-word;
}
```

6\. 文字阴影

``` css
text-shadow: 5px 2px 6px rgba(64, 64, 64, 0.5);
```

7\. @font-face 属性

Font-face 可以用来加载字体样式，而且它还能够加载服务器端的字体文件，让客户端显示客户端所没有安装的字体。

``` css
@font-face {
    font-family: BorderWeb;
    src: url(BORDERW0.eot);
}

@font-face {
    font-family: Runic;
    src: url(RUNICMT0.eot);
}

.border {
    font-size: 35px;
    color: black;
    font-family: "BorderWeb";
}

.event {
    font-size: 110px;
    color: black;
    font-family: "Runic";
}

/* 淘宝网字体使用 */

@font-face {
    font-family: iconfont;
    src: url(//at.alicdn.com/t/font_1465189805_4518812.eot);
}
```

8\. 圆角

``` css
border-radius: 15px;
```

9\. 边框图片

CSS3 border-image 属性

10. 盒阴影

``` css
/* box-shadow: 水平方向的偏移量 垂直方向的偏移量 模糊程度 扩展程度 颜色 是否具有内阴影 */
```

11. 盒子大小

CSS3 box-sizing 属性

12. 媒体查询

CSS3 @media 查询

13. CSS3 动画

@keyframes

``` css
@keyframes abc {
    from {
        transform: rotate(0);
    }

    50% {
        transform: rotate(90deg);
    }

    to {
        transform: rotate(360deg);
    }
}
```

animation 属性

``` css
/* animation ： name duration timing-function delay interation-count direction play-state */
```

14. 渐变效果

``` css
background-image: -webkit-gradient(linear,
    0% 0%,
    100% 0%,
    from(#2a8bbe),
    to(#fe280e));
```

15. CSS3 弹性盒子模型

* 弹性盒子是 CSS3 的一种新的布局模式。
* CSS3 弹性盒（ Flexible Box 或 flexbox），是一种当页面需要适应不同的屏幕大小以及设备类型时确保元素拥有恰当的行为的布局方式。
* 引入弹性盒布局模型的目的是提供一种更加有效的方式来对一个容器中的子元素进行排列、对齐和分配空白空间。

16. CSS3 过渡

``` css
div {
    transition: width 2s;
    -moz-transition: width 2s;
    /* Firefox 4 */
    -webkit-transition: width 2s;
    /* Safari 和 Chrome */
    -o-transition: width 2s;
    /* Opera */
}
```

17. CSS3 变换

* rotate()旋转
* translate()平移
* scale( )缩放
* skew()扭曲/倾斜
* 变换基点
* 3d 转换

[参考](https://www.w3school.com.cn/css3/index.asp)

[参与互动](https://github.com/yisainan/web-interview/issues/101)

</details>

<b><details><summary>33. display 有哪些值？说明他们的作用</summary></b>

参考答案：

display： none | inline | block | list-item | inline-block | table | inline-table | table-caption | table-cell | table-row | table-row-group | table-column | table-column-group | table-footer-group | table-header-group | run-in | box | inline-box | flexbox | inline-flexbox | flex | inline-flex

解析：

默认值：inline

``` 
none： 隐藏对象。与visibility属性的hidden值不同，其不为被隐藏的对象保留其物理空间
inline： 指定对象为内联元素。
block： 指定对象为块元素。
list-item： 指定对象为列表项目。
inline-block： 指定对象为内联块元素。（CSS2）
table： 指定对象作为块元素级的表格。类同于html标签<table>（CSS2）
inline-table： 指定对象作为内联元素级的表格。类同于html标签<table>（CSS2）
table-caption： 指定对象作为表格标题。类同于html标签<caption>（CSS2）
table-cell： 指定对象作为表格单元格。类同于html标签<td>（CSS2）
table-row： 指定对象作为表格行。类同于html标签<tr>（CSS2）
table-row-group： 指定对象作为表格行组。类同于html标签<tbody>（CSS2）
table-column： 指定对象作为表格列。类同于html标签<col>（CSS2）
table-column-group： 指定对象作为表格列组显示。类同于html标签<colgroup>（CSS2）
table-header-group： 指定对象作为表格标题组。类同于html标签<thead>（CSS2）
table-footer-group： 指定对象作为表格脚注组。类同于html标签<tfoot>（CSS2）
run-in： 根据上下文决定对象是内联对象还是块级对象。（CSS3）
box： 将对象作为弹性伸缩盒显示。（伸缩盒最老版本）（CSS3）
inline-box： 将对象作为内联块级弹性伸缩盒显示。（伸缩盒最老版本）（CSS3）
flexbox： 将对象作为弹性伸缩盒显示。（伸缩盒过渡版本）（CSS3）
inline-flexbox： 将对象作为内联块级弹性伸缩盒显示。（伸缩盒过渡版本）（CSS3）
flex： 将对象作为弹性伸缩盒显示。（伸缩盒最新版本）（CSS3）
inline-flex： 将对象作为内联块级弹性伸缩盒显示。（伸缩盒最新版本）（CSS3）
```

[参考](https://www.jianshu.com/p/77e1c36c0895)

[参与互动](https://github.com/yisainan/web-interview/issues/102)

</details>

<b><details><summary>34. display:inline-block 什么时候不会显示间隙？(携程)</summary></b>

参考答案：inline-block 布局的元素在编辑器里写在同一行

[参与互动](https://github.com/yisainan/web-interview/issues/103)

</details>

<b><details><summary>35. PNG, GIF, JPG 的区别及如何选</summary></b>

参考答案：

GIF：

* 1：256 色
* 2： 无损，编辑 保存时候，不会损失。
* 3：支持简单动画。
* 4：支持 boolean 透明，也就是要么完全透明，要么不透明

JPEG：

* 1：millions of colors
* 2： 有损压缩， 意味着每次编辑都会失去质量。
* 3：不支持透明。
* 4：适合照片，实际上很多相机使用的都是这个格式。

PNG：

* 1：无损，其实 PNG 有好几种格式的，一般分为两类：PNG8 和 truecolor PNGs；

* 与 GIF 相比：

  + 它通常会产生较小的文件大小。
  + 它支持阿尔法（变量）透明度。
  + 无动画支持

* 与 JPEG 相比：

  + 文件更大
  + 无损
  + 因此可以作为 JPEG 图片中间编辑的中转格式。

* 结论：

  + JPEG 适合照片
  + GIF 适合动画
  + PNG 适合其他任何种类——图表，buttons，背景，图表等等。

[参考](https://www.cnblogs.com/yadiblogs/p/9546935.html)

[参与互动](https://github.com/yisainan/web-interview/issues/104)

</details>

<b><details><summary>36. 行内元素 float:left 后是否变为块级元素？</summary></b>

参考答案：

* 行内元素设置成浮动之后变得更加像是 inline-block
* 行内块级元素，设置成这个属性的元素会同时拥有行内和块级的特性，最明显的不同是它的默认宽度不是 100%，行内元素默认 100%宽度占据一行
* 这时候给行内元素设置 padding-top 和 padding-bottom 或者 width、height 都是有效果的

[参与互动](https://github.com/yisainan/web-interview/issues/105)

</details>

<b><details><summary>37. 在网页中的应该使用奇数还是偶数的字体？为什么呢？</summary></b>

参考答案：应该使用偶数字体

1\. 比例关系

相对来说偶数字号比较容易和页面中其他部分的字号构成一个比例关系。如我使用 14px 的字体作为正文字号，那么其他部分的字体（如标题）就可以使用 14×1. 5 =21px 的字体，或者在一些地方使用到了 14×0. 5=7px 的 padding 或者 margin，如果你是在用 sass 或者 less 编写 css，这时候用处就凸显出来了。

2\. UI 设计师的缘故

大多数设计师用的软件如 ps 提供的字号是偶数，自然到了   前端那边也是用的是偶数。

3\. 浏览器缘故

其一是低版本的浏览器 ie6 会把奇数字体强制转化为偶数，即 13px 渲染为 14px。

其二是为了平分字体。偶数宽的汉字，如 12px 的汉子，去掉 1 像素的字体间距，填充了的字体像素宽度其实就是 11px，这样的汉字中竖线左右是平分的，如“中”子，左右就是 5px 了。

4\. 系统差别

Windows 自带的点阵宋体（中易宋体）从 Vista 开始只提供 12、14、16 px 这三个大小的点阵，而 13、15、17 px 时用的是小一号的点阵（即每个字占的空间大了 1 px，但点阵没变），于是略显稀疏。

而在 Linux 和其他手持设备上，奇数偶数的渲染效果其实相差不大。

解析：[参考](https://blog.csdn.net/jian_xi/article/details/79346477)

[参与互动](https://github.com/yisainan/web-interview/issues/106)

</details>

<b><details><summary>38. CSS 合并方法</summary></b>

参考答案：@import url(css 文件地址)

[参与互动](https://github.com/yisainan/web-interview/issues/107)

</details>

<b><details><summary>39. 列出你所知道可以改变页面布局的属性</summary></b>

参考答案：width、height、float、position、等

[参与互动](https://github.com/yisainan/web-interview/issues/108)

</details>

<b><details><summary>40. CSS 在性能优化方面的实践</summary></b>

参考答案：

1\. 内联首屏关键 CSS（Critical CSS）

内联 CSS 能够使浏览器开始页面渲染的时间提前，只将渲染首屏内容所需的关键 CSS 内联到 HTML 中

2\. 异步加载 CSS

3\. 文件压缩

4\. 去除无用 CSS

解析：[参考](https://www.cnblogs.com/heroljy/p/9412704.html)

[参与互动](https://github.com/yisainan/web-interview/issues/109)

</details>

<b><details><summary>41. CSS3 动画（简单动画的实现，如旋转等）</summary></b>

参考答案：

让一个 div 元素旋转 360 度示例

1\. div 的样式结构:

``` css
div {
    margin: 50px auto;
    width: 200px;
    height: 200px;
    background-color: pink;
}
```

2\. 设置旋转属性的类名:

``` css
div.rotate {
    /* 旋转360度 */
    transform: rotate(360deg);
    /* all表示所有属性,1s表示在一秒的时间完成动画 */
    transition: all 1s;
}
```

``` 
transition 有四个属性:

property: 规定应用过渡的 CSS 属性的名称。

duration: 定义过渡效果花费的时间。默认是 0,单位是 s。

timing-function: 规定过渡效果的时间曲线。默认是 "ease"。匀速'linear',加速'ease-in',减速'ease-out',先快后慢'ease-in-out'。

delay: 规定过渡效果何时开始。默认是 0。单位 s。

可以连写: transition: property duration timing-function delay;
```

3\. 给 div 元素设置鼠标移入时旋转, 也就是给它加上\. rotate 类名\. 鼠标移出时移除类名

``` js
$(function() {
    $("div")
        .mouseenter(function() {
            $(this).addClass("rotate");
        })
        .mouseleave(function() {
            $(this).removeClass("rotate");
        });
});
```

解析：[参考](https://blog.csdn.net/qq_42209630/article/details/80338578)

[参与互动](https://github.com/yisainan/web-interview/issues/110)

</details>

<b><details><summary>42. base64 的原理及优缺点</summary></b>

参考答案：

1\. 什么是 Base64

Base64 是一种基于 64 个可打印字符来表示二进制数据的编码方式，是从二进制数据到字符的过程。
原则上，计算机中所有内容都是二进制形式存储的，所以所有内容（包括文本、影音、图片等）都可以用 base64 来表示。

2\. 适用场景

``` 
1.Base64一般用于在HTTP协议下传输二进制数据，由于HTTP协议是文本协议，所以在HTTP写一下传输二进制数据需要将二进制数据转化为字符数据，
网络传输只能传输可打印字符，
在ASCII码中规定，0-31、128这33个字符属于控制字符，
32~127这95个字符属于可打印字符
那么其它字符怎么传输呢，Base64就是其中一种方式，
2.将图片等资源文件以Base64编码形式直接放于代码中，使用的时候反Base64后转换成Image对象使用。
3.偶尔需要用这条纯文本通道传一张图片之类的情况发生的时候，就会用到Base64，比如多功能Internet 邮件扩充服务（MIME）就是用Base64对邮件的附件进行编码的。
```

3\. Base64 编码原理

Base64 编码之所以称为 Base64，是因为其使用 64 个字符来对任意数据进行编码，同理有 Base32、Base16 编码。标准 Base64 编码使用的 64 个字符为：

![css_008](../images/css_008.png)

有点特殊的是最后两个字符，因对最后两个字符的选择不同，Base64 编码又有很多变种，比如用于编码 URL 的 Base64 URL 编码。

Base64 编码本质上是一种将二进制数据转成文本数据的方案。对于非二进制数据，是先将其转换成二进制形式，然后每连续 6 比特（2 的 6 次方=64）计算其十进制值，根据该值在上面的索引表中找到对应的字符，最终得到一个文本字符串。

假设我们要对 Hello! 进行 Base64 编码，按照 ASCII 表，其转换过程如下图所示：

![css_009](../images/css_009.png)

可知 Hello! 的 Base64 编码结果为 SGVsbG8h，每 3 个原始字符经 Base64 编码成 4 个字符。那么，当原始字符串长度不能被 3 整除时，怎么办呢？

以 Hello!! 为例，其转换过程为：

![css_010](../images/css_010.png)

Hello!! Base64 编码的结果为 SGVsbG8hIQAA。可见，不能被 3 整除时会采用来来补 0 的方式来完成编码。
需要注意的是：标准 Base64 编码通常用 = 字符来替换最后的 A，即编码结果为 SGVsbG8hIQ==。因为 = 字符并不在 Base64 编码索引表中，其意义在于结束符号，在 Base64 解码时遇到 = 时即可知道一个 Base64 编码字符串结束。

4\. 优缺点

优点: 可以将二进制数据转化为可打印字符，方便传输数据，对数据进行简单的加密，肉眼安全。
缺点：内容编码后体积变大，编码和解码需要额外工作量。

解析：[参考 1](https://segmentfault.com/a/1190000012654771)、[参考 2](https://blog.csdn.net/fightingitpanda/article/details/83305100)

[参与互动](https://github.com/yisainan/web-interview/issues/111)

</details>

<b><details><summary>43. stylus/sass/less 区别</summary></b>

参考答案：

1\. 后缀

默认 Sass 使用 . sass 扩展名，而 Less 使用 . less 扩展名，Stylus 默认使用 . styl 的文件扩展名

2\. 语法

3\. 变量

* sass 变量必须是以\$开头的，然后变量和值之间使用冒号（：）隔开，和 css 属性是一样的
* Less css 中变量都是用@开头的，其余与 sass 都是一样的
* stylus 对变量是没有任何设定的，可以是以\$开头，或者任何的字符，而且与变量之间可以用冒号，空格隔开，但是在 stylus 中不能用@开头

解析：[参考](https://blog.csdn.net/pedrojuliet/article/details/72887490)

[参与互动](https://github.com/yisainan/web-interview/issues/112)

</details>

<b><details><summary>44. position 的值， relative 和 absolute 分别是相对于谁进行定位的？</summary></b>

参考答案：

* absolute : 生成绝对定位的元素， 相对于最近一级的 定位不是 static 的父元素来进行定位。
* fixed （老 IE 不支持）生成绝对定位的元素，通常相对于浏览器窗口或 frame 进行定位。
* relative 生成相对定位的元素，相对于其在普通流中的位置进行定位。
* static 默认值。没有定位，元素出现在正常的流中
* sticky 生成粘性定位的元素，容器的位置根据正常文档流计算得出

[参与互动](https://github.com/yisainan/web-interview/issues/113)

</details>

<b><details><summary>45. 对偏移、卷曲、可视的理解</summary></b>

参考答案：

``` 
偏移
offsetWidth	  width  +  padding  +  border
offsetHeight	height +  padding  +  border
offsetLeft
offsetTop
offsetParent
注意：没有offsetRight和offsetBottom
************************************************************************************************

卷曲
scrollWidth    width  +  padding
scrollHeight   当内部的内容溢出盒子的时候， 顶边框的底部，计算到内容的底部；如果内容没有溢出盒子，计算方式为盒子内部的真实高度（边框到边框）
scrollLeft     这个scroll系列属性不是只读的
scrollTop
scroll()

此函数可以获取卷曲的高度和卷曲的宽度
function myScroll() {
   return {
      top: window.pageYOffset  || document.documentElement.scrollTop  || document.body.scrollTop  || 0,
      left: window.pageXOffset || document.documentElement.scrollLeft || document.body.scrollLeft || 0
    };

}

滚动滚动条的时候触发事件
box（window）.onscroll = function () {}
************************************************************************************************

可视
clientWidth   获取的是元素内部的真实宽度 width  +  padding
clientHeight  边框之间的高度
clientLeft    相当于左边框的宽度  如果元素包含了滚动条，并且滚动条显示在元素的左侧。这时，clientLeft属性会包含滚动条的宽度17px
clientTop     相当于顶边框的宽度
client()

此函数可以获取浏览器可视区域的宽高
function myClient() {
    return {
        wid: window.innerWidth  || document.documentElement.clientWidth  || document.body.clientWidth  || 0,
       heit: window.innerHeight || document.documentElement.clientHeight || document.body.clientHeight || 0
    };
}

----------------------------------------------------------------------------------------------
@offsetHeight和style.height的区别

demo.style.height只能获取行内样式，如果样式写到了其他地方，甚至根本就没写，便无法获取
style.height是字符串（而且带单位），offsetHeight是数值
demo.style.height可以设置行内样式，offsetHeight是只读属性
因此，一般用demo.offsetHeight来获取某元素的真实宽度/高度，用style.height来设置宽度/高度

----------------------------------------------------------------------------------------------
@offsetLeft和style.left的区别

一、style.left只能获取行内样式
二、offsetLeft只读，style.left可读可写
三、offsetLeft是数值，style.left是字符串并且有单位px
四、如果没有加定位，style.left获取的数值可能是无效的
五、最大区别在于offsetLeft以border左上角为基准，style.left以margin左上角为基准

----------------------------------------------------------------------------------------------
@scrollHeight和scrollWidth

标签内部实际内容的高度/宽度
不计算边框，如果内容不超出盒子，值为盒子的宽高（不带边框）
如果内容超出了盒子，就是从顶部或左部边框内侧一直到内容a的最外部分

----------------------------------------------------------------------------------------------
@scrollTop和scrollLeft

被卷去部分的 顶部/左侧 到可视区域 顶部/左侧 的距离
```

解析：

![offset大全](../images/css_002.png)

![scroll大全](../images/css_003.png)

![三个height比较](../images/css_004.png)

![style. left和offsetLeft](../images/css_005.png)

![client大全](../images/css_006.png)

[参与互动](https://github.com/yisainan/web-interview/issues/114)

</details>

<b><details><summary>46. 精灵图和 base64 如何选择？</summary></b>

参考答案：

## Css Sprites：

介绍：
Css Sprites（雪碧图或 css 精灵），是网页图片处理的一种方式，它允许你将一个页面涉及到的所有零星图片都包含到一张大图中去，这样一来，当访问该页面时，载入的图片就不会像以前那样一幅一幅地慢慢显示出来了。

原理：
将许多的小图片整合到一张大图片中，利用 css 中的 background-image 属性，background-position 属性定位某个图片位置，来达到在大图片中引用某个部位的小图片的效果。

优点：
减少网页的 http 请求，提升网页加载速度。
合并多张小图片成大图，能减少字节总数（大图大小<=多张小图大小）. 

缺点：
前期需要处理图片将小图合并，多些许工程量。
对于需要经常改变的图片维护起来麻烦。

## base64：

介绍：
base64 是网络上最常见的用于传输 8Bit 字节代码的编码方式之一，要求把每三个 8Bit 的字节转换为四个 6Bit 的字节，Base64 是网络上最常见的用于传输 8Bit 字节代码的编码方式之一。

通俗点讲：将资源原本二进制形式转成以 64 个字符基本单位，所组成的一串字符串。
比如一张图片转成 base64 编码后就像这样，图片直接以 base64 形式嵌入文件中（很长没截完）：

![css_007](../images/css_007.jpg)

生成 base64 编码：
图片生成 base64 可以用一些工具，如在线工具，但在项目中这样一个图片这样生成是挺繁琐。
特别说下，webpack 中的 url-loader 可以完成这个工作，可以对限制大小的图片进行 base64 的转换，非常方便。

优点：
base64 的图片会随着 html 或者 css 一起下载到浏览器, 减少了请求. 
可避免跨域问题

缺点：
老东西（低版本）的 IE 浏览器不兼容。
体积会比原来的图片大一点。
css 中过多使用 base64 图片会使得 css 过大，不利于 css 的加载。

适用场景：
应用于小的图片几 k 的，太大的图片会转换后的大小太大，得不偿失。
用于一些 css sprites 不利处理的小图片，如一些可以通过 background-repeat 平铺来做成背景的图片

解析：[参考](https://www.cnblogs.com/wangqi2019/p/10498627.html)

[参与互动](https://github.com/yisainan/web-interview/issues/115)

</details>

<b><details><summary>47. 如果设计中使用了非标准的字体，你该如何去实现？</summary></b>

参考答案：使用 `@font-face` 并为不同的 `font-weight` 定义 `font-family` 。

[参与互动](https://github.com/yisainan/web-interview/issues/116)

</details>

<b><details><summary>48. 知道 css 有个 content 属性吗？有什么作用？有什么应用？</summary></b>

参考答案：知道。css 的 content 属性专门应用在 before/after 伪元素上，用来插入生成内容。最常见的应用是利用伪类清除浮动。

``` css
//一种常见利用伪类清除浮动的代码
.clearfix:after {
    content: "."; //这里利用到了content属性
    display: block;
    height: 0;
    visibility: hidden;
    clear: both;
}

.clearfix {
    zoom: 1;
}
```

after 伪元素通过 content 在元素的后面生成了内容为一个点的块级素，再利用 clear:both 清除浮动。
那么问题继续还有，知道 css 计数器（序列数字字符自动递增）吗？如何通过 css content 属性实现 css 计数器？

参考答案：css 计数器是通过设置 counter-reset 、counter-increment 两个属性 、及 counter()/counters()一个方法配合 after / before 伪类实现。

[参与互动](https://github.com/yisainan/web-interview/issues/117)

</details>

<b><details><summary>49. CSS 选择器的优先级是如何计算的？</summary></b>

参考答案：浏览器通过优先级规则，判断元素展示哪些样式。优先级通过 4 个维度指标确定，我们假定以 `a、b、c、d` 命名，分别代表以下含义：

1\. `a` 表示是否使用内联样式（inline style）。如果使用， `a` 为 1，否则为 0。
2\. `b` 表示 ID 选择器的数量。
3\. `c` 表示类选择器、属性选择器和伪类选择器数量之和。
4\. `d` 表示标签（类型）选择器和伪元素选择器之和。

优先级的结果并非通过以上四个值生成一个得分，而是每个值分开比较。 `a、b、c、d` 权重从左到右，依次减小。判断优先级时，从左到右，一一比较，直到比较出最大值，即可停止。所以，如果 `b` 的值不同，那么 `c` 和 `d` 不管多大，都不会对结果产生影响。比如 `0，1，0，0` 的优先级高于 `0，0，10，10` 。

当出现优先级相等的情况时，最晚出现的样式规则会被采纳。如果你在样式表里写了相同的规则（无论是在该文件内部还是其它样式文件中），那么最后出现的（在文件底部的）样式优先级更高，因此会被采纳。

在写样式时，我会使用较低的优先级，这样这些样式可以轻易地覆盖掉。尤其对写 UI 组件的时候更为重要，这样使用者就不需要通过非常复杂的优先级规则或使用 `!important` 的方式，去覆盖组件的样式了。

解析：[参考](https://www.smashingmagazine.com/2007/07/css-specificity-things-you-should-know/)、[参考](https://www.sitepoint.com/web-foundations/specificity/)

[参与互动](https://github.com/yisainan/web-interview/issues/118)

</details>

<b><details><summary>50. 请阐述 `Float` 定位的工作原理。</summary></b>

参考答案：

浮动（float）是 CSS 定位属性。浮动元素从网页的正常流动中移出，但是保持了部分的流动性，会影响其他元素的定位（比如文字会围绕着浮动元素）。这一点与绝对定位不同，绝对定位的元素完全从文档流中脱离。

CSS 的 `clear` 属性通过使用 `left` 、 `right` 、 `both` ，让该元素向下移动（清除浮动）到浮动元素下面。

如果父元素只包含浮动元素，那么该父元素的高度将塌缩为 0。我们可以通过清除（clear）从浮动元素后到父元素关闭前之间的浮动来修复这个问题。

有一种 hack 的方法，是自定义一个 `.clearfix` 类，利用伪元素选择器 `::after` 清除浮动。[另外还有一些方法](https://css-tricks.com/all-about-floats/#article-header-id-4)，比如添加空的 `<div></div>` 和设置浮动元素父元素的 `overflow` 属性。与这些方法不同的是， `clearfix` 方法，只需要给父元素添加一个类，定义如下：

``` css
.clearfix::after {
    content: "";
    display: block;
    clear: both;
}
```

值得一提的是，把父元素属性设置为 `overflow: auto` 或 `overflow: hidden` ，会使其内部的子元素形成块格式化上下文（Block Formatting Context），并且父元素会扩张自己，使其能够包围它的子元素。

解析：[参考](https://css-tricks.com/all-about-floats/)

[参与互动](https://github.com/yisainan/web-interview/issues/119)

</details>

<b><details><summary>51. 请阐述 `z-index` 属性，并说明如何形成层叠上下文（stacking context）</summary></b>

参考答案：

CSS 中的 `z-index` 属性控制重叠元素的垂直叠加顺序。 `z-index` 只能影响 `position` 值不是 `static` 的元素。

没有定义 `z-index` 的值时，元素按照它们出现在 DOM 中的顺序堆叠（层级越低，出现位置越靠上）。非静态定位的元素（及其子元素）将始终覆盖静态定位（static）的元素，而不管 HTML 层次结构如何。

层叠上下文是包含一组图层的元素。 在一组层叠上下文中，其子元素的 `z-index` 值是相对于该父元素而不是 document root 设置的。每个层叠上下文完全独立于它的兄弟元素。如果元素 B 位于元素 A 之上，则即使元素 A 的子元素 C 具有比元素 B 更高的 `z-index` 值，元素 C 也永远不会在元素 B 之上. 

每个层叠上下文是自包含的：当元素的内容发生层叠后，整个该元素将会在父层叠上下文中按顺序进行层叠。少数 CSS 属性会触发一个新的层叠上下文，例如 `opacity` 小于 1， `filter` 不是 `none` ， `transform` 不是 `none` 。

解析：[参考 1](https://css-tricks.com/almanac/properties/z/z-index/)、[参考 2](https://philipwalton.com/articles/what-no-one-told-you-about-z-index/)、[参考 3](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Positioning/Understanding_z_index/The_stacking_context)

[参与互动](https://github.com/yisainan/web-interview/issues/120)

</details>

<b><details><summary>52. 如何解决不同浏览器的样式兼容性问题？</summary></b>

参考答案：

* 在确定问题原因和有问题的浏览器后，使用单独的样式表，仅供出现问题的浏览器加载。这种方法需要使用服务器端渲染。
* 使用已经处理好此类问题的库，比如 Bootstrap。
* 使用 `autoprefixer` 自动生成 CSS 属性前缀。
* 使用 Reset CSS 或 Normalize. css。

[参与互动](https://github.com/yisainan/web-interview/issues/121)

</details>

<b><details><summary>53. 如何为功能受限的浏览器提供页面？ 使用什么样的技术和流程？</summary></b>

参考答案：

* 优雅的降级：为现代浏览器构建应用，同时确保它在旧版浏览器中正常运行。
* Progressivepx enhancement - The practice of building an application for a base level of user experience, but adding functional enhancements when a browser supports it. 
* 渐进式增强：构建基于用户体验的应用，但在浏览器支持时添加新增功能。
* 利用 [caniuse. com](https://caniuse.com/) 检查特性支持。
* 使用 `autoprefixer` 自动生成 CSS 属性前缀。
* 使用 [Modernizr](https://modernizr.com/)进行特性检测。

[参与互动](https://github.com/yisainan/web-interview/issues/122)

</details>

<b><details><summary>54. 有什么不同的方式可以隐藏内容（使其仅适用于屏幕阅读器）？</summary></b>

参考答案：

这些方法与可访问性（a11y）有关。

* `visibility: hidden` ：元素仍然在页面流中，并占用空间。
* `width: 0; height: 0` ：使元素不占用屏幕上的任何空间，导致不显示它。
* `position: absolute; left: -99999px` ： 将它置于屏幕之外。
* `text-indent: -9999px` ：这只适用于 `block` 元素中的文本。
* Metadata： 例如通过使用 Schema. org，RDF 和 JSON-LD。
* WAI-ARIA：如何增加网页可访问性的 W3C 技术规范。

即使 WAI-ARIA 是理想的解决方案，我也会采用绝对定位方法，因为它具有最少的注意事项，适用于大多数元素，而且使用起来非常简单。

解析：[参考 1](https://www.w3.org/TR/wai-aria-1.1/)、[参考 2](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA)、[参考 3](http://a11yproject.com/)

[参与互动](https://github.com/yisainan/web-interview/issues/123)

</details>

<b><details><summary>55. 除了 `screen` ，你还能说出一个 @media 属性的例子吗？</summary></b>

参考答案：

* all

  适用于所有设备。

* print

  为了加载合适的文档到当前使用的可视窗口. 需要提前咨询 paged media（媒体屏幕尺寸）, 以满足个别设备网页尺寸不匹配等问题。

* screen

  主要适用于彩色的电脑屏幕

* speech

  speech 这个合成器. 注意: CSS2 已经有一个相似的媒体类型叫 aural. <br>

解析：[参考](https://developer.mozilla.org/zh-CN/docs/Web/CSS/@media)

[参与互动](https://github.com/yisainan/web-interview/issues/124)

</details>

<b><details><summary>56. 编写高效的 CSS 应该注意什么？</summary></b>

参考答案：

首先，浏览器从最右边的选择器，即关键选择器（key selector），向左依次匹配。根据关键选择器，浏览器从 DOM 中筛选出元素，然后向上遍历被选元素的父元素，判断是否匹配。选择器匹配语句链越短，浏览器的匹配速度越快。避免使用标签和通用选择器作为关键选择器，因为它们会匹配大量的元素，浏览器必须要进行大量的工作，去判断这些元素的父元素们是否匹配。

[BEM (Block Element Modifier)](https://bem.info/) methodology recommends that everything has a single class, and, where you need hierarchy, that gets baked into the name of the class as well, this naturally makes the selector efficient and easy to override. 
[BEM (Block Element Modifier)](https://bem.info/)原则上建议为独立的 CSS 类命名，并且在需要层级关系时，将关系也体现在命名中，这自然会使选择器高效且易于覆盖。

搞清楚哪些 CSS 属性会触发重新布局（reflow）、重绘（repaint）和合成（compositing）。在写样式时，避免触发重新布局的可能。

解析：[参考 1](https://developers.google.com/web/fundamentals/performance/rendering/)、[参考 2](https://csstriggers.com/)

[参与互动](https://github.com/yisainan/web-interview/issues/125)

</details>

<b><details><summary>57. 使用 CSS 预处理的优缺点分别是什么？</summary></b>

参考答案：

优点：

* 提高 CSS 可维护性。
* 易于编写嵌套选择器。
* 引入变量，增添主题功能。可以在不同的项目中共享主题文件。
* 通过混合（Mixins）生成重复的 CSS。
* Splitting your code into multiple files. CSS files can be split up too but doing so will require a HTTP request to download each CSS file. 
* 将代码分割成多个文件。不进行预处理的 CSS，虽然也可以分割成多个文件，但需要建立多个 HTTP 请求加载这些文件。

缺点：

* 需要预处理工具。
* 重新编译的时间可能会很慢。

[参与互动](https://github.com/yisainan/web-interview/issues/126)

</details>

<b><details><summary>58. 对于你使用过的 CSS 预处理，说说喜欢和不喜欢的地方？</summary></b>

参考答案：

喜欢：

* 绝大部分优点上题以及提过。
* Less 用 JavaScript 实现，与 NodeJS 高度结合。

不喜欢：

* 我通过 `node-sass` 使用 Sass，它用 C ++ 编写的 LibSass 绑定。在 Node 版本切换时，我必须经常重新编译。
* Less 中，变量名称以 `@` 作为前缀，容易与 CSS 关键字混淆，如 `@media` 、 `@import` 和 `@font-face` 。

[参与互动](https://github.com/yisainan/web-interview/issues/127)

</details>

<b><details><summary>59. 解释浏览器如何确定哪些元素与 CSS 选择器匹配。</summary></b>

参考答案：

浏览器从最右边的选择器（关键选择器）根据关键选择器，浏览器从 DOM 中筛选出元素，然后向上遍历被选元素的父元素，判断是否匹配。选择器匹配语句链越短，浏览器的匹配速度越快。

例如，对于形如 `p span` 的选择器，浏览器首先找到所有 `<span>` 元素，并遍历它的父元素直到根元素以找到 `<p>` 元素。对于特定的 `<span>` ，只要找到一个 `<p>` ，就知道'<span>`已经匹配并停止继续匹配。

解析：[参考](https://stackoverflow.com/questions/5797014/why-do-browsers-match-css-selectors-from-right-to-left)

[参与互动](https://github.com/yisainan/web-interview/issues/128)

</details>

<b><details><summary>60. 说说你对盒模型的理解，以及如何告知浏览器使用不同的盒模型渲染布局。</summary></b>

参考答案：

CSS 盒模型描述了以文档树中的元素而生成的矩形框，并根据排版模式进行布局。每个盒子都有一个内容区域（例如文本，图像等）以及周围可选的 `padding` 、 `border` 和 `margin` 区域。

CSS 盒模型负责计算：

* 块级元素占用多少空间。
* 边框是否重叠，边距是否合并。
* 盒子的尺寸。

盒模型有以下规则：

* 块级元素的大小由 `width` 、 `height` 、 `padding` 、 `border` 和 `margin` 决定。
* 如果没有指定 `height` ，则块级元素的高度等于其包含子元素的内容高度加上 `padding` （除非有浮动元素，请参阅下文）。
* 如果没有指定 `width` ，则非浮动块级元素的宽度等于其父元素的宽度减去父元素的 `padding` 。
* 元素的 `height` 是由内容的 `height` 来计算的。
* 元素的 `width` 是由内容的 `width` 来计算的。
* 默认情况下， `padding` 和 `border` 不是元素 `width` 和 `height` 的组成部分。

解析：[参考](https://www.smashingmagazine.com/2010/06/the-principles-of-cross-browser-css-coding/#understand-the-css-box-model)

[参与互动](https://github.com/yisainan/web-interview/issues/129)

</details>

<b><details><summary>61. `* { box-sizing: border-box; }` 会产生怎样的效果？</summary></b>

参考答案：

* 元素默认应用了 `box-sizing: content-box` ，元素的宽高只会决定内容（content）的大小。
* `box-sizing: border-box` 改变计算元素 `width` 和 `height` 的方式， `border` 和 `padding` 的大小也将计算在内。
* 元素的 `height` = 内容（content）的高度 + 垂直方向的 `padding` + 垂直方向 `border` 的宽度
* 元素的 `width` = 内容（content）的宽度 + 水平方向的 `padding` + 水平方向 `border` 的宽度

[参与互动](https://github.com/yisainan/web-interview/issues/130)

</details>

<b><details><summary>62. `relative` 、 `fixed` 、 `absolute` 和 `static` 四种定位有什么区别？</summary></b>

参考答案：

经过定位的元素，其 `position` 属性值必然是 `relative` 、 `absolute` 、 `fixed` 或 `static` 。

* `static` ：默认定位属性值。该关键字指定元素使用正常的布局行为，即元素在文档常规流中当前的布局位置。此时 top, right, bottom, left 和 z-index 属性无效。
* `relative` ：该关键字下，元素先放置在未添加定位时的位置，再在不改变页面布局的前提下调整元素位置（因此会在此元素未添加定位时所在位置留下空白）。
* `absolute` ：不为元素预留空间，通过指定元素相对于最近的非 static 定位祖先元素的偏移，来确定元素位置。绝对定位的元素可以设置外边距（margins），且不会与其他边距合并。
* `fixed` ：不为元素预留空间，而是通过指定元素相对于屏幕视口（viewport）的位置来指定元素位置。元素的位置在屏幕滚动时不会改变。打印时，元素会出现在的每页的固定位置。fixed 属性会创建新的层叠上下文。当元素祖先的 transform 属性非 none 时，容器由视口改为该祖先。
* `static` ：盒位置根据正常流计算(这称为正常流动中的位置)，然后相对于该元素在流中的 flow root（BFC）和 containing block（最近的块级祖先元素）定位。在所有情况下（即便被定位元素为 `table` 时），该元素定位均不对后续元素造成影响。当元素 B 被粘性定位时，后续元素的位置仍按照 B 未定位时的位置来确定。 `position: static` 对 `table` 元素的效果与 `position: relative` 相同。

解析：[参考](https://developer.mozilla.org/en/docs/Web/CSS/position)

[参与互动](https://github.com/yisainan/web-interview/issues/131)

</details>

<b><details><summary>63. 你使用过哪些现有的 CSS 框架？你是如何改进它们的？</summary></b>

参考答案：

* **Bootstrap**： 更新周期缓慢。Bootstrap 4 已经处于 alpha 版本将近两年了。添加了在页面中广泛使用的微调按钮组件。
* **Semantic UI**：源代码结构使得自定义主题很难理解。非常规主题系统的使用体验很差。外部库的路径需要硬编码（hard code）配置。变量重新赋值没有 Bootstrap 设计得好。
* **Bulma**： 需要很多非语义的类和标记，显得很多余。不向后兼容，以至于升级版本后，会破坏应用的正常运行。

[参与互动](https://github.com/yisainan/web-interview/issues/132)

</details>

<b><details><summary>64. 你了解 CSS Flex 和 Grid 吗？</summary></b>

参考答案：Flex 主要用于一维布局，而 Grid 则用于二维布局。

解析：

### Flex

flex 容器中存在两条轴， 横轴和纵轴， 容器中的每个单元称为 flex item。

在容器上可以设置 6 个属性：

* flex-direction
* flex-wrap
* flex-flow
* justify-content
* align-items
* align-content

注意：当设置 flex 布局之后，子元素的 float、clear、vertical-align 的属性将会失效。

#### Flex 项目属性

有六种属性可运用在 item 项目上:

1\. order
2\. flex-basis
3\. flex-grow
4\. flex-shrink
5\. flex
6\. align-self

### Grid

CSS 网格布局用于将页面分割成数个主要区域，或者用来定义组件内部元素间大小、位置和图层之间的关系。

像表格一样，网格布局让我们能够按行或列来对齐元素。 但是，使用 CSS 网格可能还是比 CSS 表格更容易布局。 例如，网格容器的子元素可以自己定位，以便它们像 CSS 定位的元素一样，真正的有重叠和层次。

[参与互动](https://github.com/yisainan/web-interview/issues/133)

</details>

<b><details><summary>65. 响应式设计与自适应设计有何不同？</summary></b>

参考答案：

响应式设计和自适应设计都以提高不同设备间的用户体验为目标，根据视窗大小、分辨率、使用环境和控制方式等参数进行优化调整。

响应式设计的适应性原则：网站应该凭借一份代码，在各种设备上都有良好的显示和使用效果。响应式网站通过使用媒体查询，自适应栅格和响应式图片，基于多种因素进行变化，创造出优良的用户体验。就像一个球通过膨胀和收缩，来适应不同大小的篮圈。

自适应设计更像是渐进式增强的现代解释。与响应式设计单一地去适配不同，自适应设计通过检测设备和其他特征，从早已定义好的一系列视窗大小和其他特性中，选出最恰当的功能和布局。与使用一个球去穿过各种的篮筐不同，自适应设计允许使用多个球，然后根据不同的篮筐大小，去选择最合适的一个。

解析：[参考 1](https://developer.mozilla.org/en-US/docs/Archive/Apps/Design/UI_layout_basics/Responsive_design_versus_adaptive_design)、[参考 2](http://mediumwell.com/responsive-adaptive-mobile/)、[参考 3](https://css-tricks.com/the-difference-between-responsive-and-adaptive-design/)

[参与互动](https://github.com/yisainan/web-interview/issues/134)

</details>

<b><details><summary>66. 你有没有使用过视网膜分辨率的图形？当中使用什么技术？</summary></b>

参考答案：我倾向于使用更高分辨率的图形（显示尺寸的两倍）来处理视网膜显示。更好的方法是使用媒体查询，像 `@media only screen and (min-device-pixel-ratio: 2) { ... }` ，然后改变 `background-image` 。

对于图标类的图形，我会尽可能使用 svg 和图标字体，因为它们在任何分辨率下，都能被渲染得十分清晰。

还有一种方法是，在检查了 `window.devicePixelRatio` 的值后，利用 JavaScript 将 `<img>` 的 `src` 属性修改，用更高分辨率的版本进行替换。

解析：[参考](https://www.sitepoint.com/css-techniques-for-retina-displays/)

[参与互动](https://github.com/yisainan/web-interview/issues/135)

</details>

<b><details><summary>67. 什么情况下，用 `translate()` 而不用绝对定位？什么时候，情况相反。</summary></b>

参考答案： `translate()` 是 `transform` 的一个值。改变 `transform` 或 `opacity` 不会触发浏览器重新布局（reflow）或重绘（repaint），只会触发复合（compositions）。而改变绝对定位会触发重新布局，进而触发重绘和复合。 `transform` 使浏览器为元素创建一个 GPU 图层，但改变绝对定位会使用到 CPU。 因此 `translate()` 更高效，可以缩短平滑动画的绘制时间。

当使用 `translate()` 时，元素仍然占据其原始空间（有点像 `position：relative` ），这与改变绝对定位不同。

解析：[参考 1](https://www.paulirish.com/2012/why-moving-elements-with-translate-is-better-than-posabs-topleft/)、[参考 2](https://neal.codes/blog/front-end-interview-css-questions)、[参考 3](https://quizlet.com/28293152/front-end-interview-questions-css-flash-cards/)、[参考 4](http://peterdoes.it/2015/12/03/a-personal-exercise-front-end-job-interview-questions-and-my-answers-all/)

[参与互动](https://github.com/yisainan/web-interview/issues/136)

</details>

<b><details><summary>68. 一边固定宽度一边宽度自适应</summary></b>

参考答案：可以使用 flex 布局 复制下面的 HTML 和 CSS 代码 用浏览器打开可以看到效果

``` html
<div class="wrap">
    <div class="div1"></div>
    <div class="div2"></div>
</div>
```

``` css
.wrap {
    display: flex;
    justify-content: space-between;
}

.div1 {
    min-width: 200px;
}

.div2 {
    width: 100%;
    background: #e6e6e6;
}

html,
body,
div {
    height: 100%;
    margin: 0;
}
```

[参与互动](https://github.com/yisainan/web-interview/issues/137)

</details>

<b><details><summary>69. display:none、visibile:hidden、opacity:0 的区别</summary></b>

参考答案：

|                  | 是否隐藏 | 是否在文档中占用空间 | 是否会触发事件 |
| ---------------- | -------- | -------------------- | -------------- |
| display: none    | 是       | 否                   | 否             |
| visibile: hidden | 是       | 是                   | 否             |
| opacity: 0       | 是       | 是                   | 是             |

[参与互动](https://github.com/yisainan/web-interview/issues/138)

</details>

<b><details><summary>70. 文本超出部分显示省略号</summary></b>

参考答案：

#### 单行

``` css
overflow: hidden;
text-overflow: ellipsis;
white-space: nowrap;
```

#### 多行

``` css
display: -webkit-box;
-webkit-box-orient: vertical;
-webkit-line-clamp: 3; // 最多显示几行
overflow: hidden;
```

[参与互动](https://github.com/yisainan/web-interview/issues/139)

</details>

<b><details><summary>71. 利用伪元素画三角</summary></b>

参考答案：

``` css
.info-tab {
    position: relative;
}

.info-tab::after {
    content: "";
    border: 4px solid transparent;
    border-top-color: #2c8ac2;
    position: absolute;
    top: 0;
}
```

[参与互动](https://github.com/yisainan/web-interview/issues/140)

</details>

<b><details><summary>72. 过渡与动画的区别是什么</summary></b>

参考答案：

* transition

  可以在一定的时间内实现元素的状态过渡为最终状态，用于模拟以一种过渡动画效果，但是功能有限，只能用于制作简单的动画效果而动画属性

* animation

  可以制作类似 Flash 动画，通过关键帧控制动画的每一步，控制更为精确，从而可以制作更为复杂的动画。

[参与互动](https://github.com/yisainan/web-interview/issues/141)

</details>

<b><details><summary>73. 去除 inline-block 元素间间距的方法</summary></b>

参考答案：

* 移除空格
* 使用 margin 负值
* 使用 font-size:0
* letter-spacing
* word-spacing

解析：更详细的介绍请看[去除 inline-block 元素间间距的 N 种方法](https://www.zhangxinxu.com/wordpress/2012/04/inline-block-space-remove-%E5%8E%BB%E9%99%A4%E9%97%B4%E8%B7%9D/)

[参与互动](https://github.com/yisainan/web-interview/issues/142)

</details>

<b><details><summary>74. 为什么要初始化 CSS 样式</summary></b>

参考答案：

* 因为浏览器的兼容问题，不同浏览器对有些标签的默认值是不同的，如果没对 CSS 初始化往往会出现浏览器之间的页面显示差异。
* 去掉标签的默认样式如：margin, padding，其他浏览器默认解析字体大小，字体设置。

[参与互动](https://github.com/yisainan/web-interview/issues/143)

</details>

<b><details><summary>75. 行内元素和块级元素有哪些</summary></b>

参考答案：

### 行内元素

一个行内元素只占据它对应标签的边框所包含的空间<br>
一般情况下，行内元素只能包含数据和其他行内元素

``` 
b, big, i, small, tt
abbr, acronym, cite, code, dfn, em, kbd, strong, samp, var
a, bdo, br, img, map, object, q, script, span, sub, sup
button, input, label, select, textarea
```

### 块级元素

占据一整行，高度、行高、内边距和外边距都可以改变，可以容纳块级标签和其他行内标签<br>

``` 
header,form,ul,ol,table,article,div,hr,aside,figure,canvas,video,audio,footer
```

[参与互动](https://github.com/yisainan/web-interview/issues/144)

</details>

<b><details><summary>76. 设备像素比</summary></b>

参考答案：

[参与互动](https://github.com/yisainan/web-interview/issues/145)

</details>

<b><details><summary>77. ::bofore 和 :after 中双冒号和单冒号有什么区别？</summary></b>

参考答案：

[参与互动](https://github.com/yisainan/web-interview/issues/146)

</details>

<b><details><summary>78. 说下 CSS3 中一些样式的兼容，分别指兼容哪些浏览器</summary></b>

参考答案：

[参与互动](https://github.com/yisainan/web-interview/issues/147)

</details>

<b><details><summary>79. 有哪些手段可以优化 CSS, 提高性能</summary></b>

参考答案：

1, 首推的是合并css文件，如果页面加载10个css文件，每个文件1k，那么也要比只加载一个100k的css文件慢。

2，减少css嵌套，最好不要套三层以上。

3，不要在ID选择器前面进行嵌套，ID本来就是唯一的而且人家权值那么大，嵌套完全是浪费性能。

4，建立公共样式类，把相同样式提取出来作为公共类使用，比如我们常用的清除浮动等。

5，减少通配符*或者类似[hidden="true"]这类选择器的使用，挨个查找所有... 这性能能好吗？当然重置样式这些必须 的东西是不能少的。

6，巧妙运用css的继承机制，如果父节点定义了，子节点就无需定义。

7，拆分出公共css文件，对于比较大的项目我们可以将大部分页面的公共结构的样式提取出来放到单独css文件里， 这样一次下载后就放到缓存里，当然这种做法会增加请求，具体做法应以实际情况而定。

8，不用css表达式，表达式只是让你的代码显得更加炫酷，但是他对性能的浪费可能是超乎你的想象的。

9，少用css rest，可能你会觉得重置样式是规范，但是其实其中有很多的操作是不必要不友好的，有需求有兴趣的 朋友可以选择normolize. css

10，cssSprite，合成所有icon图片，用宽高加上bacgroud-position的背景图方式显现出我们要的icon图，这是一种 十分实用的技巧，极大减少了http请求。

11，当然我们还需要一些善后工作，CSS压缩(这里提供一个在线压缩 YUI Compressor ，当然你会用其他工具来压缩是十 分好的)，

12，GZIP压缩，Gzip是一种流行的文件压缩算法，详细做法可以谷歌或者百度。

[参与互动](https://github.com/yisainan/web-interview/issues/148)

</details>

<b><details><summary>80. 怎么样实现边框 0. 5 个像素？</summary></b>

参考答案：

[参与互动](https://github.com/yisainan/web-interview/issues/149)

</details>

<b><details><summary>81. transform translate transition 的区别</summary></b>

参考答案：

[参与互动](https://github.com/yisainan/web-interview/issues/150)

</details>

<b><details><summary>82. 请解释一下 CSS3 的 Flexbox（弹性盒布局模型）, 以及适用场景？</summary></b>

参考答案：

[参与互动](https://github.com/yisainan/web-interview/issues/151)

</details>

<b><details><summary>83. 用纯 CSS 创建一个三角形的原理是什么？</summary></b>

参考答案：

[参与互动](https://github.com/yisainan/web-interview/issues/152)

</details>

<b><details><summary>84. 一个满屏 品 字布局 如何设计?</summary></b>

参考答案：

[参与互动](https://github.com/yisainan/web-interview/issues/153)

</details>

<b><details><summary>85. 全屏滚动的原理是什么？用到了 CSS 的那些属性？</summary></b>

参考答案：

[参与互动](https://github.com/yisainan/web-interview/issues/154)

</details>

<b><details><summary>86. 什么是响应式设计？响应式设计的基本原理是什么？如何兼容低版本的 IE？</summary></b>

参考答案：

[参与互动](https://github.com/yisainan/web-interview/issues/155)

</details>

<b><details><summary>87. 如何修改 chrome 记住密码后自动填充表单的黄色背景？</summary></b>

参考答案：

[参与互动](https://github.com/yisainan/web-interview/issues/156)

</details>

<b><details><summary>88. 用 css 分别实现某个 div 元素上下居中和左右居中</summary></b>

参考答案：

[参与互动](https://github.com/yisainan/web-interview/issues/157)

</details>

<b><details><summary>89. 你对 line-height 是如何理解的？</summary></b>

参考答案：

[参与互动](https://github.com/yisainan/web-interview/issues/158)

</details>

<b><details><summary>90. 让页面里的字体变清晰，变细用 CSS 怎么做？</summary></b>

参考答案：

-webkit-font-smoothing: antialiased; 

[参与互动](https://github.com/yisainan/web-interview/issues/159)

</details>

<b><details><summary>91. font-style 属性可以让它赋值为“oblique” oblique 是什么意思？</summary></b>

参考答案：Italic是使用文字的斜体,Oblique是让没有斜体属性的文字倾斜

[参与互动](https://github.com/yisainan/web-interview/issues/160)

</details>

<b><details><summary>92 . position:fixed; 在 android 下无效怎么处理？</summary></b>

参考答案：

[参与互动](https://github.com/yisainan/web-interview/issues/161)

</details>

<b><details><summary>93. 如果需要手动写动画，你认为最小时间间隔是多久，为什么？</summary></b>

参考答案：16.7ms。多数显示器默认频率是60Hz，即1秒刷新60次，所以理论上最小间隔为1/60*1000ms ＝ 16.7ms

[参与互动](https://github.com/yisainan/web-interview/issues/162)

</details>

<b><details><summary>94. overflow: scroll 时不能平滑滚动的问题怎么处理？</summary></b>

参考答案：

[参与互动](https://github.com/yisainan/web-interview/issues/163)

</details>

<b><details><summary>95. 有一个高度自适应的 div，里面有两个 div，一个高度 100px，希望另一个填满剩下的高度。</summary></b>

参考答案：

[参与互动](https://github.com/yisainan/web-interview/issues/164)

</details>

<b><details><summary>96. postcss 的作用</summary></b>

参考答案：

[参与互动](https://github.com/yisainan/web-interview/issues/165)

</details>

<b><details><summary>97. 自定义字体的使用场景</summary></b>

参考答案：

[参与互动](https://github.com/yisainan/web-interview/issues/166)

</details>

<b><details><summary>98. 如何美化 CheckBox</summary></b>

参考答案：

[参与互动](https://github.com/yisainan/web-interview/issues/167)

</details>

<b><details><summary>99. float 和 display:inline-block 的区别是什么？</summary></b>

参考答案：对元素设置display：inline-block ，元素不会脱离文本流，而float就会使得元素脱离文本流，且还有父元素高度坍塌的效果。

[参与互动](https://github.com/yisainan/web-interview/issues/168)

</details>

<b><details><summary>100. rem 布局字体太大怎么处理?</summary></b>

参考答案：getComputedStyle方法能够获取到计算后的样式、大小。

最后优化完的代码如下。

``` js
(function(doc, win) {

    var isAndroid = win.navigator.appVersion.match(/android/gi);
    var isIPhone = win.navigator.appVersion.match(/iphone/gi);

    var scale = 1.0;
    var ratio = 1;
    if (isIPhone) {
        if (window.devicePixelRatio == 2) {
            scale *= 0.5;
            ratio *= 2;
        }
        if (window.devicePixelRatio == 3) {
            scale *= (1 / 3);
            ratio *= 3;
        }
    }
    var text = '<meta name="viewport" content="initial-scale=' + scale + ', maximum-scale=' + scale + ',' + ' minimum-scale=' + scale + ', width=device-width,' + ' user-scalable=no" />';
    document.write(text);

    var docEl = doc.documentElement
    var resizeEvt = 'orientationchange' in window ? 'orientationchange' : 'resize'
    var recalc = function() {
        var clientWidth = docEl.clientWidth
        if (!clientWidth) return
        docEl.style.fontSize = 100 * (clientWidth / 750) + 'px'

        // 解决部分rem特别大的问题
        var docElFontSize = docEl.style.fontSize.replace(/px/gi, '')
        var computedFontSize = win.getComputedStyle(docEl)['font-size'].replace(/px/gi, '')
        docElFontSize != computedFontSize && (docEl.style.fontSize = docElFontSize * docElFontSize / computedFontSize + 'px')
    }
    if (!doc.addEventListener) return
    recalc()
    win.addEventListener(resizeEvt, recalc, false)
})(document, window);
```

[参与互动](https://github.com/yisainan/web-interview/issues/169)

</details>

<b><details><summary>101. 标准模式与怪异模式的区别</summary></b>

参考答案：浏览器解析 CSS 的两种模式：标准模式(strict mode)和怪异模式(quirks mode)

标准模式：浏览器按 W3C 标准解析执行代码；

怪异模式：使用浏览器自己的方式解析执行代码，因为不同浏览器解析执行的方式不一样，所以称之为怪异模式。

浏览器解析时使用标准模式还是怪异模式，与网页中的 DTD 声明直接相关，DTD 声明定义了标准文档的类型（标准模式解析）文档类型，会使浏览器使用相关的方式加载网页并显示，忽略 DTD 声明，将使网页进入怪异模式（quirks mode）。

区别是：

1、盒模型：

在怪异模式下，盒模型为 IE 模型

![html_001.jpg](../../images/html_001.jpg)

而在 W3C 标准的盒模型中为：

![html_002.jpg](../../images/html_002.jpg)

2、图片元素的垂直对齐方式

对于 inline 元素和 table-cell 元素，标准模式下 vertical-align 属性默认取值是 baseline；在怪异模式下，table 单元格中的图片的 vertical-align 属性默认取值是 bottom。因此在图片底部会有及像素的空间。

3、 `<table>` 元素中的字体
CSS 中，对于 font 的属性都是可以继承的。怪异模式下，对于 table 元素，字体的某些元素将不会从 body 等其他封装元素继承中的得到，特别是 font-size 属性。

4、内联元素的尺寸

* 标准模式下，non-replaced inline 元素无法自定义大写；
* 怪异模式下，定义这些元素的 width、height 属性可以影响这些元素显示的尺寸。

5、元素的百分比高度

* CSS 中对于元素的百分比高度规定：百分比为元素包含块的高度，不可为负值；如果包含块的高度没有显示给出，该值等同于 auto，所以百分比的高度必须是在元素有高度声明的情况下使用。
* 当一个元素使用百分比高度是，标准模式下，高度取决于内容变化，怪异模式下，百分比高度被准确应用

6、元素溢出的处理

标准模式下，overflow 取值默认为 visible；在怪异模式在，该溢出会被当做扩展 box 来对待，即元素的大小由内容决定，溢出不会裁剪，元素框自动调整，包含溢出内容。

</details>

<b><details><summary>102. css reset 与 css sprites</summary></b>

参考答案：

css reset ：重置浏览器默认属性

css sprites ：由多个小图片组成的大图，减少服务器对图片的请求数

</details>

<b><details><summary>103. IE6 遇到什么 bug？解决办法是？</summary></b>

参考答案：

一、IE6 双倍边距 bug

当页面上的元素使用 float 浮动时，不管是向左还是向右浮动; 只要该元素带有 margin 像素都会使该值乘以 2，例如“margin-left:10px” 在 IE6 中，该值就会被解析为 20px。想要解决这个 BUG 就需要在该元素中加入 display:inline 或 display:block 明确其元素类型即可解决双倍边距的 BUG

二、IE6 中 3 像素问题及解决办法

当元素使用 float 浮动后，元素与相邻的元素之间会产生 3px 的间隙。诡异的是如果右侧的容器没设置高度时 3px 的间隙在相邻容器的内部，当设定高度后又跑到容器的相反侧了。要解决这类 BUG 的话，需要使布局在同一行的元素都加上 float 浮动。

三、IE6 中奇数宽高的 BUG

IE6 中奇数的高宽显示大小与偶数高宽显示大小存在一定的不同。其中要问题是出在奇数高宽上。要解决此类问题，只需要尽量将外部定位的 div 高宽写成偶数即可。

四、IE6 中图片链接的下方有间隙

IE6 中图片的下方会存在一定的间隙，尤其在图片垂直挨着图片的时候，即可看到这样的间隙。要解决此类问题，需要将 img 标签定义为 display:block 或定义 vertical-align 对应的属性。也可以为 img 对应的样式写入 font-size:0

五、IE6 下空元素的高度 BUG

如果一个元素中没有任何内容，当在样式中为这个元素设置了 0-19px 之间的高度时。此元素的高度始终为 19px。

解决的方法有四种:

1\. 在元素的 css 中加入：overflow:hidden

2\. 在元素中插入 html 注释：

3\. 在元素中插入 html 的空白符：

4\. 在元素的 css 中加入：font-size:0

六、重复文字的 BUG

在某些比较复杂的排版中，有时候浮动元素的最后一些字符会出现在 clear 清除元素的下面。

解决方法如下：

1\. 确保元素都带有 display:inline

2\. 在最后一个元素上使用“margin-right:-3px

3\. 为浮动元素的最后一个条目加上条件注释，xxx

4\. 在容器的最后元素使用一个空白的 div，为这个 div 指定不超过容器的宽度。

七、IE6 中 z-index 失效

具体 BUG 为，元素的父级元素设置的 z-index 为 1，那么其子级元素再设置 z-index 时会失效，其层级会继承父级元素的设置，造成某些层级调整上的 BUG。

写在最后：实际上 IE6 中，很多 BUG 的解决方法都可以使用 display:inline、font-size:0、float 解决。因此我们在书写代码时要记住，一旦使用了 float 浮动，就为元素增加一个 display:inline 样式，可以有效的避免浮动造成的样式错乱问题。使用空 DIV 时，为了避免其高度影响布局美观，也可以为其加上 font-size:0 这样就很容易避免一些兼容上的问题。

解析：[参考](https://www.cnblogs.com/rightzhao/p/3474162.html)

</details>

<b><details><summary>104. 介绍css3中position:sticky（网易）</summary></b>

参考答案：position:sticky是一个新的css3属性，它的表现类似position:relative和position:fixed的合体，在目标区域在屏幕中可见时，它的行为就像position:relative; 而当页面滚动超出目标区域时，它的表现就像position:fixed，它会固定在目标位置。

</details>

<b><details><summary>105. 使用css实现一个持续的动画效果</summary></b>

参考答案：

``` css
animation:mymove 5s infinite;

@keyframes mymove {
    from {
        top: 0px;
    }

    to {
        top: 200px;
    }
}
```

</details>



<b><details><summary>106.CSS 优先级算法如何计算？</summary></b>

参考答案：

相关知识点：

```
CSS的优先级是根据样式声明的特殊性值来判断的。

选择器的特殊性值分为四个等级，如下：

（1）标签内选择符x,0,0,0
（2）ID选择符0,x,0,0
（3）class选择符/属性选择符/伪类选择符	0,0,x,0
（4）元素和伪元素选择符0,0,0,x

计算方法：

（1）每个等级的初始值为0
（2）每个等级的叠加为选择器出现的次数相加
（3）不可进位，比如0,99,99,99
（4）依次表示为：0,0,0,0
（5）每个等级计数之间没关联
（6）等级判断从左向右，如果某一位数值相同，则判断下一位数值
（7）如果两个优先级相同，则最后出现的优先级高，!important也适用
（8）通配符选择器的特殊性值为：0,0,0,0
（9）继承样式优先级最低，通配符样式优先级高于继承样式
（10）!important（权重），它没有特殊性值，但它的优先级是最高的，为了方便记忆，可以认为它的特殊性值为1,0,0,0,0。

计算实例：

（1）#demo a{color: orange;}/*特殊性值：0,1,0,1*/
（2）div#demo a{color: red;}/*特殊性值：0,1,0,2*/


注意：
（1）样式应用时，css会先查看规则的权重（!important），加了权重的优先级最高，当权重相同的时候，会比较规则的特殊性。

（2）特殊性值越大的声明优先级越高。

（3）相同特殊性值的声明，根据样式引入的顺序，后声明的规则优先级高（距离元素出现最近的）

 (4) 部分浏览器由于字节溢出问题出现的进位表现不做考虑
```

回答：

```
判断优先级时，首先我们会判断一条属性声明是否有权重，也就是是否在声明后面加上了!important。一条声明如果加上了权重，
那么它的优先级就是最高的，前提是它之后不再出现相同权重的声明。如果权重相同，我们则需要去比较匹配规则的特殊性。

一条匹配规则一般由多个选择器组成，一条规则的特殊性由组成它的选择器的特殊性累加而成。选择器的特殊性可以分为四个等级，
第一个等级是行内样式，为1000，第二个等级是id选择器，为0100，第三个等级是类选择器、伪类选择器和属性选择器，为0010，
第四个等级是元素选择器和伪元素选择器，为0001。规则中每出现一个选择器，就将它的特殊性进行叠加，这个叠加只限于对应的等
级的叠加，不会产生进位。选择器特殊性值的比较是从左向右排序的，也就是说以1开头的特殊性值比所有以0开头的特殊性值要大。
比如说特殊性值为1000的的规则优先级就要比特殊性值为0999的规则高。如果两个规则的特殊性值相等的时候，那么就会根据它们引
入的顺序，后出现的规则的优先级最高。
```

对于组合声明的特殊性值计算可以参考：
[《CSS 优先级计算及应用》](https://www.jianshu.com/p/1c4e639ff7d5)
[《CSS 优先级计算规则》](http://www.cnblogs.com/wangmeijian/p/4207433.html)
[《有趣：256 个 class 选择器可以干掉 1 个 id 选择器》](https://www.zhangxinxu.com/wordpress/2012/08/256-class-selector-beat-id-selector/)

</details>

<b><details><summary>107.关于伪类 LVHA 的解释?</summary></b>

参考答案：

```
a标签有四种状态：链接访问前、链接访问后、鼠标滑过、激活，分别对应四种伪类:link、:visited、:hover、:active；

当链接未访问过时：

（1）当鼠标滑过a链接时，满足:link和:hover两种状态，要改变a标签的颜色，就必须将:hover伪类在:link伪
类后面声明；
（2）当鼠标点击激活a链接时，同时满足:link、:hover、:active三种状态，要显示a标签激活时的样式（:active），
必须将:active声明放到:link和:hover之后。因此得出LVHA这个顺序。

当链接访问过时，情况基本同上，只不过需要将:link换成:visited。

这个顺序能不能变？可以，但也只有:link和:visited可以交换位置，因为一个链接要么访问过要么没访问过，不可能同时满足，
也就不存在覆盖的问题。
```

</details>

<b><details><summary>108.CSS3 新增伪类有那些？</summary></b>

参考答案：

```
（1）elem:nth-child(n)选中父元素下的第n个子元素，并且这个子元素的标签名为elem，n可以接受具体的数
值，也可以接受函数。

（2）elem:nth-last-child(n)作用同上，不过是从后开始查找。

（3）elem:last-child选中最后一个子元素。

（4）elem:only-child如果elem是父元素下唯一的子元素，则选中之。

（5）elem:nth-of-type(n)选中父元素下第n个elem类型元素，n可以接受具体的数值，也可以接受函数。

（6）elem:first-of-type选中父元素下第一个elem类型元素。

（7）elem:last-of-type选中父元素下最后一个elem类型元素。

（8）elem:only-of-type如果父元素下的子元素只有一个elem类型元素，则选中该元素。

（9）elem:empty选中不包含子元素和内容的elem类型元素。

（10）elem:target选择当前活动的elem元素。

（11）:not(elem)选择非elem元素的每个元素。

（12）:enabled 控制表单控件的禁用状态。

（13）:disabled	控制表单控件的禁用状态。

(14):checked单选框或复选框被选中。

```

详细的资料可以参考：
[《CSS3 新特性总结(伪类)》](https://www.cnblogs.com/SKLthegoodman/p/css3.html)
[《浅谈 CSS 伪类和伪元素及 CSS3 新增伪类》](https://blog.csdn.net/zhouziyu2011/article/details/58605705)

</details>

<b><details><summary>109.如何居中 div？</summary></b>

参考答案：

-水平居中：给 div 设置一个宽度，然后添加 margin:0 auto 属性

```css
div {
  width: 200px;
  margin: 0 auto;
}
```

-水平居中，利用 text-align:center 实现

```css
.container {
  background: rgba(0, 0, 0, 0.5);
  text-align: center;
  font-size: 0;
}

.box {
  display: inline-block;
  width: 500px;
  height: 400px;
  background-color: pink;
}
```

-让绝对定位的 div 居中

```css
div {
  position: absolute;
  width: 300px;
  height: 300px;
  margin: auto;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  background-color: pink; /*方便看效果*/
}
```

-水平垂直居中一

```css
/*确定容器的宽高宽500高300的层设置层的外边距div{*/
position: absolute;/*绝对定位*/
width: 500px;
height: 300px;
top: 50%;
left: 50%;
margin: -150px00-250px;/*外边距为自身宽高的一半*/
background-color: pink;/*方便看效果*/
}
```

-水平垂直居中二

```css
/*未知容器的宽高，利用`transform`属性*/
div {
  position: absolute; /*相对定位或绝对定位均可*/
  width: 500px;
  height: 300px;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background-color: pink; /*方便看效果*/
}
```

-水平垂直居中三

```css
/*利用flex布局实际使用时应考虑兼容性*/
.container {
  display: flex;
  align-items: center; /*垂直居中*/
  justify-content: center; /*水平居中*/
}
.containerdiv {
  width: 100px;
  height: 100px;
  background-color: pink; /*方便看效果*/
}
```

-水平垂直居中四

```css
/*利用text-align:center和vertical-align:middle属性*/
.container {
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  background: rgba(0, 0, 0, 0.5);
  text-align: center;
  font-size: 0;
  white-space: nowrap;
  overflow: auto;
}

.container::after {
  content: '';
  display: inline-block;
  height: 100%;
  vertical-align: middle;
}

.box {
  display: inline-block;
  width: 500px;
  height: 400px;
  background-color: pink;
  white-space: normal;
  vertical-align: middle;
}
```

回答：

```
一般常见的几种居中的方法有：

对于宽高固定的元素

（1）我们可以利用margin:0 auto来实现元素的水平居中。

（2）利用绝对定位，设置四个方向的值都为0，并将margin设置为auto，由于宽高固定，因此对应方向实现平分，可以实现水
平和垂直方向上的居中。

（3）利用绝对定位，先将元素的左上角通过top:50%和left:50%定位到页面的中心，然后再通过margin负值来调整元素
的中心点到页面的中心。

（4）利用绝对定位，先将元素的左上角通过top:50%和left:50%定位到页面的中心，然后再通过translate来调整元素
的中心点到页面的中心。

（5）使用flex布局，通过align-items:center和justify-content:center设置容器的垂直和水平方向上为居中对
齐，然后它的子元素也可以实现垂直和水平的居中。

对于宽高不定的元素，上面的后面两种方法，可以实现元素的垂直和水平的居中。
```

</details>

<b><details><summary>110.display 有哪些值？说明他们的作用。</summary></b>

参考答案：

```
block	块类型。默认宽度为父元素宽度，可设置宽高，换行显示。
none	元素不显示，并从文档流中移除。
inline	行内元素类型。默认宽度为内容宽度，不可设置宽高，同行显示。
inline-block 默认宽度为内容宽度，可以设置宽高，同行显示。
list-item	像块类型元素一样显示，并添加样式列表标记。
table	此元素会作为块级表格来显示。
inherit	规定应该从父元素继承display属性的值。
```

详细资料可以参考：
[《CSS display 属性》](http://www.w3school.com.cn/css/pr_class_display.asp)

</details>

<b><details><summary>111.position 的值 relative 和 absolute 定位原点是？</summary></b>

参考答案：

相关知识点：

```
absolute
生成绝对定位的元素，相对于值不为static的第一个父元素的padding box进行定位，也可以理解为离自己这一级元素最近的
一级position设置为absolute或者relative的父元素的padding box的左上角为原点的。

fixed（老IE不支持）
生成绝对定位的元素，相对于浏览器窗口进行定位。

relative
生成相对定位的元素，相对于其元素本身所在正常位置进行定位。

static
默认值。没有定位，元素出现在正常的流中（忽略top,bottom,left,right,z-index声明）。

inherit
规定从父元素继承position属性的值。
```

回答：

```
relative定位的元素，是相对于元素本身的正常位置来进行定位的。

absolute定位的元素，是相对于它的第一个position值不为static的祖先元素的padding box来进行定位的。这句话
我们可以这样来理解，我们首先需要找到绝对定位元素的一个position的值不为static的祖先元素，然后相对于这个祖先元
素的padding box来定位，也就是说在计算定位距离的时候，padding的值也要算进去。
```

</details>

<b><details><summary>112.CSS3 有哪些新特性？（根据项目回答）</summary></b>

参考答案：

```
新增各种CSS选择器	（:not(.input)：所有class不是“input”的节点）
圆角		（border-radius:8px）
多列布局	（multi-column layout）
阴影和反射	（Shadow\Reflect）
文字特效		（text-shadow）
文字渲染		（Text-decoration）
线性渐变		（gradient）
旋转			（transform）
缩放，定位，倾斜，动画，多背景
例如：transform:\scale(0.85,0.90)\translate(0px,-30px)\skew(-9deg,0deg)\Animation:
```

</details>

<b><details><summary>113.请解释一下 CSS3 的 Flex box（弹性盒布局模型），以及适用场景？</summary></b>

参考答案：

相关知识点：

```
Flex是FlexibleBox的缩写，意为"弹性布局"，用来为盒状模型提供最大的灵活性。

任何一个容器都可以指定为Flex布局。行内元素也可以使用Flex布局。注意，设为Flex布局以后，子元素的float、cl
ear和vertical-align属性将失效。

采用Flex布局的元素，称为Flex容器（flex container），简称"容器"。它的所有子元素自动成为容器成员，称为Flex
项目（flex item），简称"项目"。

容器默认存在两根轴：水平的主轴（main axis）和垂直的交叉轴（cross axis），项目默认沿主轴排列。


以下6个属性设置在容器上。

flex-direction属性决定主轴的方向（即项目的排列方向）。

flex-wrap属性定义，如果一条轴线排不下，如何换行。

flex-flow属性是flex-direction属性和flex-wrap属性的简写形式，默认值为row nowrap。

justify-content属性定义了项目在主轴上的对齐方式。

align-items属性定义项目在交叉轴上如何对齐。

align-content属性定义了多根轴线的对齐方式。如果项目只有一根轴线，该属性不起作用。


以下6个属性设置在项目上。

order属性定义项目的排列顺序。数值越小，排列越靠前，默认为0。

flex-grow属性定义项目的放大比例，默认为0，即如果存在剩余空间，也不放大。

flex-shrink属性定义了项目的缩小比例，默认为1，即如果空间不足，该项目将缩小。

flex-basis属性定义了在分配多余空间之前，项目占据的主轴空间。浏览器根据这个属性，计算主轴是否有多余空间。它的默认
值为auto，即项目的本来大小。

flex属性是flex-grow，flex-shrink和flex-basis的简写，默认值为0 1 auto。

align-self属性允许单个项目有与其他项目不一样的对齐方式，可覆盖align-items属性。默认值为auto，表示继承父
元素的align-items属性，如果没有父元素，则等同于stretch。
```

回答：

```
flex布局是CSS3新增的一种布局方式，我们可以通过将一个元素的display属性值设置为flex从而使它成为一个flex
容器，它的所有子元素都会成为它的项目。

一个容器默认有两条轴，一个是水平的主轴，一个是与主轴垂直的交叉轴。我们可以使用flex-direction来指定主轴的方向。
我们可以使用justify-content来指定元素在主轴上的排列方式，使用align-items来指定元素在交叉轴上的排列方式。还
可以使用flex-wrap来规定当一行排列不下时的换行方式。

对于容器中的项目，我们可以使用order属性来指定项目的排列顺序，还可以使用flex-grow来指定当排列空间有剩余的时候，
项目的放大比例。还可以使用flex-shrink来指定当排列空间不足时，项目的缩小比例。
```

详细资料可以参考：
[《Flex 布局教程：语法篇》](http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html)
[《Flex 布局教程：实例篇》](http://www.ruanyifeng.com/blog/2015/07/flex-examples.html)

</details>

<b><details><summary>114.用纯 CSS 创建一个三角形的原理是什么？</summary></b>

参考答案：

```css
采用的是相邻边框连接处的均分原理。
  将元素的宽高设为0，只设置
  border
  ，把任意三条边隐藏掉（颜色设为
  transparent），剩下的就是一个三角形。
  #demo {
  width: 0;
  height: 0;
  border-width: 20px;
  border-style: solid;
  border-color: transparent transparent red transparent;
}
```

</details>

<b><details><summary>115.一个满屏品字布局如何设计?</summary></b>

参考答案：

```
简单的方式：
	上面的div宽100%，
	下面的两个div分别宽50%，
	然后用float或者inline使其不换行即可
```

</details>

<b><details><summary>116.CSS 多列等高如何实现？</summary></b>

参考答案：

```
（1）利用padding-bottom|margin-bottom正负值相抵，不会影响页面布局的特点。设置父容器设置超出隐藏（overflow:
hidden），这样父容器的高度就还是它里面的列没有设定padding-bottom时的高度，当它里面的任一列高度增加了，则
父容器的高度被撑到里面最高那列的高度，其他比这列矮的列会用它们的padding-bottom补偿这部分高度差。

（2）利用table-cell所有单元格高度都相等的特性，来实现多列等高。

（3）利用flex布局中项目align-items属性默认为stretch，如果项目未设置高度或设为auto，将占满整个容器的高度
的特性，来实现多列等高。

```

详细资料可以参考：
[《前端应该掌握的 CSS 实现多列等高布局》](https://juejin.im/post/5b0fb34151882515662238fd)
[《CSS：多列等高布局》](https://codepen.io/yangbo5207/post/equh)

</details>

<b><details><summary>117.经常遇到的浏览器的兼容性有哪些？原因，解决方法是什么，常用 hack 的技巧？</summary></b>

参考答案：

```
（1）png24位的图片在iE6浏览器上出现背景
解决方案：做成PNG8，也可以引用一段脚本处理。

（2）浏览器默认的margin和padding不同
解决方案：加一个全局的*{margin:0;padding:0;}来统一。

（3）IE6双边距bug：在IE6下，如果对元素设置了浮动，同时又设置了margin-left或
margin-right，margin值会加倍。

#box{float:left;width:10px;margin:0 0 0 10px;}

这种情况之下IE会产生20px的距离
解决方案：在float的标签样式控制中加入_display:inline;将其转化为行内属性。(_这个符号只有ie6会识别)

（4）渐进识别的方式，从总体中逐渐排除局部。
首先，巧妙的使用"\9"这一标记，将IE游览器从所有情况中分离出来。
接着，再次使用"+"将IE8和IE7、IE6分离开来，这样IE8已经独立识别。
.bb{
background-color:#f1ee18;/*所有识别*/
.background-color:#00deff\9;/*IE6、7、8识别*/
+background-color:#a200ff;/*IE6、7识别*/
_background-color:#1e0bd1;/*IE6识别*/
}

（5）IE下，可以使用获取常规属性的方法来获取自定义属性，也可以使用getAttribute()获取自定义
属性；Firefox下，只能使用getAttribute()获取自定义属性
解决方法：统一通过getAttribute()获取自定义属性。

（6）IE下，event对象有x、y属性，但是没有pageX、pageY属性;Firefox下，event对象有
pageX、pageY属性，但是没有x、y属性。
解决方法：（条件注释）缺点是在IE浏览器下可能会增加额外的HTTP请求数。

（7）Chrome中文界面下默认会将小于12px的文本强制按照12px显示
解决方法：

1.可通过加入CSS属性-webkit-text-size-adjust:none;解决。但是，在chrome
更新到27版本之后就不可以用了。

2.还可以使用-webkit-transform:scale(0.5);注意-webkit-transform:scale(0.75);
收缩的是整个span的大小，这时候，必须要将span转换成块元素，可以使用display：block/inline-block/...；

（8）超链接访问过后hover样式就不出现了，被点击访问过的超链接样式不再具有hover和active了
解决方法：改变CSS属性的排列顺序L-V-H-A

（9）怪异模式问题：漏写DTD声明，Firefox仍然会按照标准模式来解析网页，但在IE中会触发怪异模
式。为避免怪异模式给我们带来不必要的麻烦，最好养成书写DTD声明的好习惯。
```

</details>

<b><details><summary>118.li 与 li 之间有看不见的空白间隔是什么原因引起的？有什么解决办法？</summary></b>

参考答案：

```
浏览器会把inline元素间的空白字符（空格、换行、Tab等）渲染成一个空格。而为了美观。我们通常是一个<li>放在一行，
这导致<li>换行后产生换行字符，它变成一个空格，占用了一个字符的宽度。

解决办法：

（1）为<li>设置float:left。不足：有些容器是不能设置浮动，如左右切换的焦点图等。

（2）将所有<li>写在同一行。不足：代码不美观。

（3）将<ul>内的字符尺寸直接设为0，即font-size:0。不足：<ul>中的其他字符尺寸也被设为0，需要额外重新设定其他
字符尺寸，且在Safari浏览器依然会出现空白间隔。

（4）消除<ul>的字符间隔letter-spacing:-8px，不足：这也设置了<li>内的字符间隔，因此需要将<li>内的字符
间隔设为默认letter-spacing:normal。
```

详细资料可以参考：
[《li 与 li 之间有看不见的空白间隔是什么原因引起的？》](https://blog.csdn.net/sjinsa/article/details/70919546)

</details>

<b><details><summary>119.为什么要初始化 CSS 样式？</summary></b>

参考答案：

```
-因为浏览器的兼容问题，不同浏览器对有些标签的默认值是不同的，如果没对CSS初始化往往会出现浏览器之间的页面显示差异。

-当然，初始化样式会对SEO有一定的影响，但鱼和熊掌不可兼得，但力求影响最小的情况下初始化。

最简单的初始化方法：*{padding:0;margin:0;}（强烈不建议）

淘宝的样式初始化代码：
body,h1,h2,h3,h4,h5,h6,hr,p,blockquote,dl,dt,dd,ul,ol,li,pre,form,fieldset,legend
,button,input,textarea,th,td{margin:0;padding:0;}
body,button,input,select,textarea{font:12px/1.5tahoma,arial,\5b8b\4f53;}
h1,h2,h3,h4,h5,h6{font-size:100%;}
address,cite,dfn,em,var{font-style:normal;}
code,kbd,pre,samp{font-family:couriernew,courier,monospace;}
small{font-size:12px;}
ul,ol{list-style:none;}
a{text-decoration:none;}
a:hover{text-decoration:underline;}
sup{vertical-align:text-top;}
sub{vertical-align:text-bottom;}
legend{color:#000;}
fieldset,img{border:0;}
button,input,select,textarea{font-size:100%;}
table{border-collapse:collapse;border-spacing:0;}
```

</details>

<b><details><summary>120.什么是包含块，对于包含块的理解?</summary></b>

参考答案：

```
包含块（containing block）就是元素用来计算和定位的一个框。

（1）根元素（很多场景下可以看成是<html>）被称为“初始包含块”，其尺寸等同于浏览器可视窗口的大小。

（2）对于其他元素，如果该元素的position是relative或者static，则“包含块”由其最近的块容器祖先盒的content box
边界形成。

（3）如果元素position:fixed，则“包含块”是“初始包含块”。

（4）如果元素position:absolute，则“包含块”由最近的position不为static的祖先元素建立，具体方式如下：

如果该祖先元素是纯inline元素，则规则略复杂：
•假设给内联元素的前后各生成一个宽度为0的内联盒子（inline box），则这两个内联盒子的padding box外面的包
围盒就是内联元素的“包含块”；
•如果该内联元素被跨行分割了，那么“包含块”是未定义的，也就是CSS2.1规范并没有明确定义，浏览器自行发挥
否则，“包含块”由该祖先的padding box边界形成。

如果没有符合条件的祖先元素，则“包含块”是“初始包含块”。
```

</details>

<b><details><summary>121.CSS 里的 visibility 属性有个 collapse 属性值是干嘛用的？在不同浏览器下以后什么区别？</summary></b>

参考答案：

```
（1）对于一般的元素，它的表现跟visibility：hidden;是一样的。元素是不可见的，但此时仍占用页面空间。

（2）但例外的是，如果这个元素是table相关的元素，例如table行，table group，table列，table column group，它的
表现却跟display:none一样，也就是说，它们占用的空间也会释放。

在不同浏览器下的区别：

在谷歌浏览器里，使用collapse值和使用hidden值没有什么区别。

在火狐浏览器、Opera和IE11里，使用collapse值的效果就如它的字面意思：table的行会消失，它的下面一行会补充它的位
置。

```

详细资料可以参考：
[《CSS 里的 visibility 属性有个鲜为人知的属性值：collapse》](http://www.webhek.com/post/visibility-collapse.html)

</details>

<b><details><summary>122.width:auto 和 width:100%的区别</summary></b>

参考答案：

```
一般而言

width:100%会使元素box的宽度等于父元素的content box的宽度。

width:auto会使元素撑满整个父元素，margin、border、padding、content区域会自动分配水平空间。
```

</details>

<b><details><summary>123.绝对定位元素与非绝对定位元素的百分比计算的区别</summary></b>

参考答案：

```
绝对定位元素的宽高百分比是相对于临近的position不为static的祖先元素的padding box来计算的。

非绝对定位元素的宽高百分比则是相对于父元素的content box来计算的。
```

</details>

<b><details><summary>124.简单介绍使用图片 base64 编码的优点和缺点。</summary></b>

参考答案：

```
base64编码是一种图片处理格式，通过特定的算法将图片编码成一长串字符串，在页面上显示的时候，可以用该字符串来代替图片的
url属性。

使用base64的优点是：

（1）减少一个图片的HTTP请求

使用base64的缺点是：

（1）根据base64的编码原理，编码后的大小会比原文件大小大1/3，如果把大图片编码到html/css中，不仅会造成文件体
积的增加，影响文件的加载速度，还会增加浏览器对html或css文件解析渲染的时间。

（2）使用base64无法直接缓存，要缓存只能缓存包含base64的文件，比如HTML或者CSS，这相比域直接缓存图片的效果要
差很多。

（3）兼容性的问题，ie8以前的浏览器不支持。

一般一些网站的小图标可以使用base64图片来引入。
```

详细资料可以参考：
[《玩转图片 base64 编码》](https://www.cnblogs.com/coco1s/p/4375774.html)
[《前端开发中，使用 base64 图片的弊端是什么？》](https://www.zhihu.com/question/31155574)
[《小 tip:base64:URL 背景图片与 web 页面性能优化》](https://www.zhangxinxu.com/wordpress/2012/04/base64-url-image-%E5%9B%BE%E7%89%87-%E9%A1%B5%E9%9D%A2%E6%80%A7%E8%83%BD%E4%BC%98%E5%8C%96/)

</details>

<b><details><summary>125.'display'、'position'和'float'的相互关系？</summary></b>

参考答案：

```
（1）首先我们判断display属性是否为none，如果为none，则position和float属性的值不影响元素最后的表现。

（2）然后判断position的值是否为absolute或者fixed，如果是，则float属性失效，并且display的值应该被
设置为table或者block，具体转换需要看初始转换值。

（3）如果position的值不为absolute或者fixed，则判断float属性的值是否为none，如果不是，则display
的值则按上面的规则转换。注意，如果position的值为relative并且float属性的值存在，则relative相对
于浮动后的最终位置定位。

（4）如果float的值为none，则判断元素是否为根元素，如果是根元素则display属性按照上面的规则转换，如果不是，
则保持指定的display属性值不变。

总的来说，可以把它看作是一个类似优先级的机制，"position:absolute"和"position:fixed"优先级最高，有它存在
的时候，浮动不起作用，'display'的值也需要调整；其次，元素的'float'特性的值不是"none"的时候或者它是根元素
的时候，调整'display'的值；最后，非根元素，并且非浮动元素，并且非绝对定位的元素，'display'特性值同设置值。

```

详细资料可以参考：
[《position 跟 display、margincollapse、overflow、float 这些特性相互叠加后会怎么样？》](https://www.cnblogs.com/jackyWHJ/p/3756087.html)

</details>

<b><details><summary>126.margin 重叠问题的理解。</summary></b>

参考答案：

相关知识点：

```
块级元素的上外边距（margin-top）与下外边距（margin-bottom）有时会合并为单个外边距，这样的现象称为“margin合
并”。

产生折叠的必备条件：margin必须是邻接的!

而根据w3c规范，两个margin是邻接的必须满足以下条件：

•必须是处于常规文档流（非float和绝对定位）的块级盒子，并且处于同一个BFC当中。
•没有线盒，没有空隙，没有padding和border将他们分隔开
•都属于垂直方向上相邻的外边距，可以是下面任意一种情况
•元素的margin-top与其第一个常规文档流的子元素的margin-top
•元素的margin-bottom与其下一个常规文档流的兄弟元素的margin-top
•height为auto的元素的margin-bottom与其最后一个常规文档流的子元素的margin-bottom
•高度为0并且最小高度也为0，不包含常规文档流的子元素，并且自身没有建立新的BFC的元素的margin-top
和margin-bottom


margin合并的3种场景：

（1）相邻兄弟元素margin合并。

解决办法：
•设置块状格式化上下文元素（BFC）

（2）父级和第一个/最后一个子元素的margin合并。

解决办法：

对于margin-top合并，可以进行如下操作（满足一个条件即可）：
•父元素设置为块状格式化上下文元素；
•父元素设置border-top值；
•父元素设置padding-top值；
•父元素和第一个子元素之间添加内联元素进行分隔。

对于margin-bottom合并，可以进行如下操作（满足一个条件即可）：
•父元素设置为块状格式化上下文元素；
•父元素设置border-bottom值；
•父元素设置padding-bottom值；
•父元素和最后一个子元素之间添加内联元素进行分隔；
•父元素设置height、min-height或max-height。

（3）空块级元素的margin合并。

解决办法：
•设置垂直方向的border；
•设置垂直方向的padding；
•里面添加内联元素（直接Space键空格是没用的）；
•设置height或者min-height。
```

回答：

```
margin重叠指的是在垂直方向上，两个相邻元素的margin发生重叠的情况。

一般来说可以分为四种情形：

第一种是相邻兄弟元素的marin-bottom和margin-top的值发生重叠。这种情况下我们可以通过设置其中一个元素为BFC
来解决。

第二种是父元素的margin-top和子元素的margin-top发生重叠。它们发生重叠是因为它们是相邻的，所以我们可以通过这
一点来解决这个问题。我们可以为父元素设置border-top、padding-top值来分隔它们，当然我们也可以将父元素设置为BFC
来解决。

第三种是高度为auto的父元素的margin-bottom和子元素的margin-bottom发生重叠。它们发生重叠一个是因为它们相
邻，一个是因为父元素的高度不固定。因此我们可以为父元素设置border-bottom、padding-bottom来分隔它们，也可以为
父元素设置一个高度，max-height和min-height也能解决这个问题。当然将父元素设置为BFC是最简单的方法。

第四种情况，是没有内容的元素，自身的margin-top和margin-bottom发生的重叠。我们可以通过为其设置border、pa
dding或者高度来解决这个问题。
```

</details>

<b><details><summary>127.对 BFC 规范（块级格式化上下文：block formatting context）的理解？</summary></b>

参考答案：

相关知识点：

```
块格式化上下文（Block Formatting Context，BFC）是Web页面的可视化CSS渲染的一部分，是布局过程中生成块级盒
子的区域，也是浮动元素与其他元素的交互限定区域。

通俗来讲

•BFC是一个独立的布局环境，可以理解为一个容器，在这个容器中按照一定规则进行物品摆放，并且不会影响其它环境中的物品。
•如果一个元素符合触发BFC的条件，则BFC中的元素布局不受外部影响。

创建BFC

（1）根元素或包含根元素的元素
（2）浮动元素float＝left|right或inherit（≠none）
（3）绝对定位元素position＝absolute或fixed
（4）display＝inline-block|flex|inline-flex|table-cell或table-caption
（5）overflow＝hidden|auto或scroll(≠visible)

```

回答：

```
BFC指的是块级格式化上下文，一个元素形成了BFC之后，那么它内部元素产生的布局不会影响到外部元素，外部元素的布局也
不会影响到BFC中的内部元素。一个BFC就像是一个隔离区域，和其他区域互不影响。

一般来说根元素是一个BFC区域，浮动和绝对定位的元素也会形成BFC，display属性的值为inline-block、flex这些
属性时也会创建BFC。还有就是元素的overflow的值不为visible时都会创建BFC。
```

详细资料可以参考：
[《深入理解 BFC 和 MarginCollapse》](https://www.w3cplus.com/css/understanding-bfc-and-margin-collapse.html)
[《前端面试题-BFC（块格式化上下文）》](https://segmentfault.com/a/1190000013647777)

</details>

<b><details><summary>128.IFC 是什么？</summary></b>

参考答案：

```
IFC指的是行级格式化上下文，它有这样的一些布局规则：

（1）行级上下文内部的盒子会在水平方向，一个接一个地放置。
（2）当一行不够的时候会自动切换到下一行。
（3）行级上下文的高度由内部最高的内联盒子的高度决定。
```

详细资料可以参考：
[《[译]:BFC 与 IFC》](https://segmentfault.com/a/1190000004466536#articleHeader5)
[《BFC 和 IFC 的理解（布局）》](https://blog.csdn.net/paintandraw/article/details/80401741)

</details>

<b><details><summary>129.请解释一下为什么需要清除浮动？清除浮动的方式</summary></b>

参考答案：

```
浮动元素可以左右移动，直到遇到另一个浮动元素或者遇到它外边缘的包含框。浮动框不属于文档流中的普通流，当元素浮动之后，
不会影响块级元素的布局，只会影响内联元素布局。此时文档流中的普通流就会表现得该浮动框不存在一样的布局模式。当包含框
的高度小于浮动框的时候，此时就会出现“高度塌陷”。

清除浮动是为了清除使用浮动元素产生的影响。浮动的元素，高度会塌陷，而高度的塌陷使我们页面后面的布局不能正常显示。

清除浮动的方式

（1）使用clear属性清除浮动。参考28。

（2）使用BFC块级格式化上下文来清除浮动。参考26。

因为BFC元素不会影响外部元素的特点，所以BFC元素也可以用来清除浮动的影响，因为如果不清除，子元素浮动则父元
素高度塌陷，必然会影响后面元素布局和定位，这显然有违BFC元素的子元素不会影响外部元素的设定。
```

</details>

<b><details><summary>130.使用 clear 属性清除浮动的原理？</summary></b>

参考答案：

```
使用clear属性清除浮动，其语法如下：

clear:none|left|right|both

如果单看字面意思，clear:left应该是“清除左浮动”，clear:right应该是“清除右浮动”的意思，实际上，这种解释是有问
题的，因为浮动一直还在，并没有清除。

官方对clear属性的解释是：“元素盒子的边不能和前面的浮动元素相邻。”，我们对元素设置clear属性是为了避免浮动元素
对该元素的影响，而不是清除掉浮动。

还需要注意的一点是clear属性指的是元素盒子的边不能和前面的浮动元素相邻，注意这里“前面的”3个字，也就是clear属
性对“后面的”浮动元素是不闻不问的。考虑到float属性要么是left，要么是right，不可能同时存在，同时由于clear
属性对“后面的”浮动元素不闻不问，因此，当clear:left有效的时候，clear:right必定无效，也就是此时clear:left
等同于设置clear:both；同样地，clear:right如果有效也是等同于设置clear:both。由此可见，clear:left和cle
ar:right这两个声明就没有任何使用的价值，至少在CSS世界中是如此，直接使用clear:both吧。

一般使用伪元素的方式清除浮动

.clear::after{
content:'';
display:table;//也可以是'block'，或者是'list-item'
clear:both;
}

clear属性只有块级元素才有效的，而::after等伪元素默认都是内联水平，这就是借助伪元素清除浮动影响时需要设置disp
lay属性值的原因。
```

</details>

<b><details><summary>131.zoom:1 的清除浮动原理?</summary></b>

参考答案：

```
清除浮动，触发hasLayout；
zoom属性是IE浏览器的专有属性，它可以设置或检索对象的缩放比例。解决ie下比较奇葩的bug。譬如外边距（margin）
的重叠，浮动清除，触发ie的haslayout属性等。

来龙去脉大概如下：
当设置了zoom的值之后，所设置的元素就会就会扩大或者缩小，高度宽度就会重新计算了，这里一旦改变zoom值时其实也会发
生重新渲染，运用这个原理，也就解决了ie下子元素浮动时候父元素不随着自动扩大的问题。

zoom属性是IE浏览器的专有属性，火狐和老版本的webkit核心的浏览器都不支持这个属性。然而，zoom现在已经被逐步标
准化，出现在CSS3.0规范草案中。

目前非ie由于不支持这个属性，它们又是通过什么属性来实现元素的缩放呢？可以通过css3里面的动画属性scale进行缩放。
```

</details>

<b><details><summary>132.移动端的布局用过媒体查询吗？</summary></b>

参考答案：

```
假设你现在正用一台显示设备来阅读这篇文章，同时你也想把它投影到屏幕上，或者打印出来，而显示设备、屏幕投影和打印等这些
媒介都有自己的特点，CSS就是为文档提供在不同媒介上展示的适配方法

当媒体查询为真时，相关的样式表或样式规则会按照正常的级联规被应用。当媒体查询返回假，标签上带有媒体查询的样式表仍将被
下载（只不过不会被应用）。

包含了一个媒体类型和至少一个使用宽度、高度和颜色等媒体属性来限制样式表范围的表达式。CSS3加入的媒体查询使得无需修改
内容便可以使样式应用于某些特定的设备范围。
```

详细资料可以参考：
[《CSS3@media 查询》](http://www.runoob.com/cssref/css3-pr-mediaquery.html)
[《响应式布局和自适应布局详解》](http://caibaojian.com/356.html)

</details>

<b><details><summary>133.使用 CSS 预处理器吗？喜欢哪个？</summary></b>

参考答案：

```
SASS（SASS、LESS没有本质区别，只因为团队前端都是用的SASS）
```

</details>

<b><details><summary>134.CSS 优化、提高性能的方法有哪些？</summary></b>

参考答案：

```
加载性能：

（1）css压缩：将写好的css进行打包压缩，可以减少很多的体积。
（2）css单一样式：当需要下边距和左边距的时候，很多时候选择:margin:top 0 bottom 0;但margin-bottom:bot
tom;margin-left:left;执行的效率更高。
（3）减少使用@import,而建议使用link，因为后者在页面加载时一起加载，前者是等待页面加载完成之后再进行加载。

选择器性能：

（1）关键选择器（key selector）。选择器的最后面的部分为关键选择器（即用来匹配目标元素的部分）。CSS选择符是从右到
左进行匹配的。当使用后代选择器的时候，浏览器会遍历所有子元素来确定是否是指定的元素等等；

（2）如果规则拥有ID选择器作为其关键选择器，则不要为规则增加标签。过滤掉无关的规则（这样样式系统就不会浪费时间去匹
配它们了）。

（3）避免使用通配规则，如*{}计算次数惊人！只对需要用到的元素进行选择。

（4）尽量少的去对标签进行选择，而是用class。

（5）尽量少的去使用后代选择器，降低选择器的权重值。后代选择器的开销是最高的，尽量将选择器的深度降到最低，最高不要超过
三层，更多的使用类来关联每一个标签元素。

（6）了解哪些属性是可以通过继承而来的，然后避免对这些属性重复指定规则。

渲染性能：

（1）慎重使用高性能属性：浮动、定位。

（2）尽量减少页面重排、重绘。

（3）去除空规则：｛｝。空规则的产生原因一般来说是为了预留样式。去除这些空规则无疑能减少css文档体积。

（4）属性值为0时，不加单位。

（5）属性值为浮动小数0.**，可以省略小数点之前的0。

（6）标准化各种浏览器前缀：带浏览器前缀的在前。标准属性在后。

（7）不使用@import前缀，它会影响css的加载速度。

（8）选择器优化嵌套，尽量避免层级过深。

（9）css雪碧图，同一页面相近部分的小图标，方便使用，减少页面的请求次数，但是同时图片本身会变大，使用时，优劣考虑清
楚，再使用。

（10）正确使用display的属性，由于display的作用，某些样式组合会无效，徒增样式体积的同时也影响解析性能。

（11）不滥用web字体。对于中文网站来说WebFonts可能很陌生，国外却很流行。web fonts通常体积庞大，而且一些浏
览器在下载web fonts时会阻塞页面渲染损伤性能。

可维护性、健壮性：

（1）将具有相同属性的样式抽离出来，整合并通过class在页面中进行使用，提高css的可维护性。
（2）样式与内容分离：将css代码定义到外部css中。
```

详细资料可以参考：
[《CSS 优化、提高性能的方法有哪些？》](https://www.zhihu.com/question/19886806)
[《CSS 优化，提高性能的方法》](https://www.jianshu.com/p/4e673bf24a3b)

</details>

<b><details><summary>135.浏览器是怎样解析 CSS 选择器的？</summary></b>

参考答案：

```
样式系统从关键选择器开始匹配，然后左移查找规则选择器的祖先元素。只要选择器的子树一直在工作，样式系统就会持续左移，直
到和规则匹配，或者是因为不匹配而放弃该规则。

试想一下，如果采用从左至右的方式读取CSS规则，那么大多数规则读到最后（最右）才会发现是不匹配的，这样做会费时耗能，
最后有很多都是无用的；而如果采取从右向左的方式，那么只要发现最右边选择器不匹配，就可以直接舍弃了，避免了许多无效匹配。
```

详细资料可以参考：
[《探究 CSS 解析原理》](https://juejin.im/entry/5a123c55f265da432240cc90)

</details>

<b><details><summary>136.在网页中应该使用奇数还是偶数的字体？为什么呢？</summary></b>

参考答案：

```
（1）偶数字号相对更容易和web设计的其他部分构成比例关系。比如：当我用了14px的正文字号，我可能会在一些地方用14
×0.5=7px的margin，在另一些地方用14×1.5=21px的标题字号。
（2）浏览器缘故，低版本的浏览器ie6会把奇数字体强制转化为偶数，即13px渲染为14px。
（3）系统差别，早期的Windows里，中易宋体点阵只有12和14、15、16px，唯独缺少13px。
```

详细资料可以参考：
[《谈谈网页中使用奇数字体和偶数字体》](https://blog.csdn.net/jian_xi/article/details/79346477)
[《现在网页设计中的为什么少有人用 11px、13px、15px 等奇数的字体？》](https://www.zhihu.com/question/20440679)

</details>

<b><details><summary>137.margin 和 padding 分别适合什么场景使用？</summary></b>

参考答案：

```
margin是用来隔开元素与元素的间距；padding是用来隔开元素与内容的间隔。
margin用于布局分开元素使元素与元素互不相干。
padding用于元素与内容之间的间隔，让内容（文字）与（包裹）元素之间有一段距离。

何时应当使用margin：
•需要在border外侧添加空白时。
•空白处不需要背景（色）时。
•上下相连的两个盒子之间的空白，需要相互抵消时。如15px+20px的margin，将得到20px的空白。

何时应当时用padding：
•需要在border内测添加空白时。
•空白处需要背景（色）时。
•上下相连的两个盒子之间的空白，希望等于两者之和时。如15px+20px的padding，将得到35px的空白。
```

</details>

<b><details><summary>138.抽离样式模块怎么写，说出思路，有无实践经验？[阿里航旅的面试题]</summary></b>

参考答案：

```
我的理解是把常用的css样式单独做成css文件……通用的和业务相关的分离出来，通用的做成样式模块儿共享，业务相关的，放
进业务相关的库里面做成对应功能的模块儿。
```

详细资料可以参考：
[《CSS 规范-分类方法》](http://nec.netease.com/standard/css-sort.html)

</details>

<b><details><summary>139.简单说一下 css3 的 all 属性。</summary></b>

参考答案：

```
all属性实际上是所有CSS属性的缩写，表示，所有的CSS属性都怎样怎样，但是，不包括unicode-bidi和direction
这两个CSS属性。支持三个CSS通用属性值，initial,inherit,unset。

initial是初始值的意思，也就是该元素元素都除了unicode-bidi和direction以外的CSS属性都使用属性的默认初始
值。

inherit是继承的意思，也就是该元素除了unicode-bidi和direction以外的CSS属性都继承父元素的属性值。

unset是取消设置的意思，也就是当前元素浏览器或用户设置的CSS忽略，然后如果是具有继承特性的CSS，如color，则
使用继承值；如果是没有继承特性的CSS属性，如background-color，则使用初始值。

```

详细资料可以参考：
[《简单了解 CSS3 的 all 属性》](https://www.zhangxinxu.com/wordpress/2016/03/know-about-css3-all/)

</details>

<b><details><summary>140.为什么不建议使用统配符初始化 css 样式。</summary></b>

参考答案：

```
采用*{padding:0;margin:0;}这样的写法好处是写起来很简单，但是是通配符，需要把所有的标签都遍历一遍，当网站较大时，
样式比较多，这样写就大大的加强了网站运行的负载，会使网站加载的时候需要很长一段时间，因此一般大型的网站都有分层次的一
套初始化样式。

出于性能的考虑，并不是所有标签都会有padding和margin，因此对常见的具有默认padding和margin的元素初始化即
可，并不需使用通配符*来初始化。
```

</details>

<b><details><summary>141.absolute 的 containingblock（包含块）计算方式跟正常流有什么不同？</summary></b>

参考答案：

```
（1）内联元素也可以作为“包含块”所在的元素；

（2）“包含块”所在的元素不是父块级元素，而是最近的position不为static的祖先元素或根元素；

（3）边界是padding box而不是content box。
```

</details>

<b><details><summary>142.对于 hasLayout 的理解？</summary></b>

参考答案：

```
hasLayout是IE特有的一个属性。很多的IE下的css bug都与其息息相关。在IE中，一个元素要么自己对自身的内容进
行计算大小和组织，要么依赖于父元素来计算尺寸和组织内容。当一个元素的hasLayout属性值为true时，它负责对自己和可
能的子孙元素进行尺寸计算和定位。虽然这意味着这个元素需要花更多的代价来维护自身和里面的内容，而不是依赖于祖先元素来完
成这些工作。
```

详细资料可以参考：
[《CSS 基础篇--CSS 中 IE 浏览器的 hasLayout，IE 低版本的 bug 根源》](https://segmentfault.com/a/1190000010883974)
[《CSS 魔法堂：hasLayout 原来是这样的！》](https://segmentfault.com/a/1190000004632071)

</details>

<b><details><summary>143.元素竖向的百分比设定是相对于容器的高度吗？</summary></b>

参考答案：

```
如果是height的话，是相对于包含块的高度。

如果是padding或者margin竖直方向的属性则是相对于包含块的宽度。
```

</details>

<b><details><summary>144.全屏滚动的原理是什么？用到了 CSS 的哪些属性？（待深入实践）</summary></b>

参考答案：

```
原理：有点类似于轮播，整体的元素一直排列下去，假设有5个需要展示的全屏页面，那么高度是500%，只是展示100%，容器及容
器内的页面取当前可视区高度，同时容器的父级元素overflow属性值设为hidden，通过更改容器可视区的位置来实现全
屏滚动效果。主要是响应鼠标事件，页面通过CSS的动画效果，进行移动。

overflow：hidden；transition：all 1000 ms ease；
```

详细资料可以参考：
[《js 实现网页全屏切换（平滑过渡），鼠标滚动切换》](https://blog.csdn.net/liona_koukou/article/details/52680409)
[《用 ES6 写全屏滚动插件》](https://juejin.im/post/5aeef41cf265da0ba0630de0)

</details>

<b><details><summary>145.什么是响应式设计？响应式设计的基本原理是什么？如何兼容低版本的 IE？（待深入了解）</summary></b>

参考答案：

```
响应式网站设计是一个网站能够兼容多个终端，而不是为每一个终端做一个特定的版本。基本原理是通过媒体查询检测不同的设备屏
幕尺寸做处理。页面头部必须有meta声明的viewport。
```

详细资料可以参考：
[《响应式布局原理》](https://blog.csdn.net/dreamerframework/article/details/8994741)
[《响应式布局的实现方法和原理》](http://www.mahaixiang.cn/wzsj/278.html)

</details>

<b><details><summary>146.视差滚动效果，如何给每页做不同的动画？（回到顶部，向下滑动要再次出现，和只出现一次分别怎么</summary></b>

参考答案：做？）

```
视差滚动是指多层背景以不同的速度移动，形成立体的运动效果，带来非常出色的视觉体验。
```

详细资料可以参考：
[《如何实现视差滚动效果的网页？》](https://www.zhihu.com/question/20990029)

</details>

<b><details><summary>147.如何修改 chrome 记住密码后自动填充表单的黄色背景？</summary></b>

参考答案：

```
chrome表单自动填充后，input文本框的背景会变成黄色的，通过审查元素可以看到这是由于chrome会默认给自动填充的in
put表单加上input:-webkit-autofill私有属性，然后对其赋予以下样式：

{
background-color:rgb(250,255,189)!important;
background-image:none!important;
color:rgb(0,0,0)!important;
}

对chrome默认定义的background-color，background-image，color使用important是不能提高其优先级的，但是
其他属性可使用。

使用足够大的纯色内阴影来覆盖input输入框的黄色背景，处理如下

input:-webkit-autofill,textarea:-webkit-autofill,select:-webkit-autofill{
-webkit-box-shadow:000px 1000px white inset;
border:1px solid #CCC !important;
}

```

详细资料可以参考：
[《去掉 chrome 记住密码后的默认填充样式》](https://blog.csdn.net/zsl_955200/article/details/78276209)
[《修改谷歌浏览器 chrome 记住密码后自动填充表单的黄色背景》](https://blog.csdn.net/M_agician/article/details/73381706)

</details>

<b><details><summary>148.怎么让 Chrome 支持小于 12px 的文字？</summary></b>

参考答案：

```
在谷歌下css设置字体大小为12px及以下时，显示都是一样大小，都是默认12px。

解决办法：

（1）可以使用Webkit的内核的-webkit-text-size-adjust的私有CSS属性来解决，只要加了-webkit-text-size
-adjust:none;字体大小就不受限制了。但是chrome更新到27版本之后就不可以用了。所以高版本chrome谷歌浏览器
已经不再支持-webkit-text-size-adjust样式，所以要使用时候慎用。

（2）还可以使用css3的transform缩放属性-webkit-transform:scale(0.5);注意-webkit-transform:scale(0.
75);收缩的是整个元素的大小，这时候，如果是内联元素，必须要将内联元素转换成块元素，可以使用display：block/
inline-block/...；

（3）使用图片：如果是内容固定不变情况下，使用将小于12px文字内容切出做图片，这样不影响兼容也不影响美观。
```

详细资料可以参考：
[《谷歌浏览器不支持 CSS 设置小于 12px 的文字怎么办？》](https://570109268.iteye.com/blog/2406562)

</details>

<b><details><summary>149.让页面里的字体变清晰，变细用 CSS 怎么做？</summary></b>

参考答案：

```
webkit内核的私有属性：-webkit-font-smoothing，用于字体抗锯齿，使用后字体看起来会更清晰舒服。

在MacOS测试环境下面设置-webkit-font-smoothing:antialiased;但是这个属性仅仅是面向MacOS，其他操作系统设
置后无效。
```

详细资料可以参考：
[《让字体变的更清晰 CSS 中-webkit-font-smoothing》](https://blog.csdn.net/huo_bao/article/details/50251585)

</details>

<b><details><summary>150.font-style 属性中 italic 和 oblique 的区别？</summary></b>

参考答案：

```
italic和oblique这两个关键字都表示“斜体”的意思。

它们的区别在于，italic是使用当前字体的斜体字体，而oblique只是单纯地让文字倾斜。如果当前字体没有对应的斜体字体，
则退而求其次，解析为oblique，也就是单纯形状倾斜。
```

</details>

<b><details><summary>151.设备像素、css 像素、设备独立像素、dpr、ppi 之间的区别？</summary></b>

参考答案：

```
设备像素指的是物理像素，一般手机的分辨率指的就是设备像素，一个设备的设备像素是不可变的。

css像素和设备独立像素是等价的，不管在何种分辨率的设备上，css像素的大小应该是一致的，css像素是一个相对单位，它是相
对于设备像素的，一个css像素的大小取决于页面缩放程度和dpr的大小。

dpr指的是设备像素和设备独立像素的比值，一般的pc屏幕，dpr=1。在iphone4时，苹果推出了retina屏幕，它的dpr
为2。屏幕的缩放会改变dpr的值。

ppi指的是每英寸的物理像素的密度，ppi越大，屏幕的分辨率越大。
```

详细资料可以参考：
[《什么是物理像素、虚拟像素、逻辑像素、设备像素，什么又是 PPI,DPI,DPR 和 DIP》](https://www.cnblogs.com/libin-1/p/7148377.html)
[《前端工程师需要明白的「像素」》](https://www.jianshu.com/p/af6dad66e49a)
[《CSS 像素、物理像素、逻辑像素、设备像素比、PPI、Viewport》](https://github.com/jawil/blog/issues/21)
[《前端开发中像素的概念》](https://github.com/wujunchuan/wujunchuan.github.io/issues/15)

</details>

<b><details><summary>152.layout viewport、visual viewport 和 ideal viewport 的区别？</summary></b>

参考答案：

相关知识点：

```
如果把移动设备上浏览器的可视区域设为viewport的话，某些网站就会因为viewport太窄而显示错乱，所以这些浏览器就决定
默认情况下把viewport设为一个较宽的值，比如980px，这样的话即使是那些为桌面设计的网站也能在移动浏览器上正常显示了。
ppk把这个浏览器默认的viewport叫做layout viewport。

layout viewport的宽度是大于浏览器可视区域的宽度的，所以我们还需要一个viewport来代表浏览器可视区域的大小，ppk把
这个viewport叫做visual viewport。

ideal viewport是最适合移动设备的viewport，ideal viewport的宽度等于移动设备的屏幕宽度，只要在css中把某一元
素的宽度设为ideal viewport的宽度（单位用px），那么这个元素的宽度就是设备屏幕的宽度了，也就是宽度为100%的效果。i
deal viewport的意义在于，无论在何种分辨率的屏幕下，那些针对ideal viewport而设计的网站，不需要用户手动缩放，也
不需要出现横向滚动条，都可以完美的呈现给用户。
```

回答：

```
移动端一共需要理解三个viewport的概念的理解。

第一个视口是布局视口，在移动端显示网页时，由于移动端的屏幕尺寸比较小，如果网页使用移动端的屏幕尺寸进行布局的话，那么整
个页面的布局都会显示错乱。所以移动端浏览器提供了一个layout viewport布局视口的概念，使用这个视口来对页面进行布局展
示，一般layout viewport的大小为980px，因此页面布局不会有太大的变化，我们可以通过拖动和缩放来查看到这个页面。

第二个视口指的是视觉视口，visual viewport指的是移动设备上我们可见的区域的视口大小，一般为屏幕的分辨率的大小。visu
al viewport和layout viewport的关系，就像是我们通过窗户看外面的风景，视觉视口就是窗户，而外面的风景就是布局视口
中的网页内容。

第三个视口是理想视口，由于layout viewport一般比visual viewport要大，所以想要看到整个页面必须通过拖动和缩放才
能实现。所以又提出了ideal viewport的概念，ideal viewport下用户不用缩放和滚动条就能够查看到整个页面，并且页面在
不同分辨率下显示的内容大小相同。ideal viewport其实就是通过修改layout viewport的大小，让它等于设备的宽度，这个
宽度可以理解为是设备独立像素，因此根据ideal viewport设计的页面，在不同分辨率的屏幕下，显示应该相同。
```

详细资料可以参考：
[《移动前端开发之 viewport 的深入理解》](https://www.cnblogs.com/2050/p/3877280.html)
[《说说移动前端中 viewport（视口）》](https://www.html.cn/archives/5975)
[《移动端适配知识你到底知多少》](https://juejin.im/post/5b6d21daf265da0f9d1a2ed7#heading-14)

</details>

<b><details><summary>153.position:fixed;在 android 下无效怎么处理？</summary></b>

参考答案：

```
因为移动端浏览器默认的viewport叫做layout viewport。在移动端显示时，因为layout viewport的宽度大于移动端屏幕
的宽度，所以页面会出现滚动条左右移动，fixed的元素是相对layout viewport来固定位置的，而不是移动端屏幕来固定位置的
，所以会出现感觉fixed无效的情况。

如果想实现fixed相对于屏幕的固定效果，我们需要改变的是viewport的大小为ideal viewport，可以如下设置：

<metaname="viewport"content="width=device-width,initial-scale=1.0,maximum-scale=1.0,minimum-sca
le=1.0,user-scalable=no"/>
```

</details>

<b><details><summary>154.如果需要手动写动画，你认为最小时间间隔是多久，为什么？（阿里）</summary></b>

参考答案：

```
多数显示器默认频率是60Hz，即1秒刷新60次，所以理论上最小间隔为1/60*1000ms＝16.7ms
```

</details>

<b><details><summary>155.如何让去除 inline-block 元素间间距？</summary></b>

参考答案：

```
移除空格、使用margin负值、使用font-size:0、letter-spacing、word-spacing
```

详细资料可以参考：
[《去除 inline-block 元素间间距的 N 种方法》](https://www.zhangxinxu.com/wordpress/2012/04/inline-block-space-remove-%E5%8E%BB%E9%99%A4%E9%97%B4%E8%B7%9D/)

</details>

<b><details><summary>156.overflow:scroll 时不能平滑滚动的问题怎么处理？</summary></b>

参考答案：

```
以下代码可解决这种卡顿的问题：-webkit-overflow-scrolling:touch;是因为这行代码启用了硬件加速特性，所以滑动很流
畅。
```

详细资料可以参考：
[《解决页面使用 overflow:scroll 在 iOS 上滑动卡顿的问题》](https://www.jianshu.com/p/1f4693d0ad2d)

</details>

<b><details><summary>157.有一个高度自适应的 div，里面有两个 div，一个高度 100px，希望另一个填满剩下的高度。</summary></b>

参考答案：

```
（1）外层div使用position：relative；高度要求自适应的div使用position:absolute;top:100px;bottom:0;
left:0;right:0;

（2）使用flex布局，设置主轴为竖轴，第二个div的flex-grow为1。
```

详细资料可以参考：
[《有一个高度自适应的 div，里面有两个 div，一个高度 100px，希望另一个填满剩下的高度(三种方案)》](https://blog.csdn.net/xutongbao/article/details/79408522)

</details>

<b><details><summary>158.png、jpg、gif 这些图片格式解释一下，分别什么时候用。有没有了解过 webp？</summary></b>

参考答案：

相关知识点：

```
（1）BMP，是无损的、既支持索引色也支持直接色的、点阵图。这种图片格式几乎没有对数据进行压缩，所以BMP格式的图片通常具有较大的文件大小。

（2）GIF是无损的、采用索引色的、点阵图。采用LZW压缩算法进行编码。文件小，是GIF格式的优点，同时，GIF格式还具有支持动画以及透明的优点。但，GIF格式仅支持8bit的索引色，所以GIF格式适用于对色彩要求不高同时需要文件体积较小的场景。

（3）JPEG是有损的、采用直接色的、点阵图。JPEG的图片的优点，是采用了直接色，得益于更丰富的色彩，JPEG非常适合用来存储照片，与GIF相比，JPEG不适合用来存储企业Logo、线框类的图。因为有损压缩会导致图片模糊，而直接色的选用，又会导致图片文件较GIF更大。

（4）PNG-8是无损的、使用索引色的、点阵图。PNG是一种比较新的图片格式，PNG-8是非常好的GIF格式替代者，在可能的情况下，应该尽可能的使用PNG-8而不是GIF，因为在相同的图片效果下，PNG-8具有更小的文件体积。除此之外，PNG-8还支持透明度的调节，而GIF并不支持。现在，除非需要动画的支持，否则我们没有理由使用GIF而不是PNG-8。

（5）PNG-24是无损的、使用直接色的、点阵图。PNG-24的优点在于，它压缩了图片的数据，使得同样效果的图片，PNG-24格式的文件大小要比BMP小得多。当然，PNG24的图片还是要比JPEG、GIF、PNG-8大得多。

（6）SVG是无损的、矢量图。SVG是矢量图。这意味着SVG图片由直线和曲线以及绘制它们的方法组成。当你放大一个SVG图片的时候，你看到的还是线和曲线，而不会出现像素点。这意味着SVG图片在放大时，不会失真，所以它非常适合用来绘制企业Logo、Icon等。

（7）WebP是谷歌开发的一种新图片格式，WebP是同时支持有损和无损压缩的、使用直接色的、点阵图。从名字就可以看出来它是为Web而生的，什么叫为Web而生呢？就是说相同质量的图片，WebP具有更小的文件体积。现在网站上充满了大量的图片，如果能够降低每一个图片的文件大小，那么将大大减少浏览器和服务器之间的数据传输量，进而降低访问延迟，提升访问体验。

•在无损压缩的情况下，相同质量的WebP图片，文件大小要比PNG小26%；
•在有损压缩的情况下，具有相同图片精度的WebP图片，文件大小要比JPEG小25%~34%；
•WebP图片格式支持图片透明度，一个无损压缩的WebP图片，如果要支持透明度只需要22%的格外文件大小。

但是目前只有Chrome浏览器和Opera浏览器支持WebP格式，兼容性不太好。
```

回答：

```
我了解到的一共有七种常见的图片的格式。

（1）第一种是BMP格式，它是无损压缩的，支持索引色和直接色的点阵图。由于它基本上没有进行压缩，因此它的文件体积一般比较大。

（2）第二种是GIF格式，它是无损压缩的使用索引色的点阵图。由于使用了LZW压缩方法，因此文件的体积很小。并且GIF还支持动画和透明度。但因为它使用的是索引色，所以它适用于一些对颜色要求不高且需要文件体积小的场景。

（3）第三种是JPEG格式，它是有损压缩的使用直接色的点阵图。由于使用了直接色，色彩较为丰富，一般适用于来存储照片。但由于使用的是直接色，可能文件的体积相对于GIF格式来说更大。

（4）第四种是PNG-8格式，它是无损压缩的使用索引色的点阵图。它是GIF的一种很好的替代格式，它也支持透明度的调整，并且文件的体积相对于GIF格式更小。一般来说如果不是需要动画的情况，我们都可以使用PNG-8格式代替GIF格式。

（5）第五种是PNG-24格式，它是无损压缩的使用直接色的点阵图。PNG-24的优点是它使用了压缩算法，所以它的体积比BMP格式的文件要小得多，但是相对于其他的几种格式，还是要大一些。

（6）第六种格式是svg格式，它是矢量图，它记录的图片的绘制方式，因此对矢量图进行放大和缩小不会产生锯齿和失真。它一般适合于用来制作一些网站logo或者图标之类的图片。

（7）第七种格式是webp格式，它是支持有损和无损两种压缩方式的使用直接色的点阵图。使用webp格式的最大的优点是，在相同质量的文件下，它拥有更小的文件体积。因此它非常适合于网络图片的传输，因为图片体积的减少，意味着请求时间的减小，这样会提高用户的体验。这是谷歌开发的一种新的图片格式，目前在兼容性上还不是太好。
```

详细资料可以参考：
[《图片格式那么多，哪种更适合你？》](https://www.cnblogs.com/xinzhao/p/5130410.html)

</details>

<b><details><summary>159.浏览器如何判断是否支持 webp 格式图片</summary></b>

参考答案：

```
（1）宽高判断法。通过创建image对象，将其src属性设置为webp格式的图片，然后在onload事件中获取图片的宽高，如
果能够获取，则说明浏览器支持webp格式图片。如果不能获取或者触发了onerror函数，那么就说明浏览器不支持webp格
式的图片。

（2）canvas判断方法。我们可以动态的创建一个canvas对象，通过canvas的toDataURL将设置为webp格式，然后判断
返回值中是否含有image/webp字段，如果包含则说明支持WebP，反之则不支持。
```

详细资料可以参考：
[《判断浏览器是否支持 WebP 图片》](https://blog.csdn.net/jesslu/article/details/82495061)
[《toDataURL()》](https://developer.mozilla.org/zh-CN/docs/Web/API/HTMLCanvasElement/toDataURL)

</details>

<b><details><summary>160.什么是 Cookie 隔离？（或者说：请求资源的时候不要让它带 cookie 怎么做）</summary></b>

参考答案：

```
网站向服务器请求的时候，会自动带上cookie这样增加表头信息量，使请求变慢。

如果静态文件都放在主域名下，那静态文件请求的时候都带有的cookie的数据提交给server的，非常浪费流量，所以不如隔离开
，静态资源放CDN。

因为cookie有域的限制，因此不能跨域提交请求，故使用非主要域名的时候，请求头中就不会带有cookie数据，这样可以降低请
求头的大小，降低请求时间，从而达到降低整体请求延时的目的。

同时这种方式不会将cookie传入WebServer，也减少了WebServer对cookie的处理分析环节，提高了webserver的
http请求的解析速度。
```

详细资料可以参考：
[《CDN 是什么？使用 CDN 有什么优势？》](https://www.zhihu.com/question/36514327?rf=37353035)

</details>

<b><details><summary>161.style 标签写在 body 后与 body 前有什么区别？</summary></b>

参考答案：

```
页面加载自上而下当然是先加载样式。写在body标签后由于浏览器以逐行方式对HTML文档进行解析，当解析到写在尾部的样式
表（外联或写在style标签）会导致浏览器停止之前的渲染，等待加载且解析样式表完成之后重新渲染，在windows的IE下可
能会出现FOUC现象（即样式失效导致的页面闪烁问题）
```

</details>

<b><details><summary>162.什么是 CSS 预处理器/后处理器？</summary></b>

参考答案：

```
CSS预处理器定义了一种新的语言，其基本思想是，用一种专门的编程语言，为CSS增加了一些编程的特性，将CSS作为目标生成
文件，然后开发者就只要使用这种语言进行编码工作。通俗的说，CSS预处理器用一种专门的编程语言，进行Web页面样式设计，然
后再编译成正常的CSS文件。

预处理器例如：LESS、Sass、Stylus，用来预编译Sass或less csssprite，增强了css代码的复用性，还有层级、mixin、
变量、循环、函数等，具有很方便的UI组件模块化开发能力，极大的提高工作效率。

CSS后处理器是对CSS进行处理，并最终生成CSS的预处理器，它属于广义上的CSS预处理器。我们很久以前就在用CSS后
处理器了，最典型的例子是CSS压缩工具（如clean-css），只不过以前没单独拿出来说过。还有最近比较火的Autoprefixer，
以CanIUse上的浏览器支持数据为基础，自动处理兼容性问题。

后处理器例如：PostCSS，通常被视为在完成的样式表中根据CSS规范处理CSS，让其更有效；目前最常做的是给CSS属性添加浏
览器私有前缀，实现跨浏览器兼容性的问题。
```

详细资料可以参考：
[《CSS 预处理器和后处理器》](https://blog.csdn.net/yushuangyushuang/article/details/79209752)

</details>

<b><details><summary>163.阐述一下 CSSSprites</summary></b>

参考答案：

```
将一个页面涉及到的所有图片都包含到一张大图中去，然后利用CSS的background-image，background-repeat，background
-position的组合进行背景定位。利用CSSSprites能很好地减少网页的http请求，从而很好的提高页面的性能；CSSSprites
能减少图片的字节。

优点：

减少HTTP请求数，极大地提高页面加载速度
增加图片信息重复度，提高压缩比，减少图片大小
更换风格方便，只需在一张或几张图片上修改颜色或样式即可实现

缺点：

图片合并麻烦
维护麻烦，修改一个图片可能需要重新布局整个图片，样式
```

</details>

<b><details><summary>164.使用 rem 布局的优缺点？</summary></b>

参考答案：

```
优点：
在屏幕分辨率千差万别的时代，只要将rem与屏幕分辨率关联起来就可以实现页面的整体缩放，使得在设备上的展现都统一起来了。
而且现在浏览器基本都已经支持rem了，兼容性也非常的好。

缺点：
（1）在奇葩的dpr设备上表现效果不太好，比如一些华为的高端机型用rem布局会出现错乱。
（2）使用iframe引用也会出现问题。
（3）rem在多屏幕尺寸适配上与当前两大平台的设计哲学不一致。即大屏的出现到底是为了看得又大又清楚，还是为了看的更多的问
题。
```

详细资料可以参考：
[《css3 的字体大小单位 rem 到底好在哪？》](https://www.zhihu.com/question/21504656)
[《VW:是时候放弃 REM 布局了》](https://www.jianshu.com/p/e8ae1c3861dc)
[《为什么设计稿是 750px》](https://blog.csdn.net/Honeymao/article/details/76795089)
[《使用 Flexible 实现手淘 H5 页面的终端适配》](https://github.com/amfe/article/issues/17)

</details>

<b><details><summary>165.几种常见的 CSS 布局</summary></b>

参考答案：

详细的资料可以参考：
[《几种常见的 CSS 布局》](https://juejin.im/post/5bbcd7ff5188255c80668028#heading-12)

</details>

<b><details><summary>166.画一条 0.5px 的线</summary></b>

参考答案：

```
采用meta viewport的方式

采用border-image的方式

采用transform:scale()的方式
```

详细资料可以参考：
[《怎么画一条 0.5px 的边（更新）》](https://juejin.im/post/5ab65f40f265da2384408a95)

</details>

<b><details><summary>167.transition 和 animation 的区别</summary></b>

参考答案：

```
transition关注的是CSS property的变化，property值和时间的关系是一个三次贝塞尔曲线。

animation作用于元素本身而不是样式属性，可以使用关键帧的概念，应该说可以实现更自由的动画效果。
```

详细资料可以参考：
[《CSSanimation 与 CSStransition 有何区别？》](https://www.zhihu.com/question/19749045)
[《CSS3Transition 和 Animation 区别及比较》](https://blog.csdn.net/cddcj/article/details/53582334)
[《CSS 动画简介》](http://www.ruanyifeng.com/blog/2014/02/css_transition_and_animation.html)
[《CSS 动画：animation、transition、transform、translate》](https://juejin.im/post/5b137e6e51882513ac201dfb)

</details>

<b><details><summary>168.什么是首选最小宽度？</summary></b>

参考答案：

```
“首选最小宽度”，指的是元素最适合的最小宽度。

东亚文字（如中文）最小宽度为每个汉字的宽度。

西方文字最小宽度由特定的连续的英文字符单元决定。并不是所有的英文字符都会组成连续单元，一般会终止于空格（普通空格）、短
横线、问号以及其他非英文字符等。

如果想让英文字符和中文一样，每一个字符都用最小宽度单元，可以试试使用CSS中的word-break:break-all。
```

</details>

<b><details><summary>169.为什么 height:100%会无效？</summary></b>

参考答案：

```
对于普通文档流中的元素，百分比高度值要想起作用，其父级必须有一个可以生效的高度值。

原因是如果包含块的高度没有显式指定（即高度由内容决定），并且该元素不是绝对定位，则计算值为auto，因为解释成了auto，
所以无法参与计算。

使用绝对定位的元素会有计算值，即使祖先元素的height计算为auto也是如此。
```

</details>

<b><details><summary>170.min-width/max-width 和 min-height/max-height 属性间的覆盖规则？</summary></b>

参考答案：

```
（1）max-width会覆盖width，即使width是行类样式或者设置了!important。

（2）min-width会覆盖max-width，此规则发生在min-width和max-width冲突的时候。
```

</details>

<b><details><summary>171.内联盒模型基本概念</summary></b>

参考答案：

```
（1）内容区域（content area）。内容区域指一种围绕文字看不见的盒子，其大小仅受字符本身特性控制，本质上是一个字符盒子
（character box）；但是有些元素，如图片这样的替换元素，其内容显然不是文字，不存在字符盒子之类的，因此，对于这些
元素，内容区域可以看成元素自身。

（2）内联盒子（inline box）。“内联盒子”不会让内容成块显示，而是排成一行，这里的“内联盒子”实际指的就是元素的“外在盒
子”，用来决定元素是内联还是块级。该盒子又可以细分为“内联盒子”和“匿名内联盒子”两类。

（3）行框盒子（line box），每一行就是一个“行框盒子”（实线框标注），每个“行框盒子”又是由一个一个“内联盒子”组成的。

（4）包含块（containing box），由一行一行的“行框盒子”组成。
```

</details>

<b><details><summary>172.什么是幽灵空白节点？</summary></b>

参考答案：

```
“幽灵空白节点”是内联盒模型中非常重要的一个概念，具体指的是：在HTML5文档声明中，内联元素的所有解析和渲染表现就如同
每个行框盒子的前面有一个“空白节点”一样。这个“空白节点”永远透明，不占据任何宽度，看不见也无法通过脚本获取，就好像幽灵
一样，但又确确实实地存在，表现如同文本节点一样，因此，我称之为“幽灵空白节点”。
```

</details>

<b><details><summary>173.什么是替换元素？</summary></b>

参考答案：

```
通过修改某个属性值呈现的内容就可以被替换的元素就称为“替换元素”。因此，<img>、<object>、<video>、<iframe>或者表
单元素<textarea>和<input>和<select>都是典型的替换元素。

替换元素除了内容可替换这一特性以外，还有以下一些特性。

（1）内容的外观不受页面上的CSS的影响。用专业的话讲就是在样式表现在CSS作用域之外。如何更改替换元素本身的外观需要
类似appearance属性，或者浏览器自身暴露的一些样式接口，

（2）有自己的尺寸。在Web中，很多替换元素在没有明确尺寸设定的情况下，其默认的尺寸（不包括边框）是300像素×150像
素，如<video>、<iframe>或者<canvas>等，也有少部分替换元素为0像素，如<img>图片，而表单元素的替换元素
的尺寸则和浏览器有关，没有明显的规律。

（3）在很多CSS属性上有自己的一套表现规则。比较具有代表性的就是vertical-align属性，对于替换元素和非替换元素，ve
rtical-align属性值的解释是不一样的。比方说vertical-align的默认值的baseline，很简单的属性值，基线之意，
被定义为字符x的下边缘，而替换元素的基线却被硬生生定义成了元素的下边缘。

（4）所有的替换元素都是内联水平元素，也就是替换元素和替换元素、替换元素和文字都是可以在一行显示的。但是，替换元素默认
的display值却是不一样的，有的是inline，有的是inline-block。
```

</details>

<b><details><summary>174.替换元素的计算规则？</summary></b>

参考答案：

```
替换元素的尺寸从内而外分为3类：固有尺寸、HTML尺寸和CSS尺寸。

（1）固有尺寸指的是替换内容原本的尺寸。例如，图片、视频作为一个独立文件存在的时候，都是有着自己的宽度和高度的。

（2）HTML尺寸只能通过HTML原生属性改变，这些HTML原生属性包括<img>的width和height属性、<input>的s
ize属性、<textarea>的cols和rows属性等。

（3）CSS尺寸特指可以通过CSS的width和height或者max-width/min-width和max-height/min-height设置的
尺寸，对应盒尺寸中的content box。

这3层结构的计算规则具体如下

（1）如果没有CSS尺寸和HTML尺寸，则使用固有尺寸作为最终的宽高。

（2）如果没有CSS尺寸，则使用HTML尺寸作为最终的宽高。

（3）如果有CSS尺寸，则最终尺寸由CSS属性决定。

（4）如果“固有尺寸”含有固有的宽高比例，同时仅设置了宽度或仅设置了高度，则元素依然按照固有的宽高比例显示。

（5）如果上面的条件都不符合，则最终宽度表现为300像素，高度为150像素。

（6）内联替换元素和块级替换元素使用上面同一套尺寸计算规则。
```

</details>

<b><details><summary>175.content 与替换元素的关系？</summary></b>

参考答案：

```
content属性生成的对象称为“匿名替换元素”。

（1）我们使用content生成的文本是无法选中、无法复制的，好像设置了user select:none声明一般，但是普通元素的文本
却可以被轻松选中。同时，content生成的文本无法被屏幕阅读设备读取，也无法被搜索引擎抓取，因此，千万不要自以为是
地把重要的文本信息使用content属性生成，因为这对可访问性和SEO都很不友好。

（2）content生成的内容不能左右:empty伪类。

（3）content动态生成值无法获取。
```

</details>

<b><details><summary>176.margin:auto 的填充规则？</summary></b>

参考答案：

```
margin的'auto'可不是摆设，是具有强烈的计算意味的关键字，用来计算元素对应方向应该获得的剩余间距大小。但是触发mar
gin:auto计算有一个前提条件，就是width或height为auto时，元素是具有对应方向的自动填充特性的。

（1）如果一侧定值，一侧auto，则auto为剩余空间大小。
（2）如果两侧均是auto，则平分剩余空间。
```

</details>

<b><details><summary>177.margin 无效的情形</summary></b>

参考答案：

```
（1）display计算值inline的非替换元素的垂直margin是无效的。对于内联替换元素，垂直margin有效，并且没有ma
rgin合并的问题。

（2）表格中的<tr>和<td>元素或者设置display计算值是table-cell或table-row的元素的margin都是无效的。

（3）绝对定位元素非定位方位的margin值“无效”。

（4）定高容器的子元素的margin-bottom或者宽度定死的子元素的margin-right的定位“失效”。
```

</details>

<b><details><summary>178.border 的特殊性？</summary></b>

参考答案：

```
（1）border-width却不支持百分比。

（2）border-style的默认值是none，有一部分人可能会误以为是solid。这也是单纯设置border-width或border-col
or没有边框显示的原因。

（3）border-style:double的表现规则：双线宽度永远相等，中间间隔±1。

（4）border-color默认颜色就是color色值。

（5）默认background背景图片是相对于padding box定位的。
```

</details>

<b><details><summary>179.什么是基线和 x-height？</summary></b>

参考答案：

```
字母x的下边缘（线）就是我们的基线。

x-height指的就是小写字母x的高度，术语描述就是基线和等分线（meanline）（也称作中线，midline）之间的距离。在C
SS世界中，middle指的是基线往上1/2x-height高度。我们可以近似理解为字母x交叉点那个位置。

ex是CSS中的一个相对单位，指的是小写字母x的高度，没错，就是指x-height。ex的价值就在其副业上不受字体和字号影
响的内联元素的垂直居中对齐效果。内联元素默认是基线对齐的，而基线就是x的底部，而1ex就是一个x的高度。
```

</details>

<b><details><summary>180.line-height 的特殊性？</summary></b>

参考答案：

```
（1）对于非替换元素的纯内联元素，其可视高度完全由line-height决定。对于文本这样的纯内联元素，line-height就是高
度计算的基石，用专业说法就是指定了用来计算行框盒子高度的基础高度。

（2）内联元素的高度由固定高度和不固定高度组成，这个不固定的部分就是这里的“行距”。换句话说，line-height之所以起作
用，就是通过改变“行距”来实现的。在CSS中，“行距”分散在当前文字的上方和下方，也就是即使是第一行文字，其上方也是
有“行距”的，只不过这个“行距”的高度仅仅是完整“行距”高度的一半，因此，也被称为“半行距”。

（3）行距=line-height-font-size。

（4）border以及line-height等传统CSS属性并没有小数像素的概念。如果标注的是文字上边距，则向下取整；如果是文字下
边距，则向上取整。

（5）对于纯文本元素，line-height直接决定了最终的高度。但是，如果同时有替换元素，则line-height只能决定最小高度。

（6）对于块级元素，line-height对其本身是没有任何作用的，我们平时改变line-height，块级元素的高度跟着变化实际上是
通过改变块级元素里面内联级别元素占据的高度实现的。

（7）line-height的默认值是normal，还支持数值、百分比值以及长度值。为数值类型时，其最终的计算值是和当前font-si
ze相乘后的值。为百分比值时，其最终的计算值是和当前font-size相乘后的值。为长度值时原意不变。

（8）如果使用数值作为line-height的属性值，那么所有的子元素继承的都是这个值；但是，如果使用百分比值或者长度值作为
属性值，那么所有的子元素继承的是最终的计算值。

（9）无论内联元素line-height如何设置，最终父级元素的高度都是由数值大的那个line-height决定的。

（10）只要有“内联盒子”在，就一定会有“行框盒子”，就是每一行内联元素外面包裹的一层看不见的盒子。然后，重点来了，在每个
“行框盒子”前面有一个宽度为0的具有该元素的字体和行高属性的看不见的“幽灵空白节点”。
```

</details>

<b><details><summary>181.vertical-align 的特殊性？</summary></b>

参考答案：

```
（1）vertical-align的默认值是baseline，即基线对齐，而基线的定义是字母x的下边缘。因此，内联元素默认都是沿着字
母x的下边缘对齐的。对于图片等替换元素，往往使用元素本身的下边缘作为基线。：一个inline-block元素，如果里面
没有内联元素，或者overflow不是visible，则该元素的基线就是其margin底边缘；否则其基线就是元素里面最后一行
内联元素的基线。

（2）vertical-align:top就是垂直上边缘对齐，如果是内联元素，则和这一行位置最高的内联元素的顶部对齐；如果display
计算值是table-cell的元素，我们不妨脑补成<td>元素，则和<tr>元素上边缘对齐。

（3）vertical-align:middle是中间对齐，对于内联元素，元素的垂直中心点和行框盒子基线往上1/2x-height处对齐。对
于table-cell元素，单元格填充盒子相对于外面的表格行居中对齐。

（4）vertical-align支持数值属性，根据数值的不同，相对于基线往上或往下偏移，如果是负值，往下偏移，如果是正值，往上
偏移。

（5）vertical-align属性的百分比值则是相对于line-height的计算值计算的。

（6）vertical-align起作用是有前提条件的，这个前提条件就是：只能应用于内联元素以及display值为table-cell的元
素。

（7）table-cell元素设置vertical-align垂直对齐的是子元素，但是其作用的并不是子元素，而是table-cell元素自身。
```

</details>

<b><details><summary>182.overflow 的特殊性？</summary></b>

参考答案：

```
（1）一个设置了overflow:hidden声明的元素，假设同时存在border属性和padding属性，则当子元素内容超出容器宽度
高度限制的时候，剪裁的边界是border box的内边缘，而非padding box的内边缘。

（2）HTML中有两个标签是默认可以产生滚动条的，一个是根元素<html>，另一个是文本域<textarea>。

（3）滚动条会占用容器的可用宽度或高度。

（4）元素设置了overflow:hidden声明，里面内容高度溢出的时候，滚动依然存在，仅仅滚动条不存在！
```

</details>

<b><details><summary>183.无依赖绝对定位是什么？</summary></b>

参考答案：

```
没有设置left/top/right/bottom属性值的绝对定位称为“无依赖绝对定位”。

无依赖绝对定位其定位的位置和没有设置position:absolute时候的位置相关。
```

</details>

<b><details><summary>184.absolute 与 overflow 的关系？</summary></b>

参考答案：

```
（1）如果overflow不是定位元素，同时绝对定位元素和overflow容器之间也没有定位元素，则overflow无法对absolute
元素进行剪裁。

（2）如果overflow的属性值不是hidden而是auto或者scroll，即使绝对定位元素高宽比overflow元素高宽还要大，也
都不会出现滚动条。

（3）overflow元素自身transform的时候，Chrome和Opera浏览器下的overflow剪裁是无效的。
```

</details>

<b><details><summary>185.clip 裁剪是什么？</summary></b>

参考答案：

```
所谓“可访问性隐藏”，指的是虽然内容肉眼看不见，但是其他辅助设备却能够进行识别和访问的隐藏。

clip剪裁被我称为“最佳可访问性隐藏”的另外一个原因就是，它具有更强的普遍适应性，任何元素、任何场景都可以无障碍使用。
```

</details>

<b><details><summary>186.relative 的特殊性？</summary></b>

参考答案：

```
（1）相对定位元素的left/top/right/bottom的百分比值是相对于包含块计算的，而不是自身。注意，虽然定位位移是相对自身，但是百分比值的计算值不是。

（2）top和bottom这两个垂直方向的百分比值计算跟height的百分比值是一样的，都是相对高度计算的。同时，如果包含块的高度是auto，那么计算值是0，偏移无效，也就是说，如果父元素没有设定高度或者不是“格式化高度”，那么relative类似top:20%的代码等同于top:0。

（3）当相对定位元素同时应用对立方向定位值的时候，也就是top/bottom和left/right同时使用的时候，只有一个方向的定位属性会起作用。而谁起作用则是与文档流的顺序有关的，默认的文档流是自上而下、从左往右，因此top/bottom同时使用的时候，bottom失效；left/right同时使用的时候，right失效。
```

</details>

<b><details><summary>187.什么是层叠上下文？</summary></b>

参考答案：

```
层叠上下文，英文称作stacking context，是HTML中的一个三维的概念。如果一个元素含有层叠上下文，我们可以理解为这个元
素在z轴上就“高人一等”。

层叠上下文元素有如下特性：

（1）层叠上下文的层叠水平要比普通元素高（原因后面会说明）。
（2）层叠上下文可以阻断元素的混合模式。
（3）层叠上下文可以嵌套，内部层叠上下文及其所有子元素均受制于外部的“层叠上下文”。
（4）每个层叠上下文和兄弟元素独立，也就是说，当进行层叠变化或渲染的时候，只需要考虑后代元素。
（5）每个层叠上下文是自成体系的，当元素发生层叠的时候，整个元素被认为是在父层叠上下文的层叠顺序中。


层叠上下文的创建：

（1）页面根元素天生具有层叠上下文，称为根层叠上下文。根层叠上下文指的是页面根元素，可以看成是<html>元素。因此，页面中所有的元素一定处于至少一个“层叠结界”中。

（2）对于position值为relative/absolute以及Firefox/IE浏览器（不包括Chrome浏览器）下含有position:fixed声明的定位元素，当其z-index值不是auto的时候，会创建层叠上下文。Chrome等WebKit内核浏览器下，position:fixed元素天然层叠上下文元素，无须z-index为数值。根据我的测试，目前IE和Firefox仍是老套路。

（3）其他一些CSS3属性，比如元素的opacity值不是1。
```

</details>

<b><details><summary>188.什么是层叠水平？</summary></b>

参考答案：

```
层叠水平，英文称作stacking level，决定了同一个层叠上下文中元素在z轴上的显示顺序。

显而易见，所有的元素都有层叠水平，包括层叠上下文元素，也包括普通元素。然而，对普通元素的层叠水平探讨只局限在当前层叠上
下文元素中。
```

</details>

<b><details><summary>189.元素的层叠顺序？</summary></b>

参考答案：

层叠顺序，英文称作 stacking order，表示元素发生层叠时有着特定的垂直显示顺序。

![层叠顺序](https://cavszhouyou-1254093697.cos.ap-chongqing.myqcloud.com/note-15.png)

</details>

<b><details><summary>190.层叠准则？</summary></b>

参考答案：

```
（1）谁大谁上：当具有明显的层叠水平标识的时候，如生效的z-index属性值，在同一个层叠上下文领域，层叠水平值大的那一个覆盖小的那一个。

（2）后来居上：当元素的层叠水平一致、层叠顺序相同的时候，在DOM流中处于后面的元素会覆盖前面的元素。
```

</details>

<b><details><summary>191.font-weight 的特殊性？</summary></b>

参考答案：

```
如果使用数值作为font-weight属性值，必须是100～900的整百数。因为这里的数值仅仅是外表长得像数值，实际上是一个具有特定含义的关键字，并且这里的数值关键字和字母关键字之间是有对应关系的。
```

</details>

<b><details><summary>192.text-indent 的特殊性？</summary></b>

参考答案：

```
（1）text-indent仅对第一行内联盒子内容有效。

（2）非替换元素以外的display计算值为inline的内联元素设置text-indent值无效，如果计算值inline-block/inli
ne-table则会生效。

（3）<input>标签按钮text-indent值无效。

（4）<button>标签按钮text-indent值有效。

（5）text-indent的百分比值是相对于当前元素的“包含块”计算的，而不是当前元素。
```

</details>

<b><details><summary>193.letter-spacing 与字符间距？</summary></b>

参考答案：

```
letter-spacing可以用来控制字符之间的间距，这里说的“字符”包括英文字母、汉字以及空格等。

letter-spacing具有以下一些特性。

（1）继承性。
（2）默认值是normal而不是0。虽然说正常情况下，normal的计算值就是0，但两者还是有差别的，在有些场景下，letter-spacing会调整normal的计算值以实现更好的版面布局。
（3）支持负值，且值足够大的时候，会让字符形成重叠，甚至反向排列。
（4）和text-indent属性一样，无论值多大或多小，第一行一定会保留至少一个字符。
（5）支持小数值，即使0.1px也是支持的。
（6）暂不支持百分比值。
```

</details>

<b><details><summary>194.word-spacing 与单词间距？</summary></b>

参考答案：

```
letter-spacing作用于所有字符，但word-spacing仅作用于空格字符。换句话说，word-spacing的作用就是增加空格的间隙
宽度。
```

</details>

<b><details><summary>195.white-space 与换行和空格的控制？</summary></b>

参考答案：

```
white-space属性声明了如何处理元素内的空白字符，这类空白字符包括Space（空格）键、Enter（回车）键、Tab（制表符）
键产生的空白。因此，white-space可以决定图文内容是否在一行显示（回车空格是否生效），是否显示大段连续空白（空格是否
生效）等。

其属性值包括下面这些。
•normal：合并空白字符和换行符。
•pre：空白字符不合并，并且内容只在有换行符的地方换行。
•nowrap：该值和normal一样会合并空白字符，但不允许文本环绕。
•pre-wrap：空白字符不合并，并且内容只在有换行符的地方换行，同时允许文本环绕。
•pre-line：合并空白字符，但只在有换行符的地方换行，允许文本环绕。
```

</details>

<b><details><summary>196.隐藏元素的 background-image 到底加不加载？</summary></b>

参考答案：

相关知识点：

```
根据测试，一个元素如果display计算值为none，在IE浏览器下（IE8～IE11，更高版本不确定）依然会发送图片请求，Fire
fox浏览器不会，至于Chrome和Safari浏览器则似乎更加智能一点：如果隐藏元素同时又设置了background-image，则图片
依然会去加载；如果是父元素的display计算值为none，则背景图不会请求，此时浏览器或许放心地认为这个背景图暂时是不会使
用的。

如果不是background-image，而是<img>元素，则设置display:none在所有浏览器下依旧都会请求图片资源。

还需要注意的是如果设置的样式没有对应的元素，则background-image也不会加载。hover情况下的background-image，在触
发时加载。
```

回答：

-（1）元素的背景图片

-元素本身设置 display:none，会请求图片 -父级元素设置 display:none，不会请求图片 -样式没有元素使用，不会请求
-:hover 样式下，触发时请求

-（2）img 标签图片任何情况下都会请求图片

详细资料可以参考：
[《CSS 控制前端图片 HTTP 请求的各种情况示例》](https://www.jb51.net/css/469033.html)

</details>

<b><details><summary>197.如何实现单行／多行文本溢出的省略（...）？</summary></b>

参考答案：

```css
/*单行文本溢出*/
p {
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}

/*多行文本溢出*/
p {
  position: relative;
  line-height: 1.5em;
  /*高度为需要显示的行数*行高，比如这里我们显示两行，则为3*/
  height: 3em;
  overflow: hidden;
}

p:after {
  content: '...';
  position: absolute;
  bottom: 0;
  right: 0;
  background-color: #fff;
}
```

详细资料可以参考：
[《【CSS/JS】如何实现单行／多行文本溢出的省略》](https://zhuanlan.zhihu.com/p/30707916)
[《CSS 多行文本溢出省略显示》](https://juejin.im/entry/587f453e1b69e60058555a5f)

</details>

<b><details><summary>198.常见的元素隐藏方式？</summary></b>

参考答案：

-（1）使用 display:none;隐藏元素，渲染树不会包含该渲染对象，因此该元素不会在页面中占据位置，也不会响应绑定的监听事件。

-（2）使用 visibility:hidden;隐藏元素。元素在页面中仍占据空间，但是不会响应绑定的监听事件。

-（3）使用 opacity:0;将元素的透明度设置为 0，以此来实现元素的隐藏。元素在页面中仍然占据空间，并且能够响应元素绑定的监听事件。

-（4）通过使用绝对定位将元素移除可视区域内，以此来实现元素的隐藏。

-（5）通过 z-index 负值，来使其他元素遮盖住该元素，以此来实现隐藏。

-（6）通过 clip/clip-path 元素裁剪的方法来实现元素的隐藏，这种方法下，元素仍在页面中占据位置，但是不会响应绑定的监听事件。

-（7）通过 transform:scale(0,0)来将元素缩放为 0，以此来实现元素的隐藏。这种方法下，元素仍在页面中占据位置，但是不会响应绑定的监听事件。

详细资料可以参考：
[《CSS 隐藏元素的八种方法》](https://juejin.im/post/584b645a128fe10058a0d625#heading-2)

</details>

<b><details><summary>199.css 实现上下固定中间自适应布局？</summary></b>

参考答案：

```css
利用绝对定位实现body {
  padding: 0;
  margin: 0;
}

.header {
  position: absolute;
  top: 0;
  width: 100%;
  height: 100px;
  background: red;
}

.container {
  position: absolute;
  top: 100px;
  bottom: 100px;
  width: 100%;
  background: green;
}

.footer {
  position: absolute;
  bottom: 0;
  height: 100px;
  width: 100%;
  background: red;
}

利用flex布局实现html,
body {
  height: 100%;
}

body {
  display: flex;
  padding: 0;
  margin: 0;
  flex-direction: column;
}

.header {
  height: 100px;
  background: red;
}

.container {
  flex-grow: 1;
  background: green;
}

.footer {
  height: 100px;
  background: red;
}
```

详细资料可以参考：
[《css 实现上下固定中间自适应布局》](https://www.jianshu.com/p/30bc9751e3e8)

</details>

<b><details><summary>200.css 两栏布局的实现？</summary></b>

参考答案：

相关资料：

```css
/*两栏布局一般指的是页面中一共两栏，左边固定，右边自适应的布局，一共有四种实现的方式。*/
/*以左边宽度固定为200px为例*/

/*（1）利用浮动，将左边元素宽度设置为200px，并且设置向左浮动。将右边元素的margin-left设置为200px，宽度设置为auto（默认为auto，撑满整个父元素）。*/
.outer {
  height: 100px;
}

.left {
  float: left;

  height: 100px;
  width: 200px;

  background: tomato;
}

.right {
  margin-left: 200px;

  width: auto;
  height: 100px;

  background: gold;
}

/*（2）第二种是利用flex布局，将左边元素的放大和缩小比例设置为0，基础大小设置为200px。将右边的元素的放大比例设置为1，缩小比例设置为1，基础大小设置为auto。*/
.outer {
  display: flex;

  height: 100px;
}

.left {
  flex-shrink: 0;
  flex-grow: 0;
  flex-basis: 200px;

  background: tomato;
}

.right {
  flex: auto;
  /*11auto*/

  background: gold;
}

/*（3）第三种是利用绝对定位布局的方式，将父级元素设置相对定位。左边元素设置为absolute定位，并且宽度设置为
200px。将右边元素的margin-left的值设置为200px。*/
.outer {
  position: relative;

  height: 100px;
}

.left {
  position: absolute;

  width: 200px;
  height: 100px;

  background: tomato;
}

.right {
  margin-left: 200px;
  height: 100px;

  background: gold;
}

/*（4）第四种还是利用绝对定位的方式，将父级元素设置为相对定位。左边元素宽度设置为200px，右边元素设置为绝对定位，左边定位为200px，其余方向定位为0。*/
.outer {
  position: relative;

  height: 100px;
}

.left {
  width: 200px;
  height: 100px;

  background: tomato;
}

.right {
  position: absolute;

  top: 0;
  right: 0;
  bottom: 0;
  left: 200px;

  background: gold;
}
```

[《两栏布局 demo 展示》](http://cavszhouyou.top/Demo-Display/TwoColumnLayout/index.html)

回答：

两栏布局一般指的是页面中一共两栏，左边固定，右边自适应的布局，一共有四种实现的方式。

以左边宽度固定为 200px 为例

-（1）利用浮动，将左边元素宽度设置为 200px，并且设置向左浮动。将右边元素的 margin-left 设置为 200px，宽度设置为 auto（默认为 auto，撑满整个父元素）。

-（2）第二种是利用 flex 布局，将左边元素的放大和缩小比例设置为 0，基础大小设置为 200px。将右边的元素的放大比例设置为 1，缩小比例设置为 1，基础大小设置为 auto。

-（3）第三种是利用绝对定位布局的方式，将父级元素设置相对定位。左边元素设置为 absolute 定位，并且宽度设置为 200px。将右边元素的 margin-left 的值设置为 200px。

-（4）第四种还是利用绝对定位的方式，将父级元素设置为相对定位。左边元素宽度设置为 200px，右边元素设置为绝对定位，左边定位为 200px，其余方向定位为 0。

</details>

<b><details><summary>201.css 三栏布局的实现？</summary></b>

参考答案：

相关资料：

```css
/*三栏布局一般指的是页面中一共有三栏，左右两栏宽度固定，中间自适应的布局，一共有五种实现方式。

这里以左边宽度固定为100px，右边宽度固定为200px为例。*/

/*（1）利用绝对定位的方式，左右两栏设置为绝对定位，中间设置对应方向大小的margin的值。*/
.outer {
  position: relative;
  height: 100px;
}

.left {
  position: absolute;

  width: 100px;
  height: 100px;
  background: tomato;
}

.right {
  position: absolute;
  top: 0;
  right: 0;

  width: 200px;
  height: 100px;
  background: gold;
}

.center {
  margin-left: 100px;
  margin-right: 200px;
  height: 100px;
  background: lightgreen;
}

/*（2）利用flex布局的方式，左右两栏的放大和缩小比例都设置为0，基础大小设置为固定的大小，中间一栏设置为auto*/
.outer {
  display: flex;
  height: 100px;
}

.left {
  flex: 00100px;
  background: tomato;
}

.right {
  flex: 00200px;
  background: gold;
}

.center {
  flex: auto;
  background: lightgreen;
}

/*（3）利用浮动的方式，左右两栏设置固定大小，并设置对应方向的浮动。中间一栏设置左右两个方向的margin值，注意这种方式，中间一栏必须放到最后。*/
.outer {
  height: 100px;
}

.left {
  float: left;
  width: 100px;
  height: 100px;
  background: tomato;
}

.right {
  float: right;
  width: 200px;
  height: 100px;
  background: gold;
}

.center {
  height: 100px;
  margin-left: 100px;
  margin-right: 200px;
  background: lightgreen;
}

/*（4）圣杯布局，利用浮动和负边距来实现。父级元素设置左右的 padding，三列均设置向左浮动，中间一列放在最前面，宽度设置为父级元素的宽度，因此后面两列都被挤到了下一行，通过设置 margin 负值将其移动到上一行，再利用相对定位，定位到两边。*/
.outer {
  height: 100px;
  padding-left: 100px;
  padding-right: 200px;
}

.left {
  position: relative;
  left: -100px;

  float: left;
  margin-left: -100%;

  width: 100px;
  height: 100px;
  background: tomato;
}

.right {
  position: relative;
  left: 200px;

  float: right;
  margin-left: -200px;

  width: 200px;
  height: 100px;
  background: gold;
}

.center {
  float: left;

  width: 100%;
  height: 100px;
  background: lightgreen;
}

/*（5）双飞翼布局，双飞翼布局相对于圣杯布局来说，左右位置的保留是通过中间列的 margin 值来实现的，而不是通过父元
素的 padding 来实现的。本质上来说，也是通过浮动和外边距负值来实现的。*/

.outer {
  height: 100px;
}

.left {
  float: left;
  margin-left: -100%;

  width: 100px;
  height: 100px;
  background: tomato;
}

.right {
  float: left;
  margin-left: -200px;

  width: 200px;
  height: 100px;
  background: gold;
}

.wrapper {
  float: left;

  width: 100%;
  height: 100px;
  background: lightgreen;
}

.center {
  margin-left: 100px;
  margin-right: 200px;
  height: 100px;
}
```

[《三栏布局 demo 展示》](http://cavszhouyou.top/Demo-Display/ThreeColumnLayout/index.html)

回答：

```
三栏布局一般指的是页面中一共有三栏，左右两栏宽度固定，中间自适应的布局，一共有五种实现方式。

这里以左边宽度固定为100px，右边宽度固定为200px为例。

（1）利用绝对定位的方式，左右两栏设置为绝对定位，中间设置对应方向大小的margin的值。

（2）利用flex布局的方式，左右两栏的放大和缩小比例都设置为0，基础大小设置为固定的大小，中间一栏设置为auto。

（3）利用浮动的方式，左右两栏设置固定大小，并设置对应方向的浮动。中间一栏设置左右两个方向的margin值，注意这种方式，中间一栏必须放到最后。

（4）圣杯布局，利用浮动和负边距来实现。父级元素设置左右的padding，三列均设置向左浮动，中间一列放在最前面，宽度设置为父级元素的宽度，因此后面两列都被挤到了下一行，通过设置margin负值将其移动到上一行，再利用相对定位，定位到两边。圣杯布局中间列的宽度不能小于两边任意列的宽度，而双飞翼布局则不存在这个问题。

（5）双飞翼布局，双飞翼布局相对于圣杯布局来说，左右位置的保留是通过中间列的margin值来实现的，而不是通过父元素的padding来实现的。本质上来说，也是通过浮动和外边距负值来实现的。
```

</details>

<b><details><summary>202.实现一个宽高自适应的正方形</summary></b>

参考答案：

```css
/*1.第一种方式是利用vw来实现*/
.square {
  width: 10%;
  height: 10vw;
  background: tomato;
}

/*2.第二种方式是利用元素的margin/padding百分比是相对父元素width的性质来实现*/
.square {
  width: 20%;
  height: 0;
  padding-top: 20%;
  background: orange;
}

/*3.第三种方式是利用子元素的margin-top的值来实现的*/
.square {
  width: 30%;
  overflow: hidden;
  background: yellow;
}

.square::after {
  content: '';
  display: block;
  margin-top: 100%;
}
```

[《自适应正方形 demo 展示》](http://cavszhouyou.top/Demo-Display/AdaptiveSquare/index.html)

</details>

<b><details><summary>203.实现一个三角形</summary></b>

参考答案：

```css
/*三角形的实现原理是利用了元素边框连接处的等分原理。*/
.triangle {
  width: 0;
  height: 0;
  border-width: 100px;
  border-style: solid;
  border-color: tomatotransparenttransparenttransparent;
}
```

[《三角形 demo 展示》](http://cavszhouyou.top/Demo-Display/Triangle/index.html)

</details>

<b><details><summary>204.一个自适应矩形，水平垂直居中，且宽高比为 2:1</summary></b>

参考答案：

```css
/*实现原理参考自适应正方形和水平居中方式*/
.box {
  position: absolute;
  top: 0;
  right: 0;
  left: 0;
  bottom: 0;
  margin: auto;

  width: 10%;
  height: 0;
  padding-top: 20%;
  background: tomato;
}
```

</details>

<b><details><summary>205.你知道 CSS 中不同属性设置为百分比%时对应的计算基准？</summary></b>

参考答案：

```
公式：当前元素某CSS属性值 = 基准 * 对应的百分比
元素的 position 为 relative 和 absolute 时，top和bottom、left和right基准分别为包含块的 height、width
元素的 position 为 fixed 时，top和bottom、left和right基准分别为初始包含块（也就是视口）的 height、width，移动设备较为复杂，基准为 Layout viewport 的 height、width
元素的 height 和 width 设置为百分比时，基准分别为包含块的 height 和 width
元素的 margin 和 padding 设置为百分比时，基准为包含块的 width（易错）
元素的 border-width，不支持百分比
元素的 text-indent，基准为包含块的 width

元素的 border-radius，基准为分别为自身的height、width
元素的 background-size，基准为分别为自身的height、width
元素的 translateX、translateY，基准为分别为自身的height、width
元素的 line-height，基准为自身的 font-size

元素的 font-size，基准为父元素字体
```
</details>

<b><details><summary>206.::before 和:after 中双冒号和单冒号有什么区别？解释一下这 2 个伪元素的作用。</summary></b>

参考答案：

相关知识点：

```
单冒号（:）用于CSS3伪类，双冒号（::）用于CSS3伪元素。（伪元素由双冒号和伪元素名称组成）
双冒号是在当前规范中引入的，用于区分伪类和伪元素。不过浏览器需要同时支持旧的已经存在的伪元素写法，
比如:first-line、:first-letter、:before、:after等，
而新的在CSS3中引入的伪元素则不允许再支持旧的单冒号的写法。

想让插入的内容出现在其它内容前，使用::before，否者，使用::after；
在代码顺序上，::after生成的内容也比::before生成的内容靠后。
如果按堆栈视角，::after生成的内容会在::before生成的内容之上。
```

回答：

```
在css3中使用单冒号来表示伪类，用双冒号来表示伪元素。但是为了兼容已有的伪元素的写法，在一些浏览器中也可以使用单冒号
来表示伪元素。

伪类一般匹配的是元素的一些特殊状态，如hover、link等，而伪元素一般匹配的特殊的位置，比如after、before等。
```

</details>

<b><details><summary>207.伪类与伪元素的区别</summary></b>

参考答案：

```
css引入伪类和伪元素概念是为了格式化文档树以外的信息。也就是说，伪类和伪元素是用来修饰不在文档树中的部分，比如，一句
话中的第一个字母，或者是列表中的第一个元素。

伪类用于当已有的元素处于某个状态时，为其添加对应的样式，这个状态是根据用户行为而动态变化的。比如说，当用户悬停在指定的
元素时，我们可以通过:hover来描述这个元素的状态。

伪元素用于创建一些不在文档树中的元素，并为其添加样式。它们允许我们为元素的某些部分设置样式。比如说，我们可以通过::be
fore来在一个元素前增加一些文本，并为这些文本添加样式。虽然用户可以看到这些文本，但是这些文本实际上不在文档树中。

有时你会发现伪元素使用了两个冒号（::）而不是一个冒号（:）。这是CSS3的一部分，并尝试区分伪类和伪元素。大多数浏览
器都支持这两个值。按照规则应该使用（::）而不是（:），从而区分伪类和伪元素。但是，由于在旧版本的W3C规范并未对此进行
特别区分，因此目前绝大多数的浏览器都支持使用这两种方式表示伪元素。
```

详细资料可以参考：
[《总结伪类与伪元素》](http://www.alloyteam.com/2016/05/summary-of-pseudo-classes-and-pseudo-elements/)

</details>

<b><details><summary>208.CSS 中哪些属性可以继承？</summary></b>

参考答案：

相关资料：

```
每个CSS属性定义的概述都指出了这个属性是默认继承的，还是默认不继承的。这决定了当你没有为元素的属性指定值时该如何计算值。

当元素的一个继承属性没有指定值时，则取父元素的同属性的计算值。只有文档根元素取该属性的概述中给定的初始值（这里的意思应该是在该属性本身的定义中的默认值）。

当元素的一个非继承属性（在Mozilla code里有时称之为reset property）没有指定值时，则取属性的初始值initial value（该值在该属性的概述里被指定）。

有继承性的属性：

（1）字体系列属性
font、font-family、font-weight、font-size、font-style、font-variant、font-stretch、font-size-adjust

（2）文本系列属性
text-indent、text-align、text-shadow、line-height、word-spacing、letter-spacing、text-transform、direction、color

（3）表格布局属性
caption-side border-collapse empty-cells

（4）列表属性
list-style-type、list-style-image、list-style-position、list-style

（5）光标属性
cursor

（6）元素可见性
visibility

（7）还有一些不常用的；speak，page，设置嵌套引用的引号类型quotes等属性


注意：当一个属性不是继承属性时，可以使用inherit关键字指定一个属性应从父元素继承它的值，inherit关键字用于显式地
指定继承性，可用于任何继承性/非继承性属性。
```

回答：

```
每一个属性在定义中都给出了这个属性是否具有继承性，一个具有继承性的属性会在没有指定值的时候，会使用父元素的同属性的值来作为自己的值。

一般具有继承性的属性有，字体相关的属性，font-size和font-weight等。文本相关的属性，color和text-align等。
表格的一些布局属性、列表属性如list-style等。还有光标属性cursor、元素可见性visibility。

当一个属性不是继承属性的时候，我们也可以通过将它的值设置为inherit来使它从父元素那获取同名的属性值来继承。
```

详细的资料可以参考：
[《继承属性》](https://developer.mozilla.org/zh-CN/docs/Web/CSS/inheritance)
[《CSS 有哪些属性可以继承？》](https://www.jianshu.com/p/34044e3c9317)

</details>

<b><details><summary>209.png-8和png-24有什么区别？</summary></b>

参考答案：

```
1、“PNG8”是指8位索引色位图，“PNG24”是24位索引色位图；

2、png8：每一张“png8”图像，都最多只能展示256种颜色，所以“png8”格式更适合那些颜色比较单一的图像，例如纯色、logo、图标等；因为颜色数量少，所以图片的体积也会更小；

png24：每一张“png24”图像，可展示的颜色就远远多于“png8”了，最多可展示的颜色数量多大1600万；所以“png24”所展示的图片颜色会更丰富，图片的清晰度也会更好，图片质量更高，当然图片的大小也会相应增加，所以“png24”的图片比较适合像摄影作品之类颜色比较丰富的图片。
```

</details>

<b><details><summary></summary></b>

参考答案：

</details>

<b><details><summary></summary></b>

参考答案：

</details>