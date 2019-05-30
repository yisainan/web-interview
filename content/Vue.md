# [返回主页](../README.md)

<b><details><summary>1. vue 中的性能优化</summary></b>

Vue 应用运行时性能优化措施

引入生产环境的 Vue 文件

使用单文件组件预编译模板

提取组件的 CSS 到单独到文件

利用 Object.freeze()提升性能

扁平化 Store 数据结构

合理使用持久化 Store 数据

组件懒加载

Vue 应用加载性能优化措施

服务端渲染 / 预渲染

组件懒加载

</details>

<b><details><summary>2. Vue 的实例生命周期</summary></b>

![vue_002](../images/vue_002.jpg)

（1） beforeCreate 初始化实例后 数据观测和事件配置之前调用

（2） created 实例创建完成后调用

（3） beforeMount 挂载开始前被用

（4） mounted el 被新建 vm.\$el 替换并挂在到实例上之后调用

（5） beforeUpdate 数据更新时调用

（6） updated 数据更改导致的 DOM 重新渲染后调用

（7） beforeDestory 实例被销毁前调用

（8） destroyed 实例销毁后调用

</details>

<b><details><summary>3. Vue 的双向数据绑定的原理</summary></b>

VUE 实现双向数据绑定的原理就是利用了 Object.defineProperty() 这个方法重新定义了对象获取属性值(get)和设置属性值(set)的操作来实现的。

</details>

<b><details><summary>4. 构建的 vue-cli 工程都到了哪些技术，它们的作用分别是什么？</summary></b>

1、vue.js：vue-cli 工程的核心，主要特点是 双向数据绑定 和 组件系统。

2、vue-router：vue 官方推荐使用的路由框架。

3、vuex：专为 Vue.js 应用项目开发的状态管理器，主要用于维护 vue 组件间共用的一些 变量 和 方法。

4、axios（ 或者 fetch 、ajax ）：用于发起 GET 、或 POST 等 http 请求，基于 Promise 设计。

5、vux 等：一个专为 vue 设计的移动端 UI 组件库。

6、创建一个 emit.js 文件，用于 vue 事件机制的管理。

7、webpack：模块加载和 vue-cli 工程打包器。

</details>

<b><details><summary>5. vue-cli 工程常用的 npm 命令有哪些？</summary></b>

下载 node_modules 资源包的命令：

npm install
启动 vue-cli 开发环境的 npm 命令：

npm run dev
vue-cli 生成 生产环境部署资源 的 npm 命令：

npm run build
用于查看 vue-cli 生产环境部署资源文件大小的 npm 命令：

npm run build --report
此命令必答，可以加深面试官好感！
命令效果：
![vue_001](../images/vue_001.jpg)

在浏览器上自动弹出一个 展示 vue-cli 工程打包后 app.js、manifest.js、vendor.js 文件里面所包含代码的页面。可以具此优化 vue-cli 生产环境部署的静态资源，提升 页面 的加载速度。

</details>

<b><details><summary>6. 请说出 vue-cli 工程中每个文件夹和文件的用处</summary></b>

```
vue-cli目录解析：

build 文件夹：用于存放 webpack 相关配置和脚本。开发中仅 偶尔使用 到此文件夹下 webpack.base.conf.js 用于配置 less、sass等css预编译库，或者配置一下 UI 库。
config 文件夹：主要存放配置文件，用于区分开发环境、线上环境的不同。 常用到此文件夹下 config.js 配置开发环境的 端口号、是否开启热加载 或者 设置生产环境的静态资源相对路径、是否开启gzip压缩、npm run build 命令打包生成静态资源的名称和路径等。
dist 文件夹：默认 npm run build 命令打包生成的静态资源文件，用于生产部署。
node_modules：存放npm命令下载的开发环境和生产环境的依赖包。
src: 存放项目源码及需要引用的资源文件。
src下assets：存放项目中需要用到的资源文件，css、js、images等。
src下componets：存放vue开发中一些公共组件：header.vue、footer.vue等。
src下emit：自己配置的vue集中式事件管理机制。
src下router：vue-router vue路由的配置文件。
src下service：自己配置的vue请求后台接口方法。
src下page：存在vue页面组件的文件夹。
src下util：存放vue开发过程中一些公共的.js方法。
src下vuex：存放 vuex 为vue专门开发的状态管理器。
src下app.vue：使用标签<route-view></router-view>渲染整个工程的.vue组件。
src下main.js：vue-cli工程的入口文件。
index.html：设置项目的一些meta头信息和提供<div id="app"></div>用于挂载 vue 节点。
package.json：用于 node_modules资源部 和 启动、打包项目的 npm 命令管理。
```

</details>

<b><details><summary>7. config 文件夹 下 index.js 的对于工程 开发环境 和 生产环境 的配置</summary></b>

```
build 对象下 对于 生产环境 的配置：

index：配置打包后入口.html文件的名称以及文件夹名称
assetsRoot：配置打包后生成的文件名称和路径
assetsPublicPath：配置 打包后 .html 引用静态资源的路径，一般要设置成 "./"
productionGzip：是否开发 gzip 压缩，以提升加载速度

dev 对象下 对于 开发环境 的配置：

port：设置端口号
autoOpenBrowser：启动工程时，自动打开浏览器
proxyTable：vue设置的代理，用以解决 跨域 问题
```

</details>

<b><details><summary>8. 请你详细介绍一些 package.json 里面的配置</summary></b>

```
scripts：npm run xxx 命令调用node执行的 .js 文件
dependencies：生产环境依赖包的名称和版本号，即这些 依赖包 都会打包进 生产环境的JS文件里面
devDependencies：开发环境依赖包的名称和版本号，即这些 依赖包 只用于 代码开发 的时候，不会打包进 生产环境js文件 里面。
```

</details>

<b><details><summary>9. 对于 Vue 是一套渐进式框架的理解</summary></b>

每个框架都不可避免会有自己的一些特点，从而会对使用者有一定的要求，这些要求就是主张，主张有强有弱，它的强势程度会影响在业务开发中的使用方式。

1、使用 vue，你可以在原有大系统的上面，把一两个组件改用它实现，当 jQuery 用；

2、也可以整个用它全家桶开发，当 Angular 用；

3、还可以用它的视图，搭配你自己设计的整个下层用。你可以在底层数据逻辑的地方用 OO(Object–Oriented )面向对象和设计模式的那套理念。
也可以函数式，都可以。

它只是个轻量视图而已，只做了自己该做的事，没有做不该做的事，仅此而已。

你不必一开始就用 Vue 所有的全家桶，根据场景，官方提供了方便的框架供你使用。

场景联想
场景 1：
维护一个老项目管理后台，日常就是提交各种表单了，这时候你可以把 vue 当成一个 js 库来使用，就用来收集 form 表单，和表单验证。

场景 2：
得到 boss 认可， 后面整个页面的 dom 用 Vue 来管理，抽组件，列表用 v-for 来循环，用数据驱动 DOM 的变化

场景 3:
越来越受大家信赖，领导又找你了，让你去做一个移动端 webapp，直接上了 vue 全家桶！

场景 1-3 从最初的只因多看你一眼而用了前端 js 库，一直到最后的大型项目解决方案。

</details>

<b><details><summary>10. vue.js 的两个核心是什么？</summary></b>

数据驱动和组件化思想

</details>

<b><details><summary>11. 请问 v-if 和 v-show 有什么区别</summary></b>

显示来看 v-if 是“真正的”条件渲染，因为它会确保在切换过程中条件块内的事件监听器和子组件适当地被销毁和重建；而 v-show 不管初始条件是什么，元素总是会被渲染，并且只是简单地基于 CSS 进行切换。

一般来说， v-if 有更高的切换开销，而 v-show 有更高的初始渲染开销。因此，如果需要非常频繁地切换，则使用 v-show 较好；如果在运行时条件不太可能改变，则使用 v-if 较好。

</details>

<b><details><summary>12. vue 常用的修饰符</summary></b>

[答案](https://blog.csdn.net/qq_42238554/article/details/86592295)

</details>

<b><details><summary>13. v-on 可以监听多个方法吗？</summary></b>

肯定可以的。

```
<input type="text" :value="name" @input="onInput" @focus="onFocus" @blur="onBlur" />
```

</details>

<b><details><summary>14. vue 中 key 值的作用</summary></b>

需要使用 key 来给每个节点做一个唯一标识，Diff 算法就可以正确的识别此节点，找到正确的位置区插入新的节点
所以一句话，key 的作用主要是为了高效的更新虚拟 DOM

</details>

<b><details><summary>15. vue-cli 工程升级 vue 版本</summary></b>

在项目目录里运行 npm upgrade vue vue-template-compiler，不出意外的话，可以正常运行和 build。如果有任何问题，删除 node_modules 文件夹然后重新运行 npm i 即可。（简单的说就是升级 vue 和 vue-template-compiler 两个插件）

</details>

<b><details><summary>16. vue 事件中如何使用 event 对象？</summary></b>

v-on 指令（可以简写为 @）

1、使用不带圆括号的形式，event 对象将被自动当做实参传入；

2、使用带圆括号的形式，我们需要使用 \$event 变量显式传入 event 对象。

解释：

一、event 对象

（一）事件的 event 对象

你说你是搞前端的，那么你肯定就知道事件，知道事件，你就肯定知道 event 对象吧？各种的库、框架多少都有针对 event 对象的处理。比如 jquery，通过它内部进行一定的封装，我们开发的时候，就无需关注 event 对象的部分兼容性问题。最典型的，如果我们要阻止默认事件，在 chrome 等浏览器中，我们可能要写一个：
```
event.preventDefault();
```
而在 IE 中，我们则需要写：
```
event.returnValue = false;
```
多亏了 jquery ，跨浏览器的实现，我们统一只需要写：
```
event.preventDefault();
```
兼容？jquery 内部帮我们搞定了。类似的还有比如阻止事件冒泡以以及事件绑定（addEventListener / attachEvent）等，简单到很多的后端都会使用 $('xxx').bind(...)，这不是我们今天的重点，我们往下看。

（二）vue 中的 event 对象

我们知道，相比于 jquery，vue 的事件绑定可以显得更加直观和便捷，我们只需要在模板上添加一个 v-on 指令（还可以简写为 @），即可完成类似于 $('xxx').bind 的效果，少了一个利用选择器查询元素的操作。我们知道，jquery 中，event 对象会被默认当做实参传入到处理函数中，如下

```
$('body').bind('click', function (event) {
  console.log(typeof event);        // object 
});
```
这里直接就获取到了 event 对象，那么问题来了，vue 中呢？
```
<div id="app">
    <button v-on:click="click">click me</button>
</div>
...
var app = new Vue({
    el: '#app',
    methods: {
        click(event) {
            console.log(typeof event);    // object
        }
    }
});
```
这里的实现方式看起来和 jquery 是一致的啊，但是实际上，vue 比 jquery 要要复杂得多，jquery 官方也明确的说，v-on 不简单是 addEventListener 的语法糖。在 jquery 中，我们传入到 bind 方法中的回调，只能是一个函数表类型的变量或者一个匿名函数，传递的时候，还不能执行它（在后面加上一堆圆括号），否则就变成了取这一个函数的返回值作为事件回调。而我们知道，vue 的 v-on 指令接受的值可以是函数执行的形式，比如 v-on:click="click(233)" 。这里我们可以传递任何需要传递的参数，甚至可以不传递参数：
```
<div id="app">
    <button v-on:click="click()">click me</button>
</div>
...
var app = new Vue({
    el: '#app',
    methods: {
        click(event) {
            console.log(typeof event);    // undefined
        }
    }
});
```
咦？我的 event 对象呢？怎么不见了？打印看看 arguments.length 也是 0，说明这时候确实没有实参被传入进来。T_T，那我们如果既需要传递参数，又需要用到 event 对象，这个该怎么办呢？

（三）$event

翻看 vue 文档，不难发现，其实我们可以通过将一个特殊变量 $event 传入到回调中解决这个问题：
```
<div id="app">
    <button v-on:click="click($event, 233)">click me</button>
</div>
...
var app = new Vue({
    el: '#app',
    methods: {
        click(event, val) {
            console.log(typeof event);    // object
        }
    }
});
```
好吧，这样看起来就正常了。
简单总结来说：

使用不带圆括号的形式，event 对象将被自动当做实参传入；

使用带圆括号的形式，我们需要使用 $event 变量显式传入 event 对象。


二、乌龙
前面都算是铺垫吧，现在真正的乌龙来了。
翻看小伙伴儿的代码，偶然看到了类似下面的代码：
```
<div id="app">
    <button v-on:click="click(233)">click me</button>
</div>
...
var app = new Vue({
    el: '#app',
    methods: {
        click(val) {
            console.log(typeof event);    // object
        }
    }
});
```
看到这一段代码，我的内心是崩溃的，丢进 chrome 里面一跑，尼玛还真可以，打印 arguments.length，也是正常的 1。尼玛！这是什么鬼？毁三观啊？
既没有传入实参，也没有接收的形参，这个 event 对象的来源，要么是上级作用链，要么。。。是全局作用域。。。全局的，不禁想到了 window.event
。再次上 MDN 确认了一下，果然，window.event，ie 和 chrome 都在 window 对象上有这样一个属性：

![vue_003](../images/vue_003.jpg)

代码丢进 Firefox 中运行，event 果然就变成了 undefined 了。额，这个我也不知道说什么了。。。

</details>

<b><details><summary>17. $nextTick 的使用</summary></b>

</details>

<b><details><summary>18. Vue 组件中 data 为什么必须是函数</summary></b>

</details>

<b><details><summary>19. v-for 与 v-if 的优先级</summary></b>

</details>

<b><details><summary>20. vue 中子组件调用父组件的方法</summary></b>

</details>

<b><details><summary>21. vue 中父组件调用子组件的方法</summary></b>

</details>

<b><details><summary>22. vue 中 keep-alive 组件的作用</summary></b>

</details>

<b><details><summary>23. vue 中如何编写可复用的组件？</summary></b>

</details>

<b><details><summary>24. 什么是 vue 生命周期和生命周期钩子函数？</summary></b>

</details>

<b><details><summary>25. vue 生命周期钩子函数有哪些？</summary></b>

</details>

<b><details><summary>26. vue 如何监听键盘事件中的按键？</summary></b>

</details>

<b><details><summary>27. vue 更新数组时触发视图更新的方法</summary></b>

</details>

<b><details><summary>28. vue 中对象更改检测的注意事项</summary></b>

</details>

<b><details><summary>29. 解决非工程化项目初始化页面闪动问题</summary></b>

</details>

<b><details><summary>30. v-for 产生的列表，实现 active 的切换</summary></b>

</details>

<b><details><summary>31. v-model 语法糖的组件中的使用</summary></b>

</details>

<b><details><summary>32. 十个常用的自定义过滤器</summary></b>

</details>

<b><details><summary>33. vue 等单页面应用及其优缺点</summary></b>

</details>

<b><details><summary>34. 什么是 vue 的计算属性？</summary></b>

</details>

<b><details><summary>35. vue-cli 提供的几种脚手架模板</summary></b>

</details>

<b><details><summary>36. vue 父组件如何向子组件中传递数据？</summary></b>

</details>

<b><details><summary>37. vue-cli 开发环境使用全局常量</summary></b>

</details>

<b><details><summary>38. vue-cli 生产环境使用全局常量</summary></b>

</details>

<b><details><summary>39. vue 弹窗后如何禁止滚动条滚动？</summary></b>

</details>

<b><details><summary>40. 计算属性的缓存和方法调用的区别</summary></b>

</details>

<b><details><summary>41. vue-cli 中自定义指令的使用</summary></b>

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
