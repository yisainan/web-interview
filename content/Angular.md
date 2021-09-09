# [返回主页](https://github.com/yisainan/web-interview/blob/master/README.md)

<b><details><summary>1.angular 的数据绑定采用什么机制？详述原理</summary></b>

参考答案：脏检查机制。

解析：
双向数据绑定是 AngularJS 的核心机制之一。当 view 中有任何数据变化时，会更新到 model ，当 model 中数据有变化时，view 也会同步更新，显然，这需要一个监控。

原理就是，Angular 在 scope 模型上设置了一个监听队列，用来监听数据变化并更新 view 。每次绑定一个东西到 view 上时 AngularJS 就会往 $watch 队列里插入一条 $watch ，用来检测它监视的 model 里是否有变化的东西。当浏览器接收到可以被 angular context 处理的事件时， $digest 循环就会触发，遍历所有的 $watch ，最后更新 dom。

[参与互动](https://github.com/yisainan/web-interview/issues/525)

</details>

<b><details><summary>2. AngularJS 的数据双向绑定是怎么实现的？</summary></b>

参考答案：

1、每个双向绑定的元素都有一个 watcher

2、在某些事件发生的时候，调用 digest 脏数据检测。

这些事件有：表单元素内容变化、Ajax 请求响应、点击按钮执行的函数等。

3、脏数据检测会检测 rootscope 下所有被 watcher 的元素。

\$digest 函数就是脏数据监测

[参与互动](https://github.com/yisainan/web-interview/issues/526)

</details>

<b><details><summary>3. 在使用 angularjs 项目开发中 你使用过那些第三方的插件</summary></b>

参考答案：AngularUi ui-router oclazyload 等等 附上一篇文章仔细去看看 https://segmentfault.com/a/1190000003858219

[参与互动](https://github.com/yisainan/web-interview/issues/527)

</details>

<b><details><summary>4.ng-show/ng-hide 与 ng-if 的区别？</summary></b>

参考答案：我们都知道 ng-show/ng-hide 实际上是通过 display 来进行隐藏和显示的。而 ng-if 实际上控制 dom 节点的增删除来实现的。因此如果我们是根据不同的条件来进行 dom 节点的加载的话，那么 ng-if 的性能好过 ng-show.

[参与互动](https://github.com/yisainan/web-interview/issues/528)

</details>

<b><details><summary>5. 解释下什么是$rootScrope以及和$scope 的区别？</summary></b>

参考答案：通俗的说$rootScrope 页面所有$scope 的父亲。

解析：

我们来看下如何产生$rootScope和$scope 吧。

step1: Angular 解析 ng-app 然后在内存中创建\$rootScope。

step2:angular 回继续解析，找到{{}}表达式，并解析成变量。

step3: 接着会解析带有 ng-controller 的 div 然后指向到某个 controller 函数。 这个时候在这个 controller 函数变成一个\$scope 对象实例。

[参与互动](https://github.com/yisainan/web-interview/issues/529)

</details>

<b><details><summary>6. 列出至少三种实现不同模块之间通信方式？</summary></b>

参考答案：

* Service
* events, 指定绑定的事件
* 使用 \$rootScope
* controller 之间直接使用$parent, $\$childHead 等
* directive 指定属性进行数据绑定

[参与互动](https://github.com/yisainan/web-interview/issues/530)

</details>

<b><details><summary>7. 表达式 {{yourModel}} 是如何工作的？</summary></b>

参考答案：

它依赖于 $interpolation服务，在初始化页面html后，它会找到这些表达式，并且进行标记，于是每遇见一个 {{}} ，则会设置一个 $watch 。而 $interpolation 会返回一个带有上下文参数的函数，最后该函数执行，则算是表达式 $parse 到那个作用域上。

[参与互动](https://github.com/yisainan/web-interview/issues/531)

</details>

<b><details><summary>8.angular 中的\$http</summary></b>

参考答案：\$http 是 AngularJS 中的一个核心服务，用于读取远程服务器的数据。

我们可以使用内置的$http服务直接同外部进行通信。$http 服务只是简单的封装了浏览器原生的 XMLHttpRequest 对象。

[参与互动](https://github.com/yisainan/web-interview/issues/532)

</details>

<b><details><summary>9.ng-repeat 迭代数组的时候，如果数组中有相同值，会有什么问题，如何解决？</summary></b>

参考答案：会提示 Duplicates in a repeater are not allowed. 加 track by \$index 可解决。当然，也可以 trace by 任何一个普通的值，只要能唯一性标识数组中的每一项即可（建立 dom 和数据之间的关联）

[参与互动](https://github.com/yisainan/web-interview/issues/533)

</details>

<b><details><summary>10.angularjs 是 mvc 还是 mvvm 框架</summary></b>

参考答案：mvvm

解析：

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

[参与互动](https://github.com/yisainan/web-interview/issues/534)

</details>

<b><details><summary>11.angularjs 中\$scope，controller，directive，sevice 在 mvvm 中充当什么角色</summary></b>

参考答案：如果你不知道，第一题的分析以及很明确，仔细再仔细的看一遍

[参与互动](https://github.com/yisainan/web-interview/issues/535)

</details>

<b><details><summary>12. 在 angular 项目中你如何控制静态资源的合理加载</summary></b>

参考答案：

[参与互动](https://github.com/yisainan/web-interview/issues/536)

</details>

<b><details><summary>13. 在写 controlloer 逻辑的时候 你需要注意什么？</summary></b>

参考答案：

1. 简化代码（这个是所有开发人员都要具备的）

2. 坚决不能操作 dom 节点 这个时候可能会问 为什么不能啊

你的回答是：DOM 操作只能出现在指令（directive）中。最不应该出现的位置就是服务（service）中。Angular 倡导以测试驱动开发，在 service 或者 controller 中出现了 DOM 操作，那么也就意味着的测试是无法通过的。当然，这只是一点，重要的是使用 Angular 的其中一个好处是啥，那就是双向数据绑定，这样就能专注于处理业务逻辑，无需关系一堆堆的 DOM 操作。如果在 Angular 的代码中还到处充斥着各种 DOM 操作，那为什么不直接使用 jquery 去开发呢。

测试驱动开发是什么呢？普及一下：

测试驱动开发，英文全称 Test-Driven Development，简称 TDD，是一种不同于传统软件开发流程的新型的开发方法。它要求在编写某个功能的代码之前先编写测试代码，然后只编写使测试通过的功能代码，通过测试来推动整个开发的进行。这有助于编写简洁可用和高质量的代码，并加速开发过程。

[参与互动](https://github.com/yisainan/web-interview/issues/537)

</details>

<b><details><summary>14.controller 之间怎么通讯</summary></b>

参考答案：

1、event

这里可以有两种方式，一种是$scope.$emit，然后通过监听$rootScope的事件获取参数；另一种是$rootScope.$broadcast，通过监听$scope 的事件获取参数。

这两种方法在最新版本的 Angular 中已经没有性能区别了，主要就是事件发送的方向不同，可以按实际情况选择。

2、service

可以创建一个专用的事件 Service，也可以按照业务逻辑切分，将数据存储在相应的 Service 中

3、\$rootScope

这个方法可能会比较 dirty 一点，胜在方便，也就是把数据存在$rootScope中，这样各个子$scope 都可以调用，不过需要注意一下生命周期

4、直接使用$scope.$\$nextSibling 及类似的属性

类似的还有$scope.$parent。这个方法的缺点就更多了，官方不推荐使用任何\$\$开头的属性，既增加了耦合，又需要处理异步的问题，而且 scope 的顺序也不是固定的。不推荐

另外就是通过本地存储、全局变量或者现代浏览器的 postMessage 来传递参数了，除非特殊情况，请避免这类方式。

[参与互动](https://github.com/yisainan/web-interview/issues/538)

</details>

<b><details><summary>15. 自定义指令的几个参数</summary></b>

参考答案：

说几个常用的如：

restrict: 指令在 dom 中的声明形式 E（元素）A（属性）C（类名）M（注释）

template：两种形式，一种 HTML 文本；一个可以接受两个参数的函数，tElemetn 和 tAttrs，并返回一个代表模板的字符串。模板字符串必须存在一个根 DOM 元素

templateUrl: 两种形式，一种代表外部 HTML 文件路径的字符串；一个可以接受两个参数的函数，参数为 tElement 和 tAttrs，并返回一个外部 HTML 文件路径的字符串

compile (对象或函数)：compile 选项可以返回一个对象或函数。如果设置了 compile 函数, 说明我们希望在指令和实时数据被放到 DOM 中之前进行 DOM 操作, 在这个函数中进行诸如添加和删除节点等 DOM 操作是安全的。本质上, 当我们设置了 link 选项, 实际上是创建了一个 postLink() 链接函数, 以便 compile() 函数可以定义链接函数。

然后又是传送门：http://www.cnblogs.com/mliudong/p/4180680.html

compile 和 link 的区别：

编译的时候，compile 转换 dom，碰到绑定监听器的地方就先存着，有几个存几个，到最后汇总成一个 link 函数，一并执行，提升了性能。

[参与互动](https://github.com/yisainan/web-interview/issues/539)

</details>

<b><details><summary>16.angular 和 jquery 的区别</summary></b>

参考答案：

angular 是基于数据驱动，所以 angular 适合做数据操作比较繁琐的项目（这里可以再提一下单页面应用，如果你不会福利又来了 http://www.zhihu.com/question/20792064）

jquery 是基于 dom 驱动，jquery 适合做 dom 操作多的项目

[参与互动](https://github.com/yisainan/web-interview/issues/540)

</details>

<b><details><summary>17. 对 angular 中的 form 表单了解多少</summary></b>

参考答案：

Angular 对 input 元素的 type 进行了扩展，一共提供了以下 10 种类型：

text

number

url

email

radio

checkbox

hidden

button

submit

reset

Angular 为表单内置了 4 中 CSS 样式。

ng-valid 校验合法状态

ng-invalid 校验非法状态

ng-pristine 如果要使用原生的 form，需要设置这个值

ng-dirty      表单处于脏数据状态

Angular 在对表单进行自动校验的时候会校验 Model 上的属性，如果不设置 ng-model，则 Angular 无法知道 myForm.\$invalid 这个值是否为真。

校验的一下内容

required 表示是否输入内容

ng-maxlength 最大长度

ng-minlength 最小长度

例子：传送门https://github.com/18500047564/clutter

[参与互动](https://github.com/yisainan/web-interview/issues/541)

</details>

<b><details><summary>18.fliter 是什么你了解的有多少？实现一个自定义 fliter</summary></b>

参考答案：

date（日期）

currency（货币）

limitTo（限制数组或字符串长度）

orderBy（排序）

lowercase（小写）

uppercase（大写）

number（格式化数字，加上千位分隔符，并接收参数限定小数点位数）

filter（处理一个数组，过滤出含有某个子串的元素）

json（格式化 json 对象）

filter 有两种使用方法，

一种是直接在页面里：

```html
<p>{{now | date : ‘yyyy-MM-dd’}}</p>
```

另一种是在 js 里面用：

\$filter('过滤器名称')(需要过滤的对象, 参数 1, 参数 2, ...)

\$filter('date')(now, 'yyyy-MM-dd hh:mm:ss’); 

自定义一个去重数组的

```js
app.filter("unique", function() {
    return function(arr) {
        var n = [];
        var obj = {};

        for (var i = 0; i < arr.length; i++) {
            if (!obj[arr[i]]) {
                n.push(arr[i]);
                obj[arr[i]] = 1;
            }
        }

        return n;
    };
});
```

[参与互动](https://github.com/yisainan/web-interview/issues/542)

</details>
