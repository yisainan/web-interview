# [返回主页](../README.md)

<b><details><summary>1.当你调用 setState 的时候，发生了什么事？</summary></b>

将传递给 setState 的对象合并到组件的当前状态，这将启动一个和解的过程，构建一个新的 react 元素树，与上一个元素树进行对比（ diff ），从而进行最小化的重渲染。

</details>

<b><details><summary>2.在 React 当中 Element 和 Component 有何区别？</summary></b>

React Element 是描述屏幕上所见内容的数据结构，是对于 UI 的对象表述。典型的 React Element 就是利用 JSX 构建的声明式代码片然后被转化为 createElement 的调用组合。

React Component 是一个函数或一个类，可以接收参数输入，并且返回某个 React Element

</details>
    
<b><details><summary>3.什么时候在功能组件( Class Component )上使用类组件( Functional Component )？</summary></b>

如果您的组件具有状态( state )或生命周期方法，请使用 Class 组件。否则，使用功能组件

</details>

<b><details><summary></summary></b>

</details>
