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

<b><details><summary>3.你如何获取浏览器 URL 中查询字符串中的参数？</summary></b>

```

function showWindowHref(){
    var sHref = window.location.href;
    var args = sHref.split('?');
    if(args[0] == sHref){
        return "";
    }
    var arr = args[1].split('&');
    var obj = {};
    for(var i = 0;i< arr.length;i++){
        var arg = arr[i].split('=');
        obj[arg[0]] = arg[1];
    }
    return obj;
}
var href = showWindowHref(); // obj
console.log(href['name']); // xiaoming

```

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

</details>

<b><details><summary>6.你对闭包的理解？</summary></b>

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
