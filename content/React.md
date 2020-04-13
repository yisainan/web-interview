# [返回主页](https://github.com/yisainan/web-interview/blob/master/README.md)

<b><details><summary>1.当你调用 setState 的时候，发生了什么事？</summary></b>

答案：将传递给 setState 的对象合并到组件的当前状态，这将启动一个和解的过程，构建一个新的 react 元素树，与上一个元素树进行对比（ diff ），从而进行最小化的重渲染。

[参与互动](https://github.com/yisainan/web-interview/issues/496)

</details>

<b><details><summary>2.React 项目用过什么脚手架（本题是开放性题目）</summary></b>

答案：creat-react-app Yeoman 等

[参与互动](https://github.com/yisainan/web-interview/issues/497)

</details>
    
<b><details><summary>3.什么时候在功能组件( Class Component )上使用类组件( Functional Component )？</summary></b>

答案：如果您的组件具有状态( state ) 或 生命周期方法，请使用 Class 组件。否则，使用功能组件

[参与互动](https://github.com/yisainan/web-interview/issues/498)

</details>

<b><details><summary>4.React 中 keys 的作用是什么？</summary></b>

答案：Keys 是 React 用于追踪哪些列表中元素被修改、被添加或者被移除的辅助标识。

```js
render () {
  return (
    <ul>
      {this.state.todoItems.map(({item, key}) => {
        return <li key={key}>{item}</li>
      })}
    </ul>
  )
}
```

在开发过程中，我们需要保证某个元素的 key 在其同级元素中具有唯一性。在 React Diff 算法中 React 会借助元素的 Key 值来判断该元素是新近创建的还是被移动而来的元素，从而减少不必要的元素重渲染。此外，React 还需要借助 Key 值来判断元素与本地状态的关联关系，因此我们绝不可忽视转换函数中 Key 的重要性。

[参与互动](https://github.com/yisainan/web-interview/issues/499)

</details>

<b><details><summary>5.React 优势</summary></b>

答案：

1、React 速度很快：它并不直接对 DOM 进行操作，引入了一个叫做虚拟 DOM 的概念，安插在 javascript 逻辑和实际的 DOM 之间，性能好。

2、跨浏览器兼容：虚拟 DOM 帮助我们解决了跨浏览器问题，它为我们提供了标准化的 API，甚至在 IE8 中都是没问题的。

3、一切都是 component：代码更加模块化，重用代码更容易，可维护性高。

4、单向数据流：Flux 是一个用于在 JavaScript 应用中创建单向数据层的架构，它随着 React 视图库的开发而被 Facebook 概念化。

5、同构、纯粹的 javascript：因为搜索引擎的爬虫程序依赖的是服务端响应而不是 JavaScript 的执行，预渲染你的应用有助于搜索引擎优化。

6、兼容性好：比如使用 RequireJS 来加载和打包，而 Browserify 和 Webpack 适用于构建大型应用。它们使得那些艰难的任务不再让人望而生畏。

[参与互动](https://github.com/yisainan/web-interview/issues/500)

</details>

<b><details><summary>6.React 很多个 setState 为什么是执行完再 render</summary></b>

答案：react为了提高整体的渲染性能，会将一次渲染周期中的state进行合并，在这个渲染周期中你对所有setState的所有调用都会被合并起来之后，再一次性的渲染，这样可以避免频繁的调用setState导致频繁的操作dom，提高渲染性能。具体的实现方面，可以简单的理解为react中存在一个状态变量isBatchingUpdates，当处于渲染周期开始时，这个变量会被设置成true，渲染周期结束时，会被设置成false，react会根据这个状态变量，当出在渲染周期中时，仅仅只是将当前的改变缓存起来，等到渲染周期结束时，再一次性的全部render。

[参与互动](https://github.com/yisainan/web-interview/issues/501)

</details>

<b><details><summary>7.react diff 原理（常考，大厂必考）</summary></b>

答案：把树形结构按照层级分解，只比较同级元素。

给列表结构的每个单元添加唯一的 key 属性，方便比较。

React 只会匹配相同 class 的 component（这里面的 class 指的是组件的名字）
合并操作，调用 component 的 setState 方法的时候, React 将其标记为 dirty.到每一个事件循环结束, React 检查所有标记 dirty 的 component 重新绘制.

选择性子树渲染。开发人员可以重写 shouldComponentUpdate 提高 diff 的性能。

[参与互动](https://github.com/yisainan/web-interview/issues/502)

</details>

<b><details><summary>8.react 生命周期函数</summary></b>

答案：

- 初始化阶段：
  - getDefaultProps:获取实例的默认属性
  - getInitialState:获取实例的初始化状态
  - componentWillMount：组件即将被装载、渲染到页面上
  - render:组件在这里生成虚拟的 DOM 节点
  - componentDidMount:组件真正在被装载之后
- 运行中阶段：
  - componentWillReceiveProps:组件将要接收到属性的时候调用
  - shouldComponentUpdate:组件接受到新属性或者新状态的时候（可以返回 false，接收数据后不更新，阻止 render 调用，后面的函数不会被继续执行了）
  - componentWillUpdate:组件即将更新不能修改属性和状态
  - render:组件重新描绘
  - componentDidUpdate:组件已经更新
- 销毁阶段：
  - componentWillUnmount:组件即将销毁

解析：有三大阶段，每阶段的细分 5-5-1

[参与互动](https://github.com/yisainan/web-interview/issues/503)

</details>

<b><details><summary>9.shouldComponentUpdate 是做什么的？（react 性能优化是哪个周期函数？）</summary></b>

答案：

shouldComponentUpdate 这个方法用来判断是否需要调用 render 方法重新描绘 dom。因为 dom 的描绘非常消耗性能，如果我们能在 shouldComponentUpdate 方法中能够写出更优化的 dom diff 算法，可以极大的提高性能。

[参与互动](https://github.com/yisainan/web-interview/issues/504)

</details>

<b><details><summary>10.为什么虚拟 dom 会提高性能?(必考)</summary></b>

答案：

虚拟 dom 相当于在 js 和真实 dom 中间加了一个缓存，利用 dom diff 算法避免了没有必要的 dom 操作，从而提高性能。

用 JavaScript 对象结构表示 DOM 树的结构；然后用这个树构建一个真正的 DOM 树，插到文档当中当状态变更的时候，重新构造一棵新的对象树。然后用新的树和旧的树进行比较，记录两棵树差异把 2 所记录的差异应用到步骤 1 所构建的真正的 DOM 树上，视图就更新了。

[参与互动](https://github.com/yisainan/web-interview/issues/505)

</details>

<b><details><summary>11.React 中 refs 的作用是什么？</summary></b>

答案：

Refs 是 React 提供给我们的安全访问 DOM 元素或者某个组件实例的句柄。我们可以为元素添加 ref 属性然后在回调函数中接受该元素在 DOM 树中的句柄，该值会作为回调函数的第一个参数返回：

```js
class CustomForm extends Component {
  handleSubmit = () => {
    console.log("Input Value: ", this.input.value);
  };
  render() {
    return (
      <form onSubmit={this.handleSubmit}>
        <input type="text" ref={input => (this.input = input)} />
        <button type="submit">Submit</button>
      </form>
    );
  }
}
```

上述代码中的 input 域包含了一个 ref 属性，该属性声明的回调函数会接收 input 对应的 DOM 元素，我们将其绑定到 this 指针以便在其他的类函数中使用。另外值得一提的是，refs 并不是类组件的专属，函数式组件同样能够利用闭包暂存其值：

```js
function CustomForm({ handleSubmit }) {
  let inputElement;
  return (
    <form onSubmit={() => handleSubmit(inputElement.value)}>
      <input type="text" ref={input => (inputElement = input)} />
      <button type="submit">Submit</button>
    </form>
  );
}
```

[参与互动](https://github.com/yisainan/web-interview/issues/506)

</details>

<b><details><summary>12.setState 和 replaceState 的区别</summary></b>

答案：

setState 是修改其中的部分状态，相当于 Object.assign，只是覆盖，不会减少原来的状态

replaceState 是完全替换原来的状态，相当于赋值，将原来的 state 替换为另一个对象，如果新状态属性减少，那么 state 中就没有这个状态了

[参与互动](https://github.com/yisainan/web-interview/issues/507)

</details>

<b><details><summary>13.redux 有什么缺点</summary></b>

答案：

- 一个组件所需要的数据，必须由父组件传过来，而不能像 flux 中直接从 store 取。
- 当一个组件相关数据更新时，即使父组件不需要用到这个组件，父组件还是会重新 render，可能会有效率影响，或者需要写复杂的 shouldComponentUpdate 进行判断。

[参与互动](https://github.com/yisainan/web-interview/issues/508)

</details>

<b><details><summary>14.简述 flux 思想</summary></b>

答案：Flux 的最大特点，就是数据的"单向流动"。

1. 用户访问 View
2. View 发出用户的 Action
3. Dispatcher 收到 Action，要求 Store 进行相应的更新
4. Store 更新后，发出一个"change"事件
5. View 收到"change"事件后，更新页面

[参与互动](https://github.com/yisainan/web-interview/issues/509)

</details>

<b><details><summary>15.了解 redux 么，说一下 redux 吧</summary></b>

答案：

- redux 是一个应用数据流框架，主要是解决了组件间状态共享的问题，原理是集中式管理，主要有三个核心方法，action，store，reducer，工作流程是 view 调用 store 的 dispatch 接收 action 传入 store，reducer 进行 state 操作，view 通过 store 提供的 getState 获取最新的数据，flux 也是用来进行数据操作的，有四个组成部分 action，dispatch，view，store，工作流程是 view 发出一个 action，派发器接收 action，让 store 进行数据更新，更新完成以后 store 发出 change，view 接受 change 更新视图。Redux 和 Flux 很像。主要区别在于 Flux 有多个可以改变应用状态的 store，在 Flux 中 dispatcher 被用来传递数据到注册的回调事件，但是在 redux 中只能定义一个可更新状态的 store，redux 把 store 和 Dispatcher 合并,结构更加简单清晰
- 新增 state,对状态的管理更加明确，通过 redux，流程更加规范了，减少手动编码量，提高了编码效率，同时缺点时当数据更新时有时候组件不需要，但是也要重新绘制，有些影响效率。一般情况下，我们在构建多交互，多数据流的复杂项目应用时才会使用它们

[参与互动](https://github.com/yisainan/web-interview/issues/510)

</details>

<b><details><summary>16.React 中有三种构建组件的方式</summary></b>

答案：React.createClass()、ES6 class 和无状态函数。

[参与互动](https://github.com/yisainan/web-interview/issues/511)

</details>

<b><details><summary>17.react 组件的划分业务组件技术组件？</summary></b>

答案：

- 根据组件的职责通常把组件分为 UI 组件和容器组件。
- UI 组件负责 UI 的呈现，容器组件负责管理数据和逻辑。
- 两者通过 React-Redux 提供 connect 方法联系起来。

[参与互动](https://github.com/yisainan/web-interview/issues/512)

</details>

<b><details><summary>18.描述事件在 React 中的处理方式</summary></b>

答案：

为了解决跨浏览器兼容性问题，您的 React 中的事件处理程序将传递 SyntheticEvent 的实例，它是 React 的浏览器本机事件的跨浏览器包装器。

这些 SyntheticEvent 与您习惯的原生事件具有相同的接口，除了它们在所有浏览器中都兼容。有趣的是，React 实际上并没有将事件附加到子节点本身。React 将使用单个事件监听器监听顶层的所有事件。这对于性能是有好处的，这也意味着在更新 DOM 时，React 不需要担心跟踪事件监听器。

[参与互动](https://github.com/yisainan/web-interview/issues/513)

</details>

<b><details><summary>19.应该在 React 组件的何处发起 Ajax 请求</summary></b>

答案：

在 React 组件中，应该在 componentDidMount 中发起网络请求。这个方法会在组件第一次“挂载”(被添加到 DOM)时执行，在组件的生命周期中仅会执行一次。更重要的是，你不能保证在组件挂载之前 Ajax 请求已经完成，如果是这样，也就意味着你将尝试在一个未挂载的组件上调用 setState，这将不起作用。在 componentDidMount 中发起网络请求将保证这有一个组件可以更新了。

[参与互动](https://github.com/yisainan/web-interview/issues/514)

</details>

<b><details><summary>20.(在构造函数中)调用 super(props) 的目的是什么</summary></b>

答案：

在 super() 被调用之前，子类是不能使用 this 的，在 ES2015 中，子类必须在 constructor 中调用 super()。传递 props 给 super() 的原因则是便于(在子类中)能在 constructor 访问 this.props。

[参与互动](https://github.com/yisainan/web-interview/issues/515)

</details>

<b><details><summary>21.除了在构造函数中绑定 this，还有其它方式吗</summary></b>

答案：

你可以使用属性初始值设定项(property initializers)来正确绑定回调，create-react-app 也是默认支持的。在回调中你可以使用箭头函数，但问题是每次组件渲染时都会创建一个新的回调。

[参与互动](https://github.com/yisainan/web-interview/issues/516)

</details>

<b><details><summary>22.为什么建议传递给 setState 的参数是一个 callback 而不是一个对象</summary></b>

答案：

因为 this.props 和 this.state 的更新可能是异步的，不能依赖它们的值去计算下一个 state。

[参与互动](https://github.com/yisainan/web-interview/issues/517)

</details>

<b><details><summary>23.何为高阶组件(higher order component)</summary></b>

答案：

高阶组件是一个以组件为参数并返回一个新组件的函数。HOC 运行你重用代码、逻辑和引导抽象。最常见的可能是 Redux 的 connect 函数。除了简单分享工具库和简单的组合，HOC 最好的方式是共享 React 组件之间的行为。如果你发现你在不同的地方写了大量代码来做同一件事时，就应该考虑将代码重构为可重用的 HOC。

[参与互动](https://github.com/yisainan/web-interview/issues/518)

</details>

<b><details><summary>24.何为受控组件(controlled component)</summary></b>

答案：

在 HTML 中，类似 `<input>`, `<textarea>` 和 `<select>` 这样的表单元素会维护自身的状态，并基于用户的输入来更新。当用户提交表单时，前面提到的元素的值将随表单一起被发送。但在 React 中会有些不同，包含表单元素的组件将会在 state 中追踪输入的值，并且每次调用回调函数时，如 onChange 会更新 state，重新渲染组件。一个输入表单元素，它的值通过 React 的这种方式来控制，这样的元素就被称为"受控元素"。

[参与互动](https://github.com/yisainan/web-interview/issues/519)

</details>

<b><details><summary>25.在 React 当中 Element 和 Component 有何区别？</summary></b>

答案：

React Element 是描述屏幕上所见内容的数据结构，是对于 UI 的对象表述。典型的 React Element 就是利用 JSX 构建的声明式代码片然后被转化为 createElement 的调用组合。

React Component 是一个函数或一个类，可以接收参数输入，并且返回某个 React Element

[参与互动](https://github.com/yisainan/web-interview/issues/520)

</details>

<b><details><summary>26.(组件的)状态(state)和属性(props)之间有何区别</summary></b>

答案：

- State 是一种数据结构，用于组件挂载时所需数据的默认值。State 可能会随着时间的推移而发生突变，但多数时候是作为用户事件行为的结果。
- Props(properties 的简写)则是组件的配置。props 由父组件传递给子组件，并且就子组件而言，props 是不可变的(immutable)。组件不能改变自身的 props，但是可以把其子组件的 props 放在一起(统一管理)。Props 也不仅仅是数据--回调函数也可以通过 props 传递。

[参与互动](https://github.com/yisainan/web-interview/issues/521)

</details>

<b><details><summary>27.展示组件(Presentational component)和容器组件(Container component)之间有何区别？</summary></b>

答案：

- 展示组件关心组件看起来是什么。展示专门通过 props 接受数据和回调，并且几乎不会有自身的状态，但当展示组件拥有自身的状态时，通常也只关心 UI 状态而不是数据的状态。
- 容器组件则更关心组件是如何运作的。容器组件会为展示组件或者其它容器组件提供数据和行为(behavior)，它们会调用 Flux actions，并将其作为回调提供给展示组件。容器组件经常是有状态的，因为它们是(其它组件的)数据源。

[参与互动](https://github.com/yisainan/web-interview/issues/522)

</details>

<b><details><summary>28.类组件(Class component)和 函数式组件(Functional component)之间有何区别？</summary></b>

答案：

1. 函数式组件比类组件操作简单，只是简单的调取和返回 JSX；而类组件可以使用生命周期函数来操作业务

2. 函数式组件可以理解为静态组件（组件中的内容调取的时候已经固定了，很难再修改），而类组件，可以基于组件内部的状态来动态更新渲染的内容

- 类组件不仅允许你使用更多额外的功能，如组件自身的状态和生命周期钩子，也能使组件直接访问 store 并维持状态
- 当组件仅是接收 props，并将组件自身渲染到页面时，该组件就是一个 '无状态组件(stateless component)'，可以使用一个纯函数来创建这样的组件。这种组件也被称为哑组件(dumb components)或展示组件

[参与互动](https://github.com/yisainan/web-interview/issues/523)

</details>

<b><details><summary>29.createElement 和 cloneElement 有什么区别？</summary></b>

答案：传入的第一个参数不同

React.createElement():JSX 语法就是用 React.createElement()来构建 React 元素的。它接受三个参数，第一个参数可以是一个标签名。如 div、span，或者 React 组件。第二个参数为传入的属性。第三个以及之后的参数，皆作为组件的子组件。

```js
React.createElement(type, [props], [...children]);
```

React.cloneElement()与 React.createElement()相似，不同的是它传入的第一个参数是一个 React 元素，而不是标签名或组件。新添加的属性会并入原有的属性，传入到返回的新元素中，而旧的子元素将被替换。将保留原始元素的键和引用。

```js
React.cloneElement(element, [props], [...children]);
```

[参与互动](https://github.com/yisainan/web-interview/issues/524)

</details>

<b><details><summary>30.React实现一个防抖的模糊查询输入框</summary></b>

答案：[參考](https://blog.csdn.net/cc18868876837/article/details/96303296)

</details>

<b><details><summary>31.React 和 Vue 的 diff 时间复杂度从 O(n^3) 优化到 O(n) ，那么 O(n^3) 和 O(n) 是如何计算出来的？</summary></b>

答案：

</details>

<b><details><summary>32.React 中 setState 什么时候是同步的，什么时候是异步的？</summary></b>

答案：

</details>

<b><details><summary>33.react-router里的`<Link>`标签和`<a>`标签有什么区别（滴滴）</summary></b>

答案：

</details>

<b><details><summary>34.react-router怎么实现路由切换（滴滴）</summary></b>

答案：

</details>

<b><details><summary>35.React组件事件代理的原理（网易）</summary></b>

答案：

</details>

<b><details><summary>36.RN的原理，为什么可以同时在安卓和IOS端运行（寺库）</summary></b>

答案：

</details>

<b><details><summary>37.比较一下React与Vue</summary></b>

答案：
```
相同点
1)	都有组件化开发和Virtual DOM
2)	都支持props进行父子组件间数据通信
3)	都支持数据驱动视图, 不直接操作真实DOM, 更新状态数据界面就自动更新
4)	都支持服务器端渲染
5)	都有支持native的方案,React的React Native,Vue的Weex

不同点
1)	数据绑定: vue实现了数据的双向绑定,react数据流动是单向的
2)	组件写法不一样, React推荐的做法是 JSX , 也就是把HTML和CSS全都写进JavaScript了,即'all in js'; Vue推荐的做法是webpack+vue-loader的单文件组件格式,即html,css,js写在同一个文件
3)	state对象在react应用中不可变的,需要使用setState方法更新状态;在vue中,state对象不是必须的,数据由data属性在vue对象中管理
4)	virtual DOM不一样,vue会跟踪每一个组件的依赖关系,不需要重新渲染整个组件树.而对于React而言,每当应用的状态被改变时,全部组件都会重新渲染,所以react中会需要shouldComponentUpdate这个生命周期函数方法来进行控制
5)	React严格上只针对MVC的view层,Vue则是MVVM模式
```

</details>

<b><details><summary>38.受控组件与非受控组件</summary></b>

答案：

* 受控: 表单元素状态由使用者维护
* 非受控: 表单元素状态DOM 自身维护

1. 受控组件

在HTML中，标签<input>、<textarea>、<select>的值的改变通常是根据用户输入进行更新。在React中，可变状态通常保存在组件的状态属性中，并且只能使用 setState() 更新，而呈现表单的React组件也控制着在后续用户输入时该表单中发生的情况，以这种由React控制的输入表单元素而改变其值的方式，称为：“受控组件”。

2. 不受控组件

表单数据由DOM本身处理。即不受setState()的控制，与传统的HTML表单输入相似，input输入值即显示最新值（使用 ref 从DOM获取表单值）

</details>

<b><details><summary></summary></b>

答案：

</details>

<b><details><summary></summary></b>

答案：

</details>

<b><details><summary></summary></b>

答案：

</details>

<b><details><summary></summary></b>

答案：

</details>
