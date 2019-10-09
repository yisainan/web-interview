# [返回主页](https://github.com/yisainan/web-interview/blob/master/README.md)

<b><details><summary>1.说下 jQuery/Zepto 中的 on 方法有哪些参数，分别代表什么意思？</summary></b>

答案：

[参与互动](https://github.com/yisainan/web-interview/issues/347)

</details>

<b><details><summary>2.谈一下 Jquery 中的 bind(),live(),delegate(),on()的区别？</summary></b>

答案：

- bind： 绑定事件，对新添加的事件不起作用，方法用于将一个处理程序附加到每个匹配元素的事件上并返回 jQuery 对象。
- live： 方法将一个事件处理程序附加到与当前选择器匹配的所有元素（包含现有的或将来添加的）的指定事件上并返回 jQuery 对象。
- delegate： 方法基于一组特定的根元素将处理程序附加到匹配选择器的所有元素（现有的或将来的）的一个或多个事件上。

[参与互动](https://github.com/yisainan/web-interview/issues/348)

</details>

<b><details><summary>3.jQuery 的队列是如何实现的？队列可以用在哪些地方？</summary></b>

答案：

[参与互动](https://github.com/yisainan/web-interview/issues/349)

</details>

<b><details><summary>4.jquery.extend 与 jquery.fn.extend 的区别？</summary></b>

答案：

[参与互动](https://github.com/yisainan/web-interview/issues/350)

</details>

<b><details><summary>5.jQuery 的属性拷贝(extend)的实现原理是什么，如何实现深拷贝？</summary></b>

答案：

[参与互动](https://github.com/yisainan/web-interview/issues/351)

</details>

<b><details><summary>6.jquery 中如何将数组转化为 json 字符串，然后再转化回来？</summary></b>

答案：

[参与互动](https://github.com/yisainan/web-interview/issues/352)

</details>

<b><details><summary>7.jQuery.fn 的 init 方法返回的 this 指的是什么对象？为什么要返回 this？</summary></b>

答案：

[参与互动](https://github.com/yisainan/web-interview/issues/353)

</details>

<b><details><summary>8.jQuery 与 jQuery UI、jQuery Mobile 区别？</summary></b>

答案：

[参与互动](https://github.com/yisainan/web-interview/issues/354)

</details>

<b><details><summary>9.jQuery 的 slideUp 动画 ，如果目标元素是被外部事件驱动, 当鼠标快速地连续触发外部元素事件, 动画会滞后的反复执行，该如何处理呢?</summary></b>

答案：

[参与互动](https://github.com/yisainan/web-interview/issues/355)

</details>

<b><details><summary>10.你觉得 jQuery 源码有哪些写的好的地方</summary></b>

答案：

[参与互动](https://github.com/yisainan/web-interview/issues/356)

</details>

<b><details><summary>11.你觉得 zepto 源码有哪些写的好的地方</summary></b>

答案：

[参与互动](https://github.com/yisainan/web-interview/issues/357)

</details>

<b><details><summary>12.jQuery 的实现原理和核心？</summary></b>

答案：

1、jQuery 的实现原理

```js
var jQuery = function(selector, context) {
  return new jQuery.fn.init(selector, context);
};
```

1)jQuery 采用的是构造函数模式进行开发的,jQuery 是一个类

2)上面说的常用的方法(CSS、属性、筛选、事件、动画、文档处理)都是定义在 jQuery.prototype 上的 ->只有 jQuery 的实例才能使用这些方法

2、选择器/筛选

1)我们的选择器其实就是创造 jQuery 类的一个实例 ->获取页面中元素用的 jQuery(); -> \$()

\$()就是 jQuery 的选择器,就是创建 jQuery 这个类的一个实例

2)执行的时候需要传递两个参数

```
selector -> 选择器的类型 一般都是string类型
context -> 获取的上下文  第二个参数一般不传，不传默认为document
$("#div1")
$(".box")
$("#div1 span") -> $("span", div1)
console.log($("#div1 span:first"))
```

3)通过选择器获取的是一个 jQuery 类的实例->jQuery 对象

```
console. log($( #div1"))

[jQuery对象的私有的属性]

$("#div1")[0] -> div1这个元素对象
S(#div1").selector -> "#div1"
S(#div1").context -> document
("#div1").length-)1 获取元素的个数

[jQuery对象的公有的属性]
jQuery.prototype
```

4)我们获取的是 jQuery 对象(他是 jQuery 的实例)不是我们的原生 js 对象

jQuery:$("#div1")
JS:document.getElementById("div1") 原生JS的对象不能直接的使用jQuery的方法,同理,jQuery的对象也不能使用原生js的方法
$("#div1").className = "box"; no
document.getElementById("div1").addClass();

5)互相转化

```
var $oDiv =$("#div1")
var oDiv = document.getElementById("div1")
Js->jQuery: $(oDiv).addClass()
jQuery->Js: $oDiv[o]/ $oDiv.get(0)
```

3、核心

```js
$(document).ready(function() {
  //HTML结构加载完成就执行这里的代码
});
$(function() {});
```

```
each

$("selector").each( function(){})遍历获取的这些元素 jQuery.prototype
$.each(ary)遍历数组中的每一项 jQuery.each
```

我们的 jQuery 不仅仅是一个类(在它的原型上定义了很多的方法,每一个 jQuery 的实例都可以使用这些方法),它还是一个普通的对象,在 jQuery 本身的属性中还增加了一系列的方法:Ajax、each、工具

\$.unique(ary)

\$.ajax()

```
$.extend()->把 jQuery当做一个对象,给它扩展属性->完善类库

$.fn.extend()->在 jQuery的原型上扩展属性和方法->编写 jQuery插件

$.extend({
    a: function(){

    }
})
$.a()

$.fn.extend({
    b: function(){

    }
})
$().b()
```

[参与互动](https://github.com/yisainan/web-interview/issues/358)

</details>

<b><details><summary>13.是否知道自定义事件？ jQuery 里的 fire 函数是什么意思，什么时候用？</summary></b>

答案：

[参与互动](https://github.com/yisainan/web-interview/issues/359)

</details>

<b><details><summary>14.jQuery 通过哪个方法和 Sizzle 选择器结合的？</summary></b>

答案：

[参与互动](https://github.com/yisainan/web-interview/issues/360)

</details>

<b><details><summary>15.jQuery 一个对象可以同时绑定多个事件，这是如何实现的？</summary></b>

答案：jQuery 可以给一个对象同时绑定多个事件，低层实现方式是使用 addEventListner 或 attachEvent 兼容不同的浏览器实现事件的绑定，这样可以给同一个对象注册多个事件。

[参与互动](https://github.com/yisainan/web-interview/issues/361)

</details>

<b><details><summary>16.针对 jQuery 的优化方法？</summary></b>

答案：

[参与互动](https://github.com/yisainan/web-interview/issues/362)

</details>

<b><details><summary>17.jQuery UI 如何自定义组件？</summary></b>

答案：

[参与互动](https://github.com/yisainan/web-interview/issues/363)

</details>

<b><details><summary>18.jQuery 和 Zepto 的区别？ 各自的使用场景？</summary></b>

答案：

1. Zepto 对象 不能自定义事件

```
例如执行： $({}).bind('cust', function(){});
结果：  TypeError: Object has no method 'addEventListener'
解决办法是创建一个脱离文档流的节点作为事件对象：
例如： $('').bind('cust', function(){});
```

2. Zepto 的选择器表达式: [name=value]   中 value 必须用 双引号 "  or 单引号 ' 括起来

```
例如执行：$('[data-userid=123123123]')
结果：Error: SyntaxError: DOM Exception 12
解决办法： $('[data-userid="123123123]"') or \$("[data-userid='123123123']")

2-1.zepto 的选择器没有办法选出 \$("div[name!='abc']") 的元素
2-2.zepto获取select元素的选中option不能用类似jq的方法$('option[selected]'),因为selected属性不是css的标准属性

应该使用$('option').not(function(){ return !this.selected })
比如：jq:$this.find('option[selected]').attr('data-v') * 1
zepto:$this.find('option').not(function() {return !this.selected}).attr('data-v') * 1
但是获取有select中含有disabled属性的元素可以用 $this.find("option:not(:disabled)") 因为disabled是标准属性
参考网址：https://github.com/madrobby/zepto/issues/503

2-3、zepto在操作dom的selected和checked属性时尽量使用prop方法

```

3. Zepto 是根据标准浏览器写的，所以对于节点尺寸的方法只提供 width() 和 height()，省去了 innerWidth(), innerHeight(),outerWidth(),outerHeight()

```
Zepto.js: 由盒模型（ box-sizing ）决定
jQery: 忽略盒模型，始终返回内容区域的宽/高（不包含 padding 、 border ）解决方式就是使用 .css('width') 而不是 .width() 。

3-1.边框三角形宽高的获取
假设用下面的 HTML 和 CSS 画了一个小三角形：
```

```css
<div class="caret" > </div > .caret {
  width: 0;
  height: 0;
  border-width: 0 20px 20px;
  border-color: transparent transparent blue;
  border-style: none dotted solid;
}
```

```
jQuery 使用 .width() 和 .css('width') 都返回 ，高度也一样；
Zepto 使用 .width() 返回 ，使用 .css('width') 返回 0px 。
所以，这种场景，jQuery 使用 .outerWidth() / .outerHeight() ；Zepto 使用 .width() / .height() 。

3-2.offset()

Zepto.js: 返回 top 、 left 、 width 、 height
jQuery: 返回 width 、 height

3-3.隐藏元素

Zepto.js: 无法获取宽高；
jQuery: 可以获取。
```

4. Zepto 的 each 方法只能遍历 数组，不能遍历 JSON 对象
5. Zepto 的 animate 方法参数说明 ：详情点击-> [zepto 中 animate 的用法](https://blog.csdn.net/kongjiea/article/details/38534435)

6. zepto 的 jsonp callback 函数名无法自定义

7. DOM 操作区别

jq 代码：

```js
(function($) {
  $(function() {
    var $list = $("<ul><li>jQuery 插入</li></ul>", {
      id: "insert-by-jquery"
    });
    $list.appendTo($("body"));
  });
})(window.jQuery);
```

jQuery 操作 ul 上的 id 不会被添加。

zepto 代码：

```js
Zepto(function($) {
  var $list = $("<ul><li>Zepto 插入</li></ul>", {
    id: "insert-by-zepto"
  });
  $list.appendTo($("body"));
});
```

Zepto 可以在 ul 上添加 id 。

8. 事件触发区别

jq 代码：

```js
(function($) {
  $(function() {
    $script = $("<script />", {
      src: "http://cdn.amazeui.org/amazeui/1.0.1/js/amazeui.min.js",
      id: "ui-jquery"
    });

    $script.appendTo($("body"));

    $script.on("load", function() {
      console.log("jQ script loaded");
    });
  });
})(window.jQuery);
```

使用 jQuery 时 load 事件的处理函数 不会 执行

zepto 代码：

```js
Zepto(function($) {
  $script = $("<script />", {
    src: "http://cdn.amazeui.org/amazeui/1.0.1/js/amazeui.js",
    id: "ui-zepto"
  });

  $script.appendTo($("body"));

  $script.on("load", function() {
    console.log("zepto script loaded");
  });
});
```

使用 Zepto 时 load 事件的处理函数 会 执行。

9. zepto 阻止事件冒泡

10. zepto 的 slideUP 和 slidedown 事件到底部才能触发

```js
document.addEventListener(
  "touchmove",
  function(event) {
    event.preventDefault();
  },
  false
);
```

解析：[参考](https://blog.csdn.net/kongjiea/article/details/42522305#)

[参与互动](https://github.com/yisainan/web-interview/issues/364)

</details>

<b><details><summary>19.jQuery 对象的特点</summary></b>

答案：

[参与互动](https://github.com/yisainan/web-interview/issues/365)

</details>

<b><details><summary>20.Zepto 的点透问题如何解决？</summary></b>

答案：点透主要是由于两个 div 重合，例如：一个 div 调用 show()，一个 div 调用 hide()；这个时候当点击上面的 div 的时候就会影响到下面的那个 div；
解决办法主要有 2 种：

1. github 上有一个叫做 fastclick 的库，它也能规避移动设备上 click 事件的延迟响应，https://github.com/ftlabs/fastclick
   将它用 script 标签引入页面（该库支持 AMD，于是你也可以按照 AMD 规范，用诸如 require.js 的模块加载器引入），并且在 dom ready 时初始化在 body 上，
2. 根据分析，如果不引入其它类库，也不想自己按照上述 fastclcik 的思路再开发一套东西，需要 1.一个优先于下面的“divClickUnder”捕获的事件；2.并且通过这个事件阻止掉默认行为（下面的“divClickUnder”对 click 事件的捕获，在 ios 的 safari，click 的捕获被认为和滚屏、点击输入框弹起键盘等一样，是一种浏览器默认行为，即可以被 event.preventDefault()阻止的行为）。

[参与互动](https://github.com/yisainan/web-interview/issues/366)

</details>

<b><details><summary>21.一个 div，有几种方式得到这个 div 的 jQuery 对象？</summary></b>

`<div class='aabbcc' id='nodesView'></div>`想直接获取这个 div 的 dom 对象，如何获取？dom 对象如何转化为 jQuery 对象？

答案：

[参与互动](https://github.com/yisainan/web-interview/issues/367)

</details>

<b><details><summary>22.jQuery 框架中\$.ajax()的常用参数有哪些？写一个 post 请求并带有发送数据和返回数据的样例</summary></b>

答案：

[参与互动](https://github.com/yisainan/web-interview/issues/368)

</details>

<b><details><summary>23.jQuery 的优点</summary></b>

答案：

1、轻量级

JQuery 非常轻巧，采用 Dean Edwards 编写的 Packer 压缩后，大小不到 30KB,如果使用 Min 版并且在服务器端启用 Gzip 压缩后，大小只有 18KB。

gzip： 每天一个 linux 命令（32）：gzip 减少文件大小有两个明显的好处，一是可以减少存储空间，二是通过网络传输文件时，可以减少传输的时间。gzip 是在 Linux 系统中经常使用的一个对文件进行压缩和解压缩的命令，既方便又好用。gzip 不仅可以用来压缩大的、较少使用的文件以节省磁盘空间，还可以和 tar 命令一起构成 Linux 操作系统中比较流行的压缩文件格式。据统计，gzip 命令对文本文件有 60%～ 70%的压缩率。

2、强大的选择器

JQuery 允许开发者使用从 CSS1 到 CSS3 几乎所有的选择器，以及 JQuery 独创的高级而且复杂的选择器，另外还可以加入插件使其支持 XPath 选择器，甚至开发者可以编写属于自己的选择器。由于 JQuery 支持选择器这一特性，因此有一定 CSS 经验的开发人员可以很容易的切入到 JQuery 的学习中来。

XPath：
XPath 是一门在 XML 文档中查找信息的语言。XPath 可用来在 XML 文档中对元素和属性进行遍历。

     XPath 是 W3C XSLT 标准的主要元素，并且 XQuery 和 XPointer 都构建于 XPath 表达之上。

     因此，对 XPath 的理解是很多高级 XML 应用的基础。

3、出色的 DOM 操作的封装

JQuery 封装了大量常用的 DOM 操作，使开发者在编写 DOM 操作相关程序的时候能够得心应手。JQuery 轻松地完成各种原本非常复杂的操作，让 JavaScript 新手也能写出出色的程序。

4、可靠的事件处理机制

JQuery 的事件处理机制吸收了 JavaScript 专家 Dean Edwards 编写的事件处理函数的精华，是的 JQuery 在处理事件绑定的时候相当可靠。在预留退路、循序渐进以及非入侵式编程思想方面，JQuery 也做得非常不错。

5、完善的 Ajax

JQuery 将所有的 Ajax 操作封装到一个函数\$.ajax()里，使得开发者处理 Ajax 的时候能够专心处理业务逻辑而无需关心复杂的浏览器兼容性和 XMLHttpRequest 对象的创建和使用的问题。

6、不污染顶级变量

JQuery 只建立一个名为 JQuery 的对象，其所有的函数方法都在这个对象之下。其别名\$也可以随时交流控制权，绝对不会污染其他的对象。该特性是 JQuery 可以与其他 JavaScript 库共存，在项目中放心地引用而不需要考虑到后期的冲突。

7、出色的浏览器兼容性

作为一个流行的 JavaScript 库，浏览器的兼容性是必须具备的条件之一。JQuery 能够在 IE6.0+,FF 2+,Safari2.+和 Opera9.0+下正常运行。JQuery 同时修复了一些浏览器之间的的差异，使开发者不必在开展项目前建立浏览器兼容库。

8、链式操作方式

JQuery 中最有特色的莫过于它的链式操作方式——即对发生在同一个 JQuery 对象上的一组动作，可以直接接连写无需要重复获取对象。这一特点使得 JQuery 的代码无比优雅。

9.隐式迭代

当用 JQuery 找到带有“.myClass”类的全部元素，然后隐藏他们时。无需循环遍历每一个返回的元素。相反，JQuery 里的方法都被设计成自动操作的对象集合，而不是单独的对象，这使得大量的循环结构变得不再必要，从而大幅度地减少代码量。

10、行为层与结构层的分离

开发者可以使用选择器选中元素，然后直接给元素添加事件。这种将行为层与结构层完全分离的思想，可以使 JQuery 开发人员和 HTML 或其他页面开发人员各司其职，摆脱过去开发冲突或个人单干的开发模式。同时，后期维护也非常方便，不需要在 HTML 代码中寻找某些函数和重复修改 HTML 代码。

11、丰富的插件支持

JQuery 的易扩展性，吸引了来自全球开发者来编写 JQuery 的扩展插件。目前已经有超过几百种官方插件支持，而且还不断有新插件面试。

12、完善的文档

JQuery 的文档非常丰富，现阶段多位英文文档，中文文档相对较少。很多热爱 JQuery 的团队都在努力完善 JQuery 中文文档，例如 JQuery 的中文 API。

13、开源

JQuery 是一个开源的产品，任何人都可以自由地使用并提出修改意见。

[参与互动](https://github.com/yisainan/web-interview/issues/369)

</details>

<b><details><summary>24.Jquery 如何获取子元素</summary></b>

答案：

Jquery 获取子元素的方法有 2 种，分别是 children()方法和 find()方法。下面我们分别来使用这两种方法，看看它们有何差异。

解析：

1、children()方法：获取该元素下的直接子集元素

2、find()方法：获取该元素下的所有子集元素

3、children()方法获取最外层 ul 下面直接子集元素 li：\$("#ul").children("li")

需要注意的是，如果 li 元素下还有 li 元素，children 方法将不会被获取。我们可以用 length 来测试获取的个数“\$("#ul").children("li").length”，最后输出结果为 3

4、find()方法获取 ul 下所有元素 li：\$("#ul").find("li")

需要注意的是，find 方法会无限循环查找 ul 标签节点下的 li，一直找到没有为止，用 length 来测试获取个数“\$("#ul").find("li").length”，最后输出结果为 9

5、children 和 find 的区别：children 只会查找直接子集，而 find 会跨越层级查找，一直找到没有为止。

示例：

```html
<ul id="ul">
  <li>
    list1
    <ul>
      <li>
        list1-1
      </li>
      <li>
        list1-2
      </li>
    </ul>
  </li>
  <li>
    list2
    <ul>
      <li>
        list2-1
      </li>
      <li>
        list2-2
      </li>
    </ul>
  </li>
  <li>
    list3
    <ul>
      <li>
        list3-1
      </li>
      <li>
        list3-2
      </li>
    </ul>
  </li>
</ul>
```

```js
console.log($("#ul").find("li").length); // 9
console.log($("#ul").children("li").length); // 3
```

[参与互动](https://github.com/yisainan/web-interview/issues/370)

</details>
