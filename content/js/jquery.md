# [返回主页](https://github.com/yisainan/web-interview/blob/master/README.md)

<b><details><summary>1.说下 jQuery/Zepto 中的 on 方法有哪些参数，分别代表什么意思？</summary></b>

答案：

</details>

<b><details><summary>2.谈一下 Jquery 中的 bind(),live(),delegate(),on()的区别？</summary></b>

答案： 

* bind： 绑定事件，对新添加的事件不起作用，方法用于将一个处理程序附加到每个匹配元素的事件上并返回 jQuery 对象。
* live： 方法将一个事件处理程序附加到与当前选择器匹配的所有元素（包含现有的或将来添加的）的指定事件上并返回 jQuery 对象。
* delegate： 方法基于一组特定的根元素将处理程序附加到匹配选择器的所有元素（现有的或将来的）的一个或多个事件上。

</details>

<b><details><summary>3.jQuery 的队列是如何实现的？队列可以用在哪些地方？</summary></b>

答案：

</details>

<b><details><summary>4.jquery.extend 与 jquery.fn.extend 的区别？</summary></b>

答案：

</details>

<b><details><summary>5.jQuery 的属性拷贝(extend)的实现原理是什么，如何实现深拷贝？</summary></b>

答案：

</details>

<b><details><summary>6.jquery 中如何将数组转化为 json 字符串，然后再转化回来？</summary></b>

答案：

</details>

<b><details><summary>7.jQuery.fn 的 init 方法返回的 this 指的是什么对象？为什么要返回 this？</summary></b>

答案：

</details>

<b><details><summary>8.jQuery 与 jQuery UI、jQuery Mobile 区别？</summary></b>

答案：

</details>

<b><details><summary>9.jQuery 的 slideUp 动画 ，如果目标元素是被外部事件驱动, 当鼠标快速地连续触发外部元素事件, 动画会滞后的反复执行，该如何处理呢?</summary></b>

答案：

</details>

<b><details><summary>10.你觉得 jQuery 源码有哪些写的好的地方</summary></b>

答案：

</details>

<b><details><summary>11.你觉得 jQuery 或 zepto 源码有哪些写的好的地方</summary></b>

答案：

</details>

<b><details><summary>12.jQuery 的实现原理？</summary></b>

答案：

</details>

<b><details><summary>13.是否知道自定义事件？ jQuery 里的 fire 函数是什么意思，什么时候用？</summary></b>

答案：

</details>

<b><details><summary>14.jQuery 通过哪个方法和 Sizzle 选择器结合的？</summary></b>

答案：

</details>

<b><details><summary>15.jQuery 一个对象可以同时绑定多个事件，这是如何实现的？</summary></b>

答案：

</details>

<b><details><summary>16.针对 jQuery 的优化方法？</summary></b>

答案：

</details>

<b><details><summary>17.jQuery UI 如何自定义组件？</summary></b>

答案：

</details>

<b><details><summary>18.jQuery 和 Zepto 的区别？ 各自的使用场景？</summary></b>

答案：

</details>

<b><details><summary>19.jQuery 对象的特点</summary></b>

答案：

</details>

<b><details><summary>20.Zepto 的点透问题如何解决？</summary></b>

答案：点透主要是由于两个 div 重合，例如：一个 div 调用 show()，一个 div 调用 hide()；这个时候当点击上面的 div 的时候就会影响到下面的那个 div；
解决办法主要有 2 种：

1. github 上有一个叫做 fastclick 的库，它也能规避移动设备上 click 事件的延迟响应，https://github.com/ftlabs/fastclick
   将它用 script 标签引入页面（该库支持 AMD，于是你也可以按照 AMD 规范，用诸如 require.js 的模块加载器引入），并且在 dom ready 时初始化在 body 上，
2. 根据分析，如果不引入其它类库，也不想自己按照上述 fastclcik 的思路再开发一套东西，需要 1.一个优先于下面的“divClickUnder”捕获的事件；2.并且通过这个事件阻止掉默认行为（下面的“divClickUnder”对 click 事件的捕获，在 ios 的 safari，click 的捕获被认为和滚屏、点击输入框弹起键盘等一样，是一种浏览器默认行为，即可以被 event.preventDefault()阻止的行为）。

</details>

<b><details><summary></summary></b>

答案：

</details>

<b><details><summary></summary></b>

答案：

</details>
