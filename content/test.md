# vue

* new Vue发生什么？vue的实例化，底层调用init方法，初始化数据和方法之类的

* Vue的数据为什么频繁变化但只会更新一次？

* Vue组件为什么采用异步渲染？

* 异步渲染原理是什么？

* nextTick的原理？利用优先级promise MutationObserver setImmdate setTimeout

* vue父子组件挂载顺序?【记住最后一个是父 倒数第二往前都是子】

    加载过程 父 父 父 子 子 子 子 父
    更新过程 父 子 子 父
    销毁过程 父 子 子 父


* process.nextTick和Vue.nextTick的区别？【process.nextTick是node环境下的，在微任务之前执行。vue.nextTick是vue提供的在宏任务或微任务中执行】

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


Process.nextTick 在下次事件循环微任务之前；vue.nexttick [就是在宏任务微任务中执行，没记住]



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

* vue响应式原理? 就是数据监听。依赖收集，派发更新

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

* Promise的两个特点

* vue3 6大特性？快 小 ts 三个新的api【teltport Fragment】 compostionApi


* CSRF? A网站登录状态，B网站接口响应里请求A网站接口

* vue实现原理？模板通过render编译成虚拟dom，通过数据劫持实现双向数据
绑定【正确的是解析模板成render函数，执行获得虚拟dom；渲染显示页面】

* nextTick的原理？利用事件循环，按有优先级promise，mutationObserver、setImmdate、setTimeout优先级执行

* 整个更新渲染的过程是？data属性发生变化，watcher加入更新队列，
nexttick清空队列，执行watcher中回调渲染页面



* Vue是如何实现上面的效果的呢？new Vue之后，遍历整个组件树，模板会编译成render函数，render函数执行获得虚拟dom。子组件也同样操作，最后形成虚拟dom树。

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

* setState发生了啥？把当前状态与原始进行融合，这是异步的过程

* umi createReactapp

* 功能组件：类组件？？不清楚【大多数使用的类组件，能用生命周期函数；函数组件没办法用】

* key就是方便diff运算的

* 优势就是1.引入了虚拟dom，可有效减少频繁的dom操作2.生态比较完善【速度快、模块化、兼容性好】

* setState是异步的，需要等执行完状态才都更新完，这是再渲染

* diff原理就是虚拟dom树一层一层由根层向上比对，

* 生命周期 render componetnwillmount componetDidmount shouldCompontentupdate  
  compontentwillupdate stateinit defaultProps

* shouldComponentUpdate 判断组件是否可以更新

* 虚拟dom减少了频繁的真实dom操作导致的重拍重绘。

* refs 操作dom时使用

* 12 setState会与之前状态值进行融合。replaceState 直接就是替换了

* 13 redux优缺点都不知道

* 14 flux

* 41 jsx就是语法糖，最终生成虚拟dom。两者是相辅相成的【回答错误：应该说jsx本质就是js中的React.createElement】

* 42 jsx比较简洁，更易于开发者开发代码。不用也可以，就是写法上更麻烦【大概意思对，但不准确，Jsx语法糖 类html标签语法 虚拟dom】

* 43 【不清楚jsx背后的模块】【其实就是React.createElement】
可以联想到vue中的h函数，本质就是vue中的createElement方法。
```
  const app = new Vue({
    ··· ···
    render:function(createElement){
        return createElement(App)
    }
  })
```

# html

* HTML 与 XHTML? xhtml必须有闭合的标签、属性小写、

# css

* 2 css盒子模型就是？【回答不准确】应该这样说：盒模型包含content+padding+border+margin。W3C盒模型（content-box）width和hight只是包含content；IE盒模型（border-box），包含content+border+padding

* 3 隐藏元素？display：none； opratity：0；【就想出这两个】
还有visibility：hidden；position；overflow：hidden

* 清除浮动？clear：both；【记不清】

*

*

*

# 浏览器

* 浏览器的渲染过程?dom文档对象模型 cssom渲染 接下来就是js动态渲染

# 安全

* 水平越权。垂直越权。【回答正确】

# 大厂

* 1 方便diff运算的

* 2 【记不住。】

* 3 防抖就是防止手抖短时间触发多次点击等事件。节流就是没隔一段时间执行一次。区别就是防抖规定间隔时间2s，只要前后两个事件间隔少于这个事件，就只执行最后一次；节流是你点了第一个事件，2s内再次点就不会触发了，2s后点击的才生效【基本正确】

* 4 【记不清】

* 5 深度优先就是不撞南墙不回头，根节点加入有5个子节点，他会先把第一个遍历完了，在开始第二个；而广度有限是先把5子节点遍历完，再去孙子节点，再到重孙。。。【基本正确】

* 8 setTimeout 延时计时器 、promise本身是同步，。then是异步。状态一经改变，不会在变；外界无法改变promise内部的状态；Async await 是genner函数的语法糖，需要配合使用，async函数内写await函数，实现同步执行 【基本正确】

* 9 【不太懂】其实就是generater函数的语法糖，利用generater同步写法实现异步

* 10 script start =》async1 start》promise1》 script end 》 async2 》 async1 end 》 promise2 》 setTimeout 【async2打印时间错误】

错误原因：遇到了await时，会将await后面的表达式执行一遍

变式1：script start》async1 start》promise1》promise2 》promise3》script end》async1 end》promise4》setTimeout【promise2打印时间错误】

变式2：【后面再练习】

* 13 【回答正确】

* 

*  

*  

*  

*  

*

*  

*  

*  

*  

*  

*  

*  

*  

*  

* 
