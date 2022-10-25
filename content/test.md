* new Vue发生什么？ Vue就是个类，只能通过new 关键字来初始化。然后会调用this._init，这个方法做了几件事：合并配置，初始化生命周期，初始化事件中心，初始化渲染，初始化 data、props、computed、watcher 等等

* Vue的数据为什么频繁变化但只会更新一次？ 如果同一个观察者被多次触发，只会被推入到nextTick 的回调队列中一次

* Vue组件为什么采用异步渲染？例如一个组件使用了两个data的属性，更新两个属性如果触发两次渲染的话，会影响性能。因此Vue采取异步更新。

* 异步渲染原理是什么？每次更新响应的属性之后，会将渲染的watcher放到一个队列中，在下个事件循环中再执行。整个更新渲染的过程是： 1. data的属性更新 2. 通知依赖的render 3. render的watcher加入队列（队列去重） 4. nextTick清空watcher队列，执行各watcher中的回调

* nextTick的原理？Vue使用MutationObserver/Promise/setTimeout实现nextTick。Vue判断浏览器兼容性，按照MutationObserver -> Promise -> setTimeout的优先级实现nextTick。

* vue父子组件挂载顺序：初始化的时候父 beforeCreate created beforeMount 子 beforeCreate created beforeMount 父 mounted 子 mounted；；；更新 父beforeUpdate 子beforeUpdate 父updated 子updated；【这里理解错了，应该是子updated 父 updated 】；；销毁 父beforeDestroy 子beforeDestroy 子destroyed 父destroyed 

* process.nextTick和Vue.nextTick的区别？Vue.nextTick是将任务加入到宏任务队列或者微任务队列。
process.nextTick并未将任务加入到宏任务队列或者微任务队列，它是将任务加到下次事件循环之前。

* vue组件watch中deep和immediate的作用？watch有两个选项：deep和immediate，deep决定是否深度监听，即是否监听多层对象数据，immediate决定是否立即执行，如果为true，会在绑定时候（初始时候）立即执行，如果为false，只在监听的值变更时候执行。默认为false。

* vue如何实现自定义指令？使用Vue.diractive全局注册或者在组件的directive属性中，通过钩子来实现自定义指令。 

* Vue.use方法的使用？通过调用Vue.use()方法来安装插件，插件是一个构造函数，它必须实现一个install方法，Vue会调用install方法，并传入Vue变量，让插件可以使用Vue来向Vue添加全局功能。

* vue和react的区别是什么？
相同点就是虚拟dom


React和Vue在框架设计上有很多相同点 1. 使用 Virtual DOM 2. 提供了响应式 (Reactive) 和组件化 (Composable) 的视图组件。 3. 将注意力集中保持在核心库，而将其他功能如路由和全局状态管理交给相关的库。 性能、包体积大小也都不是决定因素。 它们在编码风格和使用细节上存在差别： 1. React的API简洁，Vue的API更多，因此使用Vue编写代码可能更少。 2. Vue更容易上手（因为帮开发者做了很多事情，computed、双向绑定等），React要实现相同功能需要用户手操作，例如需要通过受控组件来实现表单的数据同步，不如Vue的v-model语法糖更便捷。而且Vue的模板语法更贴近原生，因而更容易接受和理解。 3. React虽然API简单，但也因此在某些场景需要一些实践来优化，如shouldComponentUpdate，Vue使用数据劫持，能够做到改变了才触发渲染，更精准。 4. 模板语法 VS JSX语法，其实Vue也可以支持JSX，JSX表达能力更强，模板语法更直观。 5. React有一些主张，例如纯函数等，对编写项目有一定的限制，有的观点认为React规范能尽可能保证项目少出bug，所以更适合大型项目。 6. react社区较大，Vue及周边都主要是官方在维护，更稳定一些。 7. 超大规模的首屏渲染上React有一些优势，因为Vue需要做一些初始化工作。 8. React组件是继承React.Component，Vue是对象，因此React可以实现基于继承的组件复用（虽然并不推荐），而Vue不行。 在响应式原理上也存在差别： React和Vue在响应式的原理上有所不同，Vue是通过数据劫持，实现当数据变化时候响应式更新，React是在setState时候diff组件树。

* vue父子组件通信？

* vue兄弟组件通信？

* vue的eventbus的实现？ 实际就是一个vue实例。自己作为调度中心，通过$on $emit 实现兄弟组件传参

* vue响应式原理? 通过数据劫持改变组件取值和设置行为，取值的时候依赖手机，设置的时候通知订阅者

* 模板编译原理？ vue的compile过程？ 

* vue的computed和watch的实现原理？


* computed是怎么收集依赖的？ 主要是被data收集依赖，

* vue-router中的路由守卫有哪些？独享 全局 组件内

* vue3.0有哪些变化？Vue3.0和Vue2.0的区别？ 新增组合api，v-if和v-for优先级变化

* Vuex工作机制？

* 

* 



未完待续(https://zhuanlan.zhihu.com/p/507020019)

深入浅出Vue响应式原理 https://segmentfault.com/a/1190000019700618

Vue响应式原理？1.监测数据变化：双向数据绑定 2. 依赖收集 3.派发更新，完成渲染

Vue通过数据代理改变组件的数据访问和设置的行为，在访问时候收集依赖，在设置时候通知订阅者。 更详细的说明请参考知识点。

订阅者 Dep 观察者 Watcher

依赖收集的时候调用 addSub，当需要派发更新的时候调用 notify

收集依赖 所谓的依赖，其实就是Watcher。

* 

* 

* 

* loader的工作原理？有一些webpack不认识的模块，通过

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

* 

* 


* 

* 

* 

* 

* 

* 

* Promise的两个特点 

* vue3 6大特性  更小 更快 合并api（不对叫组合api） ts支持    
teplate （不对是teleport）组件 Fragment

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

* nextTick的原理？

* 整个更新渲染的过程是？data属性发生变化，watcher加入更新队列，
nexttick清空队列，执行watcher中回调渲染页面

  

* Vue是如何实现上面的效果的呢？new Vue之后，遍历整个组件树，模板会编
译成render函数，render函数执行获得虚拟dom。子组件也同样操作，最后形成
虚拟dom树。

* 

* 


识别入口。解析文件，编译文件，生成代码




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

6.







