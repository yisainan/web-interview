# [返回主页](https://github.com/yisainan/web-interview/blob/master/README.md)

<b><details><summary>1.什么是 MVVM？</summary></b>

答案：1.拆分说明（M，V，VM 都是干啥的） 2.之间联系（Model 和 ViewModel 的双向数据绑定）

解析：

MVVM 是 Model-View-ViewModel 的缩写。MVVM 是一种设计思想。Model 层代表数据模型，也可以在 Model 中定义数据修改和操作的业务逻辑；View 代表 UI 组件，它负责将数据模型转化成 UI 展现出来，ViewModel 是一个同步 View 和 Model 的对象（桥梁）。

在 MVVM 架构下，View 和 Model 之间并没有直接的联系，而是通过 ViewModel 进行交互，Model 和 ViewModel 之间的交互是双向的， 因此 View 数据的变化会同步到 Model 中，而 Model 数据的变化也会立即反应到 View 上。

ViewModel 通过双向数据绑定把 View 层和 Model 层连接了起来，而 View 和 Model 之间的同步工作完全是自动的，无需人为干涉，因此开发者只需关注业务逻辑，不需要手动操作 DOM, 不需要关注数据状态的同步问题，复杂的数据状态维护完全由 MVVM 来统一管理。

</details>

<b><details><summary>2、MVC、MVP 与 MVVM 模式</summary></b>

答案：

一、MVC

通信方式如下

![架构_001](../../images/架构_001.png)

1. 视图（View）：用户界面。 传送指令到 Controller

2. 控制器（Controller）：业务逻辑 完成业务逻辑后，要求 Model 改变状态

3. 模型（Model）：数据保存 将新的数据发送到 View，用户得到反馈

二、MVP

通信方式如下

![架构_002](../../images/架构_002.png)

1. 各部分之间的通信，都是双向的。

2. View 与 Model 不发生联系，都通过 Presenter 传递。

3. View 非常薄，不部署任何业务逻辑，称为"被动视图"（Passive View），即没有任何主动性，而 Presenter 非常厚，所有逻辑都部署在那里。

五、MVVM

MVVM 模式将 Presenter 改名为 ViewModel，基本上与 MVP 模式完全一致。通信方式如下

![架构_003](../../images/架构_003.png)

唯一的区别是，它采用双向绑定（data-binding）：View 的变动，自动反映在 ViewModel，反之亦然。

</details>

<b><details><summary>3、常见的实现 MVVM 几种方式</summary></b>

答案：

</details>

<b><details><summary>4、解释下 Object.defineProperty()方法</summary></b>

答案：这是 js 中一个非常重要的方法，ES6 中某些方法的实现依赖于它，VUE 通过它实现双向绑定，此方法会直接在一个对象上定义一个新属性，或者修改一个已经存在的属性， 并返回这个对象

解析：

## 语法

Object.defineProperty(object, attribute, descriptor)

- 这三个参数都是必输项
- 第一个参数为 目标对象
- 第二个参数为 需要定义的属性或者方法
- 第三个参数为 目标属性所拥有的特性

## descriptor

前两个参数都很明确，重点是第三个参数 descriptor， 它有以下取值

- value: 属性的值
- writable: 属性的值是否可被重写（默认为 false）
- configurable: 总开关，是否可配置，若为 false, 则其他都为 false（默认为 false）
- enumerable: 属性是否可被枚举（默认为 false）
- get: 获取该属性的值时调用
- set: 重写该属性的值时调用

一个例子

```js
var a = {};
Object.defineProperty(a, "b", {
  value: 123
});
console.log(a.b); //123
a.b = 456;
console.log(a.b); //123
a.c = 110;
for (item in a) {
  console.log(item, a[item]); //c 110
}
```

因为 writable 和 enumerable 默认值为 false, 所以对 a.b 赋值无效，也无法遍历它

## configurable

总开关，是否可配置，设置为 false 后，就不能再设置了，否则报错， 例子

```js
var a = {};
Object.defineProperty(a, "b", {
  configurable: false
});
Object.defineProperty(a, "b", {
  configurable: true
});
//error: Uncaught TypeError: Cannot redefine property: b
```

## writable

是否可重写

```js
var a = {};
Object.defineProperty(a, "b", {
  value: 123,
  writable: false
});
console.log(a.b); // 打印 123
a.b = 25; // 没有错误抛出（在严格模式下会抛出，即使之前已经有相同的值）
console.log(a.b); // 打印 123， 赋值不起作用。
```

## enumerable

属性特性 enumerable 定义了对象的属性是否可以在 for...in 循环和 Object.keys() 中被枚举

```js
var a = {};
Object.defineProperty(a, "b", {
  value: 3445,
  enumerable: true
});
console.log(Object.keys(a)); // 打印["b"]
```

enumerable 改为 false

```js
var a = {};
Object.defineProperty(a, "b", {
  value: 3445,
  enumerable: false //注意咯这里改了
});
console.log(Object.keys(a)); // 打印[]
```

## set 和 get

如果设置了 set 或 get, 就不能设置 writable 和 value 中的任何一个，否则报错

```js
var a = {};
Object.defineProperty(a, "abc", {
  value: 123,
  get: function() {
    return value;
  }
});
//Uncaught TypeError: Invalid property descriptor. Cannot both specify accessors and a value or writable attribute, #<Object> at Function.defineProperty
```

对目标对象的目标属性 赋值和取值 时， 分别触发 set 和 get 方法

```js
var a = {};
var b = 1;
Object.defineProperty(a, "b", {
  set: function(newValue) {
    b = 99;
    console.log("你要赋值给我,我的新值是" + newValue);
  },
  get: function() {
    console.log("你取我的值");
    return 2; //注意这里，我硬编码返回2
  }
});
a.b = 1; //打印 你要赋值给我,我的新值是1
console.log(b); //打印 99
console.log(a.b); //打印 你取我的值
//打印 2    注意这里，和我的硬编码相同的
```

上面的代码中，给 a.b 赋值，b 的值也跟着改变了。原因是给 a.b 赋值，自动调用了 set 方法，在 set 方法中改变了 b 的值。vue 双向绑定的原理就是这个。

扩展：[参考](https://www.cnblogs.com/zhaowj/p/9576450.html)

</details>

<b><details><summary>5、实现一个自己的 MVVM（原理剖析）</summary></b>

答案：

</details>

<b><details><summary>10、递归组件的使用</summary></b>

答案：组件是可以在自己的模板中调用自身的，不过他们只能通过name选项来做这件事

解析：

</details>

<b><details><summary>11、Obj.keys()与 Obj.defineProperty</summary></b>

答案：

</details>

<b><details><summary>12、发布-订阅模式</summary></b>

答案：

</details>

<b><details><summary>13、实现 MVVM 的思路分析</summary></b>

答案：

</details>

<b><details><summary>14.mvvm 和 mvc 区别？它和其它框架（jquery）的区别是什么？哪些场景适合？</summary></b>

答案：

mvc 和 mvvm 其实区别并不大。都是一种设计思想。主要就是 mvc 中 Controller 演变成 mvvm 中的 viewModel。mvvm 主要解决了 mvc 中大量的 DOM 操作使页面渲染性能降低，加载速度变慢，影响用户体验。

区别：vue 数据驱动，通过数据来显示视图层而不是节点操作。

场景：数据操作比较多的场景，更加便捷

</details>
