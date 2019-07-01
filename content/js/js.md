# [返回主页](../../README.md)

<b><details><summary>1. JavaScript 中如何检测一个变量是一个 String 类型？请写出函数实现</summary></b>

typeof(obj) === "string"
typeof obj === "string"
obj.constructor === String

</details>

<b><details><summary>2.请用 js 去除字符串空格？</summary></b>

方法一：使用 replace 正则匹配的方法
方法二：使用 str.trim()方法
方法三：使用 jquery,\$.trim(str)方法

</details>

<b><details><summary>4.怎样添加、移除、移动、复制、创建和查找节点？</summary></b>

1）创建新节点

createDocumentFragment() //创建一个 DOM 片段
　　 createElement() //创建一个具体的元素
　　 createTextNode() //创建一个文本节点

2）添加、移除、替换、插入
　　 appendChild() //添加
　　 removeChild() //移除
　　 replaceChild() //替换
　　 insertBefore() //插入

3）查找
　　 getElementsByTagName() //通过标签名称
　　 getElementsByName() //通过元素的 Name 属性的值
　　 getElementById() //通过元素 Id，唯一性

</details>

<b><details><summary>5.事件委托是什么</summary></b>

让利用事件冒泡的原理，让自己的所触发的事件，让他的父元素代替执行！

<summary>阻止事件冒泡</summary>
  event.stopPropagation() || e.cancelBubble = true || return false

</details>

<b><details><summary>6.你对闭包的理解？优缺点？</summary></b>

1.闭包就是能够读取其他函数内部变量的函数。由于在 ECMA2015 中，只有函数才能分割作用域，函数内部可以访问当前作用域的变量，但是外部无法访问函数内部的变量，所以闭包可以理解成“定义在一个函数内部的函数，外部可以通过内部返回的函数访问内部函数的变量“。在本质上，闭包是将函数内部和函数外部连接起来的桥梁。

</details>

<b><details><summary>7.require 与 import 的区别</summary></b>

第一、两者的加载方式不同，require 是在运行时加载，而 import 是在编译时加载

require('./a')(); // a 模块是一个函数，立即执行 a 模块函数

var data = require('./a').data; // a 模块导出的是一个对象

var a = require('./a')[0]; // a 模块导出的是一个数组 ======> 哪都行

import \$ from 'jquery';

import \* as _ from '_';

import {a,b,c} from './a';

import {default as alias, a as a_a, b, c} from './a'; ======>用在开头

第二、规范不同，require 是 CommonJS/AMD 规范，import 是 ESMAScript6+规范

第三、require 特点：社区方案，提供了服务器/浏览器的模块加载方案。非语言层面的标准。只能在运行时确定模块的依赖关系及输入/输出的变量，无法进行静态优化。

import 特点：语言规格层面支持模块功能。支持编译时静态分析，便于 JS 引入宏和类型检验。动态绑定。

</details>

<b><details><summary>8.javascript 对象的几种创建方式</summary></b>

1，工厂模式

2，构造函数模式

3，原型模式

4，混合构造函数和原型模式

5，动态原型模式

6，寄生构造函数模式

7，稳妥构造函数模式

</details>

<b><details><summary>9.javascript 继承的 6 种方法</summary></b>

1，原型链继承

2，借用构造函数继承

3，组合继承(原型+借用构造)

4，原型式继承

5，寄生式继承

6，寄生组合式继承

详情：JavaScript 继承方式详解

</details>

<b><details><summary>13.变量提升</summary></b>

[变量提升概念]()
[变量提升面试题]()

</details>

<b><details><summary>14.this 和 apply 的应用</summary></b>

</details>

<b><details><summary>15.sort 排序原理</summary></b>

</details>

<b><details><summary>16. jsonp 优缺点？ 事件委托怎么取索引</summary></b>

</details>

<b><details><summary>17.如何判断 NaN</summary></b>

</details>

<b><details><summary>18. null/undefined 的区别</summary></b>

</details>

<b><details><summary>20. 如何判断 JS 变量的一个类型（至少三种方式）</summary></b>

</details>

<b><details><summary>21. for/in、Object.keys 和 Object.getOwnPropertyNames 对属性遍历有什么区别？</summary></b>

</details>

<b><details><summary>22.在子 iframe 中调用外层页面的接口，传入一个对象，外层页面如何判断该对象是否为数组？</summary></b>

</details>

<b><details><summary>23.请简要描述 webview 中通过 js bridge 和 native 通信的技术实现</summary></b>

</details>

<b><details><summary>24.如何判断一个对象是否为数组</summary></b>

</details>

<b><details><summary>25.`<script>` 标签的 defer 和 asnyc 属性的作用以及二者的区别？</summary></b>

</details>

<b><details><summary>26.Object.prototype.toString.call() 和 instanceOf 和 Array.isArray() 区别好坏</summary></b>

</details>

<b><details><summary>27.ES6 都有什么 iterater 遍历器</summary></b>

</details>

</details>

<b><details><summary>28.松散类型的数组</summary></b>

</details>

<b><details><summary>29.JS 严格模式和正常模式</summary></b>

</details>

<b><details><summary>30.移动端 tap 点击事件和 click 的区别</summary></b>

</details>

<b><details><summary>31.JS 单线程还是多线程，如何显示异步操作</summary></b>

</details>

</details>

<b><details><summary>32. JavaScript 数组的函数 map/forEach/reduce/filter</summary></b>

</details>

<b><details><summary>33. JS 块级作用域、变量提升</summary></b>

</details>

<b><details><summary>35. JS 哪些操作会造成内存泄露</summary></b>

</details>

</details>

<b><details><summary>36.重排与重绘的区别，什么情况下会触发？</summary></b>

</details>

<b><details><summary>37.发布订阅设计模式</summary></b>

</details>

<b><details><summary>38.防抖，节流</summary></b>

</details>

<b><details><summary>39.兼容各种浏览器版本的事件绑定</summary></b>

</details>

</details>

<b><details><summary>40.typescript 遇到过什么坑</summary></b>

</details>

<b><details><summary>ES6 的动态加载，如何动态 import</summary></b>

</details>

<b><details><summary>JavaScript 的数据类型</summary></b>

JS数据类型共有六种，分别是 String、Number、Boolean、Null、Undefined 和 Object 等， 另外，ES6 新增了 Symbol 类型。其中，Object 是引用类型，其他的都是基本类型(Primitive Type)。

</details>

<b><details><summary>如何判断一个对象是否属于某个类？</summary></b>

</details>

<b><details><summary>new 操作符具体干了什么呢?</summary></b>

</details>

<b><details><summary>call() 和 apply() 的含义和区别？</summary></b>

</details>

<b><details><summary>那些操作会造成内存泄漏？</summary></b>

</details>

<b><details><summary>Zepto 的点透问题如何解决？</summary></b>

</details>

<b><details><summary>如何判断当前脚本运行在浏览器还是 node 环境中？</summary></b>

</details>

<b><details><summary>移动端最小触控区域是多大？</summary></b>

</details>

<b><details><summary>移动端的点击事件的有延迟，时间是多久，为什么会有？ 怎么解决这个延时？</summary></b>

</details>

<b><details><summary>解释 JavaScript 中的作用域与变量声明提升？</summary></b>

</details>

<b><details><summary>Node.js 的适用场景？</summary></b>

</details>

<b><details><summary>什么是“前端路由”?什么时候适合使用“前端路由”? “前端路由”有哪些优点和缺点?</summary></b>

</details>

<b><details><summary>使用构造函数的注意点</summary></b>

    *  1 一般情况下构造函数的首字母需要大写，因为我们在看到一个函数首字母
    *  大写的情况，就认定这是一个构造函数，需要跟new关键字进行搭配使用，创建一个新的
    *  实例（对象）
    *  2 构造函数在被调用的时候需要跟new关键字搭配使用。
    *  3 在构造函数内部通过this+属性名的形式为实例添加一些属性和方法。
    *  4 构造函数一般不需要返回值，如果有返回值
    *  4.1 如果返回值是一个基本数据类型，那么调用构造函数，返回值仍旧是那么创建出来的
    *  对象。
    *  4.2 如果返回值是一个复杂数据类型，那么调用构造函数的时候，返回值就是这个return之后的
    *  那个复杂数据类型。

</details>

<b><details><summary>如何获取浏览器版本信息</summary></b>

window.navigator.userAgent

</details>

<b><details><summary>调试工具的使用</summary></b>

调试模式中的按钮作用
F8 跳出断点调试模式
F10、F11 代码的逐行调试

进入断点调试模式的 方法
1 在浏览器当中打断点

2 直接在代码中加 debugger

</details>

<b><details><summary>数组的常用方法</summary></b>

</details>

<b><details><summary>字符串常用操作</summary></b>

</details>

<b><details><summary>作用域的概念及作用</summary></b>

 * 作用域 ： 起作用的一块区域
 * 作用域的概念： 对变量起保护作用的一块区域
 * 作用： 作用域外部无法获取到作用域内部声明的变量，作用域内部能够获取到作用域外界声明的变量。

</details>

<b><details><summary>作用域的分类</summary></b>

1 块作用域  花括号 {}

2 词法作用域
作用域只跟在何处被创建有关系，跟在何处被调用没有关系

3 动态作用域
作用域只跟在何处被调用有关系，跟在何处被创建没有关系
</details>

<b><details><summary>js属于哪种作用域</summary></b>

```js
 // 块作用域
    /*{
        var num =123;
    }
    console.log(num);*/
    // 如果js属于块作用域，那么在花括号外部就无法访问到花括号内部的声明的num变量。
    // 如果js不属于块级作用域，那么花括号外部就能够访问到花括号内部声明的num变量
    // 能够输出num变量，也就说明js不属于块级作用。
    // 在ES6 之前的版本js是不存在块级作用域的。


    //js属于词法作用域还是动态作用域

    // js中函数可以帮我们去形成一个作用域

   /* function fn(){
        var num =123;
    }
    fn();
    //在函数外界能否访问到num这样一个变量
    console.log(num)*///Uncaught ReferenceError: num is not defined
    // 如果函数能够生成一个作用域，那么在函数外界就无法访问到函数内部声明的变量。
    // js中的函数能够生成一个作用。  函数作用域 。


    // 词法作用域：作用的外界只跟作用域在何处创建有关系，跟作用域在何处被调用没有关系

    var num = 123;
    function f1() {
        console.log(num);//
    }
    function f2() {
        var num = 456;
        f1();//f1在f2被调用的时候会被执行 。
    }
    f2();

    //如果js是词法作用域，那么就会输出f1被创建的时候外部的num变量 123
    //如果js是动态作用域，那么f1执行的时候就会输出f1被调用时外部环境中的num  456

    // js中的作用域属于词法作用域（函数作用域）

```

</details>

<b><details><summary>什么是面向对象？</summary></b>

<!--1 面向对象和面向过程的异同-->
<!--2 在JavaScript中面向对象的表现形式-->
<!--3 其他语言中面向对象的表现形式（了解）-->

</details>

<b><details><summary>javascript的typeof返回哪些数据类型</summary></b>

</details>

<b><details><summary>列举3种强制类型转换和2种隐式类型转换</summary></b>

强制（parseInt,parseFloat,Number）隐式（+ -）

</details>

<b><details><summary>split() join()的区别</summary></b>

</details>

<b><details><summary>如何对网站文件和资源优化</summary></b>

```
文件合并及压缩
使用CDN托管
使用缓存
```

</details>

<b><details><summary>标准模式与怪异模式的区别</summary></b>

</details>

<b><details><summary>img上title与alt</summary></b>

title：图片的信息；alt：图片不显示时显示的文字

</details>

<b><details><summary>css reset 与 css sprites</summary></b>

css reset ：重置浏览器默认属性

css sprites ：由多个小图片组成的大图，减少服务器对图片的请求数

</details>

<b><details><summary>IE6遇到什么bug？解决办法是？</summary></b>

</details>

<b><details><summary>数组方法pop() push() unshift() shift()</summary></b>

</details>

<b><details><summary>事件绑定与普通事件有什么区别</summary></b>

用普通事件添加相同事件，下面会覆盖上面的，而事件绑定不会

普通事件是针对非dom元素，时间绑定是针对dom元素的事件

</details>

<b><details><summary>IE和DOM事件流的区别</summary></b>

</details>

<b><details><summary>IE和标准下有哪些兼容性的写法</summary></b>

</details>

<b><details><summary>css可以继承的属性</summary></b>

list- font- text-

</details>

<b><details><summary>如何阻止冒泡与默认行为</summary></b>

当需要停止冒泡行为时，可以使用
```js
function stopBubble(e) { 
//如果提供了事件对象，则这是一个非IE浏览器 
if ( e && e.stopPropagation ) 
    //因此它支持W3C的stopPropagation()方法 
    e.stopPropagation(); 
else 
    //否则，我们需要使用IE的方式来取消事件冒泡 
    window.event.cancelBubble = true; 
}
```
当需要阻止默认行为时，可以使用
```js
//阻止浏览器的默认行为 
function stopDefault( e ) { 
    //阻止默认浏览器动作(W3C) 
    if ( e && e.preventDefault ) 
        e.preventDefault(); 
    //IE中阻止函数器默认动作的方式 
    else 
        window.event.returnValue = false; 
    return false; 
}
```

</details>

<b><details><summary>如何实现js中的继承</summary></b>

[详情](https://www.cnblogs.com/diligentYe/p/6413450.html)

</details>

<b><details><summary>js中this 闭包 作用域</summary></b>

this：指向调用上下文

闭包：定义一个函数就开辟了一个局部作用域，整个js执行环境有一个全局作用域

作用域：一个函数可以访问其他函数中的变量（闭包是一个受保护的变量空间）

```js
var f = (function fn() {
  var name = 1;
  return function () {
    name++;
    console.log(name)
  }
})()

==>undefined 有疑问
```

</details>

<b><details><summary>javascript的本地对象，内置对象和宿主对象</summary></b>

</details>

<b><details><summary>== 和 === 的不同</summary></b>

</details>

<b><details><summary>javascript的同源策略</summary></b>

</details>

<b><details><summary>js是一门怎样的语言，它有什么特点</summary></b>

</details>

<b><details><summary>事件冒泡与事件捕获</summary></b>

事件冒泡：由最具体的元素（目标元素）向外传播到最不具体的元素

事件捕获：由最不确定的元素到目标元素

</details>

<b><details><summary>foo = foo||bar ，这行代码是什么意思？为什么要这样写？</summary></b>

这种写法称为短路表达式
相当于
```js
var foo;
if (foo) {
  foo = foo
} else {
  foo = bar
}
```
答案：常用于函数参数的空判断

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
