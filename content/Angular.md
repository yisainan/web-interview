# [返回主页](../README.md)

<b><details><summary>1.angular的数据绑定采用什么机制？详述原理</summary></b>

  脏检查机制。

  双向数据绑定是 AngularJS 的核心机制之一。当 view 中有任何数据变化时，会更新到 model ，当 model 中数据有变化时，view 也会同步更新，显然，这需要一个监控。

  原理就是，Angular 在 scope 模型上设置了一个监听队列，用来监听数据变化并更新 view 。每次绑定一个东西到 view 上时 AngularJS 就会往 $watch 队列里插入一条 $watch ，用来检测它监视的 model 里是否有变化的东西。当浏览器接收到可以被 angular context 处理的事件时， $digest 循环就会触发，遍历所有的 $watch ，最后更新 dom。

</details>

<b><details><summary>2.AngularJS的数据双向绑定是怎么实现的？</summary></b>

  1、每个双向绑定的元素都有一个 watcher

  2、在某些事件发生的时候，调用 digest 脏数据检测。

  这些事件有：表单元素内容变化、Ajax 请求响应、点击按钮执行的函数等。

  3、脏数据检测会检测 rootscope 下所有被 watcher 的元素。

  \$digest 函数就是脏数据监测

</details>

<b><details><summary>3.在使用angularjs项目开发中 你使用过那些第三方的插件</summary></b>

  AngularUi ui-router oclazyload 等等 附上一篇文章仔细去看看 https://segmentfault.com/a/1190000003858219

</details>

<b><details><summary>4.ng-show/ng-hide 与 ng-if的区别？</summary></b>

  我们都知道 ng-show/ng-hide 实际上是通过 display 来进行隐藏和显示的。而 ng-if 实际上控制 dom 节点的增删除来实现的。因此如果我们是根据不同的条件来进行 dom 节点的加载的话，那么 ng-if 的性能好过 ng-show.

</details>

<b><details><summary>5.解释下什么是$rootScrope以及和$scope的区别？</summary></b>

  通俗的说$rootScrope 页面所有$scope 的父亲。

  我们来看下如何产生$rootScope和$scope 吧。

  step1:Angular 解析 ng-app 然后在内存中创建\$rootScope。

  step2:angular 回继续解析，找到{{}}表达式，并解析成变量。

  step3:接着会解析带有 ng-controller 的 div 然后指向到某个 controller 函数。 这个时候在这个 controller 函数变成一个\$scope 对象实例。

</details>

<b><details><summary>6.列出至少三种实现不同模块之间通信方式？</summary></b>

  Service

  events,指定绑定的事件

  使用 \$rootScope

  controller 之间直接使用$parent, $\$childHead 等

  directive 指定属性进行数据绑定

</details>

<b><details><summary>7. 表达式 {{yourModel}} 是如何工作的？</summary></b>

  它依赖于 $interpolation服务，在初始化页面html后，它会找到这些表达式，并且进行标记，于是每遇见一个 {{}} ，则会设置一个 $watch 。而 $interpolation 会返回一个带有上下文参数的函数，最后该函数执行，则算是表达式 $parse 到那个作用域上。

</details>

<b><details><summary>8.angular中的$http</summary></b>

  \$http 是 AngularJS 中的一个核心服务，用于读取远程服务器的数据。

  我们可以使用内置的$http服务直接同外部进行通信。$http 服务只是简单的封装了浏览器原生的 XMLHttpRequest 对象。

</details>

<b><details><summary>9.ng-repeat迭代数组的时候，如果数组中有相同值，会有什么问题，如何解决？</summary></b>

  会提示 Duplicates in a repeater are not allowed. 加 track by \$index 可解决。当然，也可以 trace by 任何一个普通的值，只要能唯一性标识数组中的每一项即可（建立 dom 和数据之间的关联）

</details>

<b><details><summary>10.angularjs 是mvc还是mvvm框架</summary></b>

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

<b><details><summary>11.angularjs中$scope，controller，directive，sevice在mvvm中充当什么角色</summary></b>

  如果你不知道，第一题的分析以及很明确，仔细再仔细的看一遍

</details>

<b><details><summary>12.在使用angularjs项目开发中 你使用过那些第三方的插件</summary></b>

</details>

<b><details><summary></summary></b>

</details>

<b><details><summary></summary></b>

</details>

<b><details><summary></summary></b>

</details>
