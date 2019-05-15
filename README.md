# web-interview

<b><details><summary>💡 关于</summary></b>

📚 本仓库是面向 <b>web 前端</b> 方向校招求职者、初学者的基础知识总结

🙏 仓库内容如有错误或改进欢迎 issue 或 pr。由于本人水平有限，仓库中的知识点有来自本人原创、读书笔记、书籍、博文等，非原创均已标明出处，如有遗漏，请 issue 提出。本仓库遵循 CC BY-NC-SA 4.0 协议，转载请注明出处。

</details>

<b><details><summary>➕ [HTML](./HTML.md)</summary></b>

</details>

<b><details><summary>📦 CSS</summary></b>

- <details><summary>1.介绍一下标准的CSS的盒子模型？低版本IE的盒子模型有什么不同的？</summary>

  （1）有两种， IE 盒子模型、W3C 盒子模型；

  （2）盒模型： 内容(content)、填充(padding)、边界(margin)、 边框(border)；

  （3）区 别： IE 的 content 部分把 border 和 padding 计算了进去;

  </details>

- <details><summary>2.CSS隐藏元素的几种方法（至少说出三种）</summary>

  Opacity:元素本身依然占据它自己的位置并对网页的布局起作用。它也将响应用户交互;

  Visibility:与 opacity 唯一不同的是它不会响应任何用户交互。此外，元素在读屏软件中也会被隐藏;

  Display:display 设为 none 任何对该元素直接打用户交互操作都不可能生效。此外，读屏软件也不会读到元素的内容。这种方式产生的效果就像元素完全不存在;

  Position:不会影响布局，能让元素保持可以操作;

  Clip-path:clip-path 属性还没有在 IE 或者 Edge 下被完全支持。如果要在你的 clip-path 中使用外部的 SVG 文件，浏览器支持度还要低;

  </details>

- <details><summary>3.CSS清除浮动的几种方法（至少两种）</summary>

  使用带 clear 属性的空元素

  使用 CSS 的 overflow 属性；

  使用 CSS 的:after 伪元素；

  使用邻接元素处理；

  </details>

- <details><summary>4.页面导入样式时，使用link和@import有什么区别？</summary>

  link 属于 XHTML 标签，除了加载 CSS 外，还能用于定义 RSS, 定义 rel 连接属性等作用；而@import 是 CSS 提供的，只能用于加载 CSS;
  页面被加载的时，link 会同时被加载，而@import 引用的 CSS 会等到页面被加载完再加载;

  import 是 CSS2.1 提出的，只在 IE5 以上才能被识别，而 link 是 XHTML 标签，无兼容问题;

  </details>

- <details><summary>5.CSS 选择符有哪些？哪些属性可以继承？优先级算法如何计算？ CSS3新增伪类有那些？</summary>

  id 选择器（ # myid）

  类选择器（.myclassname）

  标签选择器（div, h1, p）

  相邻选择器（h1 + p）

  子选择器（ul > li）

  后代选择器（li a）

  通配符选择器（ \* ）

  属性选择器（a[rel = “external”]）

  伪类选择器（a: hover, li: nth – child）

  可继承的样式： font-size font-family color, UL LI DL DD DT;

  不可继承的样式：border padding margin width height ;

  优先级就近原则，同权重情况下样式定义最近者为准;

  优先级为:

  !important > id > class > tag

  important 比 内联优先级高

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

</details>

<b><details><summary>〽️ JS</summary></b>

- <details><summary>1. JavaScript中如何检测一个变量是一个String类型？请写出函数实现</summary>

  typeof(obj) === "string"
  typeof obj === "string"
  obj.constructor === String

  </details>

- <details><summary>2.请用js去除字符串空格？</summary>

  方法一：使用 replace 正则匹配的方法
  方法二：使用 str.trim()方法
  方法三：使用 jquery,\$.trim(str)方法

  </details>

- <details><summary>3.你如何获取浏览器URL中查询字符串中的参数？</summary>

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

- <details><summary>4.怎样添加、移除、移动、复制、创建和查找节点？</summary>

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

- <details><summary>5.事件委托是什么</summary>

  让利用事件冒泡的原理，让自己的所触发的事件，让他的父元素代替执行！

  </details>

- <details><summary>6.你对闭包的理解？</summary>

  </details>

</details>

<b><details><summary>⚡️ Vue</summary></b>

- <details><summary>1.vue中的性能优化</summary>

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

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

</details>

<b><details><summary>❓ React</summary></b>

- <details><summary>1.当你调用setState的时候，发生了什么事？</summary>

  将传递给 setState 的对象合并到组件的当前状态，这将启动一个和解的过程，构建一个新的 react 元素树，与上一个元素树进行对比（ diff ），从而进行最小化的重渲染。

  </details>

- <details><summary>2.在 React 当中 Element 和 Component 有何区别？</summary>

  React Element 是描述屏幕上所见内容的数据结构，是对于 UI 的对象表述。典型的 React Element 就是利用 JSX 构建的声明式代码片然后被转化为 createElement 的调用组合。

  React Component 是一个函数或一个类，可以接收参数输入，并且返回某个 React Element

  </details>

- <details><summary>3.什么时候在功能组件( Class Component )上使用类组件( Functional Component )？</summary>

  如果您的组件具有状态( state )或生命周期方法，请使用 Class 组件。否则，使用功能组件

  </details>

- <details><summary></summary>

  </details>

</details>

<b><details><summary>💻 Angular </summary></b>

- <details><summary>1.angular的数据绑定采用什么机制？详述原理</summary>

  脏检查机制。

  双向数据绑定是 AngularJS 的核心机制之一。当 view 中有任何数据变化时，会更新到 model ，当 model 中数据有变化时，view 也会同步更新，显然，这需要一个监控。

  原理就是，Angular 在 scope 模型上设置了一个监听队列，用来监听数据变化并更新 view 。每次绑定一个东西到 view 上时 AngularJS 就会往 $watch 队列里插入一条 $watch ，用来检测它监视的 model 里是否有变化的东西。当浏览器接收到可以被 angular context 处理的事件时， $digest 循环就会触发，遍历所有的 $watch ，最后更新 dom。

  </details>

- <details><summary>2.AngularJS的数据双向绑定是怎么实现的？</summary>

  1、每个双向绑定的元素都有一个 watcher

  2、在某些事件发生的时候，调用 digest 脏数据检测。

  这些事件有：表单元素内容变化、Ajax 请求响应、点击按钮执行的函数等。

  3、脏数据检测会检测 rootscope 下所有被 watcher 的元素。

  \$digest 函数就是脏数据监测

  </details>

- <details><summary>3.在使用angularjs项目开发中 你使用过那些第三方的插件</summary>

  AngularUi ui-router oclazyload 等等 附上一篇文章仔细去看看 https://segmentfault.com/a/1190000003858219

  </details>

- <details><summary>4.ng-show/ng-hide 与 ng-if的区别？</summary>

  我们都知道 ng-show/ng-hide 实际上是通过 display 来进行隐藏和显示的。而 ng-if 实际上控制 dom 节点的增删除来实现的。因此如果我们是根据不同的条件来进行 dom 节点的加载的话，那么 ng-if 的性能好过 ng-show.

  </details>

- <details><summary>5.解释下什么是$rootScrope以及和$scope的区别？</summary>

  通俗的说$rootScrope 页面所有$scope 的父亲。

  我们来看下如何产生$rootScope和$scope 吧。

  step1:Angular 解析 ng-app 然后在内存中创建\$rootScope。

  step2:angular 回继续解析，找到{{}}表达式，并解析成变量。

  step3:接着会解析带有 ng-controller 的 div 然后指向到某个 controller 函数。 这个时候在这个 controller 函数变成一个\$scope 对象实例。

  </details>

- <details><summary>6.列出至少三种实现不同模块之间通信方式？</summary>

  Service

  events,指定绑定的事件

  使用 \$rootScope

  controller 之间直接使用$parent, $\$childHead 等

  directive 指定属性进行数据绑定

  </details>

- <details><summary>7. 表达式 {{yourModel}} 是如何工作的？</summary>

  它依赖于 $interpolation服务，在初始化页面html后，它会找到这些表达式，并且进行标记，于是每遇见一个 {{}} ，则会设置一个 $watch 。而 $interpolation 会返回一个带有上下文参数的函数，最后该函数执行，则算是表达式 $parse 到那个作用域上。

  </details>

- <details><summary>8.angular中的$http</summary>

  \$http 是 AngularJS 中的一个核心服务，用于读取远程服务器的数据。

  我们可以使用内置的$http服务直接同外部进行通信。$http 服务只是简单的封装了浏览器原生的 XMLHttpRequest 对象。

  </details>

- <details><summary>9.ng-repeat迭代数组的时候，如果数组中有相同值，会有什么问题，如何解决？</summary>

  会提示 Duplicates in a repeater are not allowed. 加 track by \$index 可解决。当然，也可以 trace by 任何一个普通的值，只要能唯一性标识数组中的每一项即可（建立 dom 和数据之间的关联）

  </details>

- <details><summary>10.angularjs 是mvc还是mvvm框架</summary>

  首先阐述下你对 mvc 和 mvvm 的理解:

  首先为什么我们会需要 MVC？因为随着代码规模越来越大，切分职责是大势所趋，还有为了后期维护方便，修改一块功能不影响其他功能。还有为了复用，因为很多逻辑是一样的。而 MVC 只是手段，终极目标是模块化和复用。

  mvvm 的优点

  低耦合：View 可以独立于 Model 变化和修改，同一个 ViewModel 可以被多个 View 复用；并且可以做到 View 和 Model 的变化互不影响；

  可重用性：可以把一些视图的逻辑放在 ViewModel，让多个 View 复用；

  独立开发：开发人员可以专注与业务逻辑和数据的开发（ViewModemvvmdi 计人员可以专注于 UI(View)的设计；

  可测试性：清晰的 View 分层，使得针对表现层业务逻辑的测试更容易，更简单。

  在 angular 中 MVVM 模式主要分为四部分：

  View：它专注于界面的显示和渲染，在 angular 中则是包含一堆声明式 Directive 的视图模板。

  ViewModel：它是 View 和 Model 的粘合体，负责 View 和 Model 的交互和协作，它负责给 View 提供显示的数据，以及提供了 View 中 Command 事件操作 Model 的途径；在 angular 中\$scope 对象充当了这个 ViewModel 的角色；

  Model：它是与应用程序的业务逻辑相关的数据的封装载体，它是业务领域的对象，Model 并不关心会被如何显示或操作，所以模型也不会包含任何界面显示相关的逻辑。在 web 页面中，大部分 Model 都是来自 Ajax 的服务端返回数据或者是全局的配置对象；而 angular 中的 service 则是封装和处理这些与 Model 相关的业务逻辑的场所，这类的业务服务是可以被多个 Controller 或者其他 service 复用的领域服务。

  Controller：这并不是 MVVM 模式的核心元素，但它负责 ViewModel 对象的初始化，它将组合一个或者多个 service 来获取业务领域 Model 放在 ViewModel 对象上，使得应用界面在启动加载的时候达到一种可用的状态。

  mvc 的界面和逻辑关联紧密，数据直接从数据库读取。mvvm 的界面与 viewmode 是松耦合，界面数据从 viewmodel 中获取。所以 angularjs 更倾向于 mvvm

  </details>

- <details><summary>11.angularjs中$scope，controller，directive，sevice在mvvm中充当什么角色</summary>

  如果你不知道，第一题的分析以及很明确，仔细再仔细的看一遍

  </details>

- <details><summary>12.在使用angularjs项目开发中 你使用过那些第三方的插件</summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

</details>

<b><details><summary>☁️ 计算机网络</summary></b>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

</details>

<b><details><summary>🌩 网络编程</summary></b>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

</details>

<b><details><summary>💾 数据库</summary></b>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

</details>

<b><details><summary>📏 设计模式</summary></b>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

</details>

<b><details><summary>⚙️ 链接装载库</summary></b>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

</details>

<b><details><summary>📚 书籍</summary></b>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

</details>

<b><details><summary>🔱 C/C++ 发展方向</summary></b>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

- <details><summary></summary>

  </details>

</details>

<b><details><summary>👬 贡献者</summary></b>

包括勘误的 Issue、PR，排序按照贡献时间。

[tamarous](https://github.com/tamarous)

</details>

<b><details><summary>📜 License</summary></b>

本仓库遵循 CC BY-NC-SA 4.0（署名 - 非商业性使用） 协议，转载请注明出处。

[![CC BY-NC-SA 4.0](https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png)](LICENSE)

</details>
