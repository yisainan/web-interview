# vue

* new Vue发生什么？

* Vue的数据为什么频繁变化但只会更新一次？

* Vue组件为什么采用异步渲染？

* 异步渲染原理是什么？

* nextTick的原理？利用优先级promise MutationObserver setImmdate setTimeout

* vue父子组件挂载顺序?

    加载过程 父 父 父 子 子 子 子 父
    更新过程 父 子 子 父
    销毁过程 父 子 子 父 


* process.nextTick和Vue.nextTick的区别？【不清楚】
    1.先说Vue.nextTick，任务在宏任务 微任务执行
    2.process.nextTick 是在下个事件循环之前执行,加在微任务前面。优先级高于其他的微任务


    如果你希望异步任务尽可能快地执行，那就使用 process.nextTick

```
process.nextTick(() => console.log(1)); 
Promise.resolve().then(() => console.log(2)); 
process.nextTick(() => console.log(3)); 
Promise.resolve().then(() => console.log(4));

```
会输出 1324

* vue组件watch中deep和immediate的作用？
    deep深度监听、immediate立即执行的意思

* vue如何实现自定义指令？
    directive

* Vue.use方法的使用？使用插件，插件需要有install方法

* vue和react的区别是什么？
    vue template模板 react jsx语法
    vue 容易上手 react 需要门槛高一些
    vue 双向数据绑定 react 单向数据流


* vue父子组件通信？prop vuex

* vue兄弟组件通信？eventBus vuex

* vue的eventbus的实现？就是利用vue的实例，实现的观察订阅者模式

* vue响应式原理? 就是数据监听。依赖手机，派发更新

* 模板编译原理？ vue的compile过程？ template模板 ast树，render函数；

* vue的computed和watch的实现原理？

* computed是怎么收集依赖的？ 主要是被data收集依赖，

* vue-router中的路由守卫有哪些？独享 全局 组件内

* vue3.0有哪些变化？Vue3.0和Vue2.0的区别？ 新增组合api，v-if和v-for优先级变化

* Vuex工作机制？

* JS 运⾏机制？

* nextTick的作用?

* Vue如何给一个对象添加新的属性？vue有个$set方法

* vue组件data用箭头函数行不行？可以使用箭头函数，但是需要注意this指向。

* vue怎么检测到数组的变化？Vue2通过重写数组方法实现，Vue3通过Proxy数据代理实现。

以上答案见(https://zhuanlan.zhihu.com/p/507020019)



深入浅出Vue响应式原理 https://segmentfault.com/a/1190000019700618

Vue响应式原理？核心就是数据监听



依赖收集的时候调用 addSub，当需要派发更新的时候调用 notify

收集依赖 所谓的依赖，其实就是Watcher。

* 

* loader的工作原理？有一些webpack不认识的模块，通过

* Flow是什么？是facebook出品的js静态类型检查工具。vue源码就是用的flow。vue源码是基于 Rollup 构建的

* Flow 的工作方式？类型腿短（推断） 类型注释、

* v-if v-for的优先级？vue2 v-for>v-if vue3 v-if>v-for


* 宏任务和微任务，见js/179.
首先执行的是script任务，也就是全局任务，属于宏任务。
// script任务执行完后，开始执行所有的微任务
// 微任务执行完毕，再取任务队列中的一个宏任务执行

宏任务macrotask 主要有：setTimeout,setInterval,setImmediate,requestAnimationFrame,UI rendeing，nodeJS 中的 I/O，script（整体代码）

微任务microtask 主要有：process.nextTick,Promises,MutationObserver


* 

* Promise的两个特点 ：1.外界无法改变其状态 2：状态一经改变就不会在变

* vue3 6大特性？

* 

* 

* 

* 

* 

* 

* 

* CSRF? A网站登录状态，B网站接口响应里请求A网站接口

* vue实现原理？模板通过render编译成虚拟dom，通过数据劫持实现双向数据
绑定【正确的是解析模板成render函数，执行获得虚拟dom；渲染显示页面】

* nextTick的原理？利用事件循环，按有优先级promise，mutationObserver、setImmdate、setTimeout优先级执行

* 整个更新渲染的过程是？data属性发生变化，watcher加入更新队列，
nexttick清空队列，执行watcher中回调渲染页面

  

* Vue是如何实现上面的效果的呢？new Vue之后，遍历整个组件树，模板会编
译成render函数，render函数执行获得虚拟dom。子组件也同样操作，最后形成
虚拟dom树。

* 

*


window.URL.createObjectURL() 创建对象URL


Window对象下有个URL.ceeateObjectERL方法，会创建一个 DOMString，存储在内存中，仅在被创建的文档对象中有效，说白了就是内存中的地址
可以接受File对象或者Blob对象

createObjectURL返回一段带hash的url，并且一直存储在内存中，直到document触发了unload事件（例如：document close）或者执行revokeObjectURL来释放。


Blob 对象表示一个不可变、原始数据的类文件对象。


这里大概说下File对象和Blob对象:
File对象,就是一个文件,比如我用input type="file"标签来上传文件,那么里面的每个文件都是一个File对象.
Blob对象,就是二进制数据,比如通过new Blob()创建的对象就是Blob对象.又比如,在XMLHttpRequest里,如果指定responseType为blob,那么得到的返回值也是一个blob对象.


2。深拷贝是复制一个新的对象，不共享内存，修改新对象不会影响旧对象；浅拷贝是复制旧对象的指针，而不复制对象本身，共享内存。

3.vue性能优化：代码优化，v-if v-show的使用场景，v-if v-for写在一起。seo优化，服务端渲染。打包优化，按需加载。

4.compiler编译器 observer 观察者

5.Vue.js 源码是基于 Rollup 构建的，Rollup 跟webpack一样是构建工具；vue3用的vite启动，vite的主要优势在开发阶段

* vue性能优化？代码优化。打包优化。

* keep-alive的生命周期
1.activated： 页面第一次进入的时候，钩子触发的顺序是created->mounted->activated
2.deactivated: 页面退出的时候会触发deactivated，当再次前进或者后退的时候只触发activated

* vue渲染模板时怎么保留模板中的HTML注释呢？设置comments属性，官网默认为舍弃注释`<template comments> ... <template>`



# react


# html

* HTML 与 XHTML? xhtml必须有闭合的标签、属性小写、


# 浏览器

* 浏览器的渲染过程


* 

* 

* 

* 

* 

* 

* 

* 



