# [返回主页](../README.md)

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

<b><details><summary>6.你对闭包的理解？</summary></b>
1.闭包就是能够读取其他函数内部变量的函数。由于在ECMA2015中，只有函数才能分割作用域，函数内部可以当前作用域链的变量，但是外部无法访问函数内部的变量，所以闭包可以理解成“定义在一个函数内部的函数，外部可以通过内部返回的函数访问内部函数的变量“。在本质上，闭包是将函数内部和函数外部连接起来的桥梁。
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

<b><details><summary>8.javascript对象的几种创建方式</summary></b>

1，工厂模式

2，构造函数模式

3，原型模式

4，混合构造函数和原型模式

5，动态原型模式

6，寄生构造函数模式

7，稳妥构造函数模式

</details>

<b><details><summary>9.javascript继承的6种方法</summary></b>

1，原型链继承

2，借用构造函数继承

3，组合继承(原型+借用构造)

4，原型式继承

5，寄生式继承

6，寄生组合式继承

详情：JavaScript 继承方式详解

</details>

<b><details><summary>10.javascript里面的继承怎么实现，如何避免原型链上面的对象共享</summary></b>

用构造函数和原型链的混合模式去实现继承，避免对象共享可以参考经典的 extend()函数，很多前端框架都有封装的，就是用一个空函数当做中间变量

</details>

<b><details><summary>13.变量提升</summary></b>

[变量提升概念]()
[变量提升面试题]()

</details>

<b><details><summary>14.this和apply的应用</summary></b>

</details>

<b><details><summary>15.sort 排序原理</summary></b>

</details>

<b><details><summary>16. jsonp 优缺点？ 事件委托怎么取索引</summary></b>

</details>

<b><details><summary>17.如何判断 NaN</summary></b>

</details>

<b><details><summary>18. null/undefined 的区别</summary></b>

</details>

<b><details><summary>19.简单介绍下 JS 的原型和原型链</summary></b>

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

<b><details><summary>29.JS严格模式和正常模式</summary></b>

</details>

<b><details><summary>30.移动端tap点击事件和click的区别</summary></b>

</details>

<b><details><summary>31.JS单线程还是多线程，如何显示异步操作</summary></b>

</details>

</details>

<b><details><summary>32. JavaScript数组的函数 map/forEach/reduce/filter</summary></b>

</details>

<b><details><summary>33. JS块级作用域、变量提升</summary></b>

</details>

<b><details><summary>34.说下 jQuery/Zepto 中的 on 方法有哪些参数，分别代表什么意思？</summary></b>

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

<b><details><summary></summary></b>

</details>

<b><details><summary></summary></b>

</details>

<b><details><summary></summary></b>

</details>