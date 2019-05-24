# [返回主页](../README.md)

<b><details><summary>1.vue 中的性能优化</summary></b>

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

<b><details><summary>Vue的实例生命周期</summary></b>

</details>

<b><details><summary> Vue的双向数据绑定的原理</summary></b>

</details>

<b><details><summary>构建的 vue-cli 工程都到了哪些技术，它们的作用分别是什么？</summary></b>

1、vue.js：vue-cli工程的核心，主要特点是 双向数据绑定 和 组件系统。

2、vue-router：vue官方推荐使用的路由框架。

3、vuex：专为 Vue.js 应用项目开发的状态管理器，主要用于维护vue组件间共用的一些 变量 和 方法。

4、axios（ 或者 fetch 、ajax ）：用于发起 GET 、或 POST 等 http请求，基于 Promise 设计。

5、vux等：一个专为vue设计的移动端UI组件库。

6、创建一个emit.js文件，用于vue事件机制的管理。

7、webpack：模块加载和vue-cli工程打包器。

</details>

<b><details><summary>vue-cli 工程常用的 npm 命令有哪些？</summary></b>

下载 node_modules 资源包的命令：

npm install 
启动 vue-cli 开发环境的 npm命令：

npm run dev 
vue-cli 生成 生产环境部署资源 的 npm命令：

npm run build 
用于查看 vue-cli 生产环境部署资源文件大小的 npm命令：

npm run build --report
此命令必答，可以加深面试官好感！
命令效果：
![vue_001](../images/vue_001.jpg)

在浏览器上自动弹出一个 展示 vue-cli 工程打包后 app.js、manifest.js、vendor.js 文件里面所包含代码的页面。可以具此优化 vue-cli 生产环境部署的静态资源，提升 页面 的加载速度。

</details>

<b><details><summary>请说出vue-cli工程中每个文件夹和文件的用处</summary></b>

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

<b><details><summary>config文件夹 下 index.js 的对于工程 开发环境 和 生产环境 的配置</summary></b>

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

<b><details><summary>请你详细介绍一些 package.json 里面的配置</summary></b>

```
scripts：npm run xxx 命令调用node执行的 .js 文件
dependencies：生产环境依赖包的名称和版本号，即这些 依赖包 都会打包进 生产环境的JS文件里面
devDependencies：开发环境依赖包的名称和版本号，即这些 依赖包 只用于 代码开发 的时候，不会打包进 生产环境js文件 里面。
```

</details>

<b><details><summary>对于Vue是一套渐进式框架的理解</summary></b>

</details>

<b><details><summary>vue.js的两个核心是什么？</summary></b>

</details>

<b><details><summary>请问 v-if 和 v-show 有什么区别</summary></b>

</details>

<b><details><summary>vue常用的修饰符</summary></b>

</details>

<b><details><summary>v-on可以监听多个方法吗？</summary></b>

</details>

<b><details><summary>vue中 key 值的作用</summary></b>

</details>

<b><details><summary>vue-cli工程升级vue版本</summary></b>

</details>

<b><details><summary>vue事件中如何使用event对象？</summary></b>

</details>

<b><details><summary>$nextTick的使用</summary></b>

</details>

<b><details><summary>Vue 组件中 data 为什么必须是函数</summary></b>

</details>

<b><details><summary>v-for 与 v-if 的优先级</summary></b>

</details>

<b><details><summary>vue中子组件调用父组件的方法</summary></b>

</details>

<b><details><summary>vue中父组件调用子组件的方法</summary></b>

</details>

<b><details><summary>vue中 keep-alive 组件的作用</summary></b>

</details>

<b><details><summary>vue中如何编写可复用的组件？</summary></b>

</details>

<b><details><summary>什么是vue生命周期和生命周期钩子函数？</summary></b>

</details>

<b><details><summary>vue生命周期钩子函数有哪些？</summary></b>

</details>

<b><details><summary>vue如何监听键盘事件中的按键？</summary></b>

</details>

<b><details><summary>vue更新数组时触发视图更新的方法</summary></b>

</details>

<b><details><summary>vue中对象更改检测的注意事项</summary></b>

</details>

<b><details><summary>解决非工程化项目初始化页面闪动问题</summary></b>

</details>

<b><details><summary>v-for产生的列表，实现active的切换</summary></b>

</details>

<b><details><summary>22、v-model语法糖的组件中的使用</summary></b>

</details>

<b><details><summary>23、十个常用的自定义过滤器</summary></b>

</details>

<b><details><summary>24、vue等单页面应用及其优缺点</summary></b>

</details>

<b><details><summary>25、什么是vue的计算属性？</summary></b>

</details>

<b><details><summary>26、vue-cli提供的几种脚手架模板</summary></b>

</details>

<b><details><summary>27、vue父组件如何向子组件中传递数据？</summary></b>

</details>

<b><details><summary>28、vue-cli开发环境使用全局常量</summary></b>

</details>

<b><details><summary>29、vue-cli生产环境使用全局常量</summary></b>

</details>

<b><details><summary>30、vue弹窗后如何禁止滚动条滚动？</summary></b>

</details>

<b><details><summary>31、计算属性的缓存和方法调用的区别</summary></b>

</details>

<b><details><summary>32、vue-cli中自定义指令的使用</summary></b>

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