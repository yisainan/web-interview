# [返回主页](https://github.com/yisainan/web-interview/blob/master/README.md)

<b><details><summary>1. vue 中的性能优化</summary></b>

答案：

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

减少 http 请求，合理设置 HTTP 缓存
使用浏览器缓存
启用压缩
CSS Sprites
LazyLoad Images
CSS 放在页面最上部，javascript 放在页面最下面
尽量避免使用 eval 和 Function

</details>

<b><details><summary>2. Vue 的实例生命周期</summary></b>

答案：

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

答案：

VUE 实现双向数据绑定的原理就是利用了 Object.defineProperty() 这个方法重新定义了对象获取属性值(get)和设置属性值(set)的操作来实现的。

Vue3.0 将用原生 Proxy 替换 Object.defineProperty

</details>

<b><details><summary>3. 为什么要替换 Object.defineProperty？</summary></b>

答案：

在 Vue 中，Object.defineProperty 无法监控到数组下标的变化，导致直接通过数组的下标给数组设置值，不能实时响应。

Object.defineProperty 只能劫持对象的属性,因此我们需要对每个对象的每个属性进行遍历。

</details>

<b><details><summary>3. 什么是 Proxy？</summary></b>

答案：

Proxy 是 ES6 中新增的一个特性，翻译过来意思是"代理"，用在这里表示由它来“代理”某些操作。 Proxy 让我们能够以简洁易懂的方式控制外部对对象的访问。其功能非常类似于设计模式中的代理模式。

Proxy 可以理解成，在目标对象之前架设一层“拦截”，外界对该对象的访问，都必须先通过这层拦截，因此提供了一种机制，可以对外界的访问进行过滤和改写。

使用 Proxy 的核心优点是可以交由它来处理一些非核心逻辑（如：读取或设置对象的某些属性前记录日志；设置对象的某些属性值前，需要验证；某些属性的访问控制等）。 从而可以让对象只需关注于核心逻辑，达到关注点分离，降低对象复杂度等目的。

</details>

<b><details><summary>9. 对于 Vue 是一套渐进式框架的理解</summary></b>

答案：

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

答案：数据驱动和组件化思想

</details>

<b><details><summary>11. 请问 v-if 和 v-show 有什么区别</summary></b>

答案：

v-show 指令是通过修改元素的 display 的 CSS 属性让其显示或者隐藏

v-if 指令是直接销毁和重建 DOM 达到让元素显示和隐藏的效果

</details>

<b><details><summary>12. vue 常用的修饰符</summary></b>

答案：

解析：

[参考](https://blog.csdn.net/qq_42238554/article/details/86592295)

</details>

<b><details><summary>13. v-on 可以监听多个方法吗？</summary></b>

答案：肯定可以的。

解析：

```html
<input
  type="text"
  :value="name"
  @input="onInput"
  @focus="onFocus"
  @blur="onBlur"
/>
```

</details>

<b><details><summary>14. vue 中 key 值的作用</summary></b>

答案：

需要使用 key 来给每个节点做一个唯一标识，Diff 算法就可以正确的识别此节点，找到正确的位置区插入新的节点
所以一句话，key 的作用主要是为了高效的更新虚拟 DOM

</details>

<b><details><summary>15. vue-cli 工程升级 vue 版本</summary></b>

答案：

在项目目录里运行 npm upgrade vue vue-template-compiler，不出意外的话，可以正常运行和 build。如果有任何问题，删除 node_modules 文件夹然后重新运行 npm i 即可。（简单的说就是升级 vue 和 vue-template-compiler 两个插件）

</details>

<b><details><summary>16. vue 事件中如何使用 event 对象？</summary></b>

答案：

v-on 指令（可以简写为 @）

1、使用不带圆括号的形式，event 对象将被自动当做实参传入；

2、使用带圆括号的形式，我们需要使用 \$event 变量显式传入 event 对象。

解析：

一、event 对象

（一）事件的 event 对象

你说你是搞前端的，那么你肯定就知道事件，知道事件，你就肯定知道 event 对象吧？各种的库、框架多少都有针对 event 对象的处理。比如 jquery，通过它内部进行一定的封装，我们开发的时候，就无需关注 event 对象的部分兼容性问题。最典型的，如果我们要阻止默认事件，在 chrome 等浏览器中，我们可能要写一个：

```js
event.preventDefault();
```

而在 IE 中，我们则需要写：

```js
event.returnValue = false;
```

多亏了 jquery ，跨浏览器的实现，我们统一只需要写：

```js
event.preventDefault();
```

兼容？jquery 内部帮我们搞定了。类似的还有比如阻止事件冒泡以以及事件绑定（addEventListener / attachEvent）等，简单到很多的后端都会使用 \$('xxx').bind(...)，这不是我们今天的重点，我们往下看。

（二）vue 中的 event 对象

我们知道，相比于 jquery，vue 的事件绑定可以显得更加直观和便捷，我们只需要在模板上添加一个 v-on 指令（还可以简写为 @），即可完成类似于 \$('xxx').bind 的效果，少了一个利用选择器查询元素的操作。我们知道，jquery 中，event 对象会被默认当做实参传入到处理函数中，如下

```js
$("body").bind("click", function(event) {
  console.log(typeof event); // object
});
```

这里直接就获取到了 event 对象，那么问题来了，vue 中呢？

```js
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

```js
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

（三）\$event

翻看 vue 文档，不难发现，其实我们可以通过将一个特殊变量 \$event 传入到回调中解决这个问题：

```js
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

使用带圆括号的形式，我们需要使用 \$event 变量显式传入 event 对象。

二、乌龙
前面都算是铺垫吧，现在真正的乌龙来了。
翻看小伙伴儿的代码，偶然看到了类似下面的代码：

```js
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

<b><details><summary>17.\$nextTick 的使用</summary></b>

答案：

1、什么是 Vue.nextTick()？

定义：在下次 DOM 更新循环结束之后执行延迟回调。在修改数据之后立即使用这个方法，获取更新后的 DOM。

所以就衍生出了这个获取更新后的 DOM 的 Vue 方法。所以放在 Vue.nextTick()回调函数中的执行的应该是会对 DOM 进行操作的 js 代码；

理解：nextTick()，是将回调函数延迟在下一次 dom 更新数据后调用，简单的理解是：当数据更新了，在 dom 中渲染后，自动执行该函数，

```js

<template>
  <div class="hello">
    <div>
      <button id="firstBtn" @click="testClick()" ref="aa">{{testMsg}}</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      testMsg:"原始值",
    }
  },
  methods:{
    testClick:function(){
      let that=this;
      that.testMsg="修改后的值";
      console.log(that.$refs.aa.innerText);   //that.$refs.aa获取指定DOM，输出：原始值
    }
  }
}
</script>
```

使用 this.\$nextTick()

```js
methods:{
    testClick:function(){
      let that=this;
      that.testMsg="修改后的值";
      that.$nextTick(function(){
        console.log(that.$refs.aa.innerText);  //输出：修改后的值
      });
    }
  }
```

注意：Vue 实现响应式并不是数据发生变化之后 DOM 立即变化，而是按一定的策略进行 DOM 的更新。$nextTick 是在下次 DOM 更新循环结束之后执行延迟回调，在修改数据之后使用 $nextTick，则可以在回调中获取更新后的 DOM，

2、什么时候需要用的 Vue.nextTick()？？

1、Vue 生命周期的 created()钩子函数进行的 DOM 操作一定要放在 Vue.nextTick()的回调函数中，原因是在 created()钩子函数执行的时候 DOM 其实并未进行任何渲染，而此时进行 DOM 操作无异于徒劳，所以此处一定要将 DOM 操作的 js 代码放进 Vue.nextTick()的回调函数中。与之对应的就是 mounted 钩子函数，因为该钩子函数执行时所有的 DOM 挂载已完成。

```js
created(){
    let that=this;
    that.$nextTick(function(){  //不使用this.$nextTick()方法会报错
        that.$refs.aa.innerHTML="created中更改了按钮内容";  //写入到DOM元素
    });
}
```

2、当项目中你想在改变 DOM 元素的数据后基于新的 dom 做点什么，对新 DOM 一系列的 js 操作都需要放进 Vue.nextTick()的回调函数中；通俗的理解是：更改数据后当你想立即使用 js 操作新的视图的时候需要使用它

```js

<template>
  <div class="hello">
    <h3 id="h">{{testMsg}}</h3>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      testMsg:"原始值",
    }
  },
  methods:{
    changeTxt:function(){
      let that=this;
      that.testMsg="修改后的文本值";  //vue数据改变，改变dom结构
      let domTxt=document.getElementById('h').innerText;  //后续js对dom的操作
      console.log(domTxt);  //输出可以看到vue数据修改后DOM并没有立即更新，后续的dom都不是最新的
      if(domTxt==="原始值"){
        console.log("文本data被修改后dom内容没立即更新");
      }else {
        console.log("文本data被修改后dom内容被马上更新了");
      }
    },

  }
}
</script>
```

正确的用法是：vue 改变 dom 元素结构后使用 vue.\$nextTick()方法来实现 dom 数据更新后延迟执行后续代码

```js
    changeTxt:function(){
      let that=this;
      that.testMsg="修改后的文本值";  //修改dom结构

      that.$nextTick(function(){  //使用vue.$nextTick()方法可以dom数据更新后延迟执行
        let domTxt=document.getElementById('h').innerText;
        console.log(domTxt);  //输出可以看到vue数据修改后并没有DOM没有立即更新，
        if(domTxt==="原始值"){
          console.log("文本data被修改后dom内容没立即更新");
        }else {
          console.log("文本data被修改后dom内容被马上更新了");
        }
      });
    }
```

3、在使用某个第三方插件时 ，希望在 vue 生成的某些 dom 动态发生变化时重新应用该插件，也会用到该方法，这时候就需要在 \$nextTick 的回调函数中执行重新应用插件的方法。

Vue.nextTick(callback) 使用原理：

原因是，Vue 是异步执行 dom 更新的，一旦观察到数据变化，Vue 就会开启一个队列，然后把在同一个事件循环 (event loop) 当中观察到数据变化的 watcher 推送进这个队列。如果这个 watcher 被触发多次，只会被推送到队列一次。这种缓冲行为可以有效的去掉重复数据造成的不必要的计算和 DOm 操作。而在下一个事件循环时，Vue 会清空队列，并进行必要的 DOM 更新。
当你设置 vm.someData = 'new value'，DOM 并不会马上更新，而是在异步队列被清除，也就是下一个事件循环开始时执行更新时才会进行必要的 DOM 更新。如果此时你想要根据更新的 DOM 状态去做某些事情，就会出现问题。。为了在数据变化之后等待 Vue 完成更新 DOM ，可以在数据变化之后立即使用 Vue.nextTick(callback) 。这样回调函数在 DOM 更新完成后就会调用。

</details>

<b><details><summary>18. Vue 组件中 data 为什么必须是函数</summary></b>

答案：

在 new Vue() 中，data 是可以作为一个对象进行操作的，然而在 component 中，data 只能以函数的形式存在，不能直接将对象赋值给它，这并非是 Vue 自身如此设计，而是跟 JavaScript 特性相关，我们来回顾下 JavaScript 的原型链

```js
var Component = function() {};
Component.prototype.data = {
  message: "Love"
};
var component1 = new Component(),
  component2 = new Component();
component1.data.message = "Peace";
console.log(component2.data.message); // Peace
```

以上两个实例都引用同一个对象，当其中一个实例属性改变时，另一个实例属性也随之改变，只有当两个实例拥有自己的作用域时，才不会互相干扰 ！！！！！这句是重点！！！！！

```js
var Component = function() {
  this.data = this.data();
};
Component.prototype.data = function() {
  return {
    message: "Love"
  };
};
var component1 = new Component(),
  component2 = new Component();
component1.data.message = "Peace";
console.log(component2.data.message); // Love
```

</details>

<b><details><summary>19. v-for 与 v-if 的优先级</summary></b>

答案：v-for 比 v-if 优先

</details>

<b><details><summary>20. vue 中子组件调用父组件的方法</summary></b>

答案：

- 第一种方法是直接在子组件中通过 this.\$parent.event 来调用父组件的方法
- 第二种方法是在子组件里用\$emit 向父组件触发一个事件，父组件监听这个事件就行了
- 第三种是父组件把方法传入子组件中，在子组件里直接调用这个方法

解析：

第一种方法是直接在子组件中通过 this.\$parent.event 来调用父组件的方法

父组件

```js
<template>
  <div>
    <child></child>
  </div>
</template>
<script>
  import child from '~/components/dam/child';
  export default {
    components: {
      child
    },
    methods: {
      fatherMethod() {
        console.log('测试');
      }
    }
  };
</script>
```

子组件

```html
<template>
  <div>
    <button @click="childMethod()">点击</button>
  </div>
</template>
<script>
  export default {
    methods: {
      childMethod() {
        this.$parent.fatherMethod();
      }
    }
  };
</script>
```

第二种方法是在子组件里用\$emit 向父组件触发一个事件，父组件监听这个事件就行了

父组件

```html
<template>
  <div>
    <child @fatherMethod="fatherMethod"></child>
  </div>
</template>
<script>
  import child from "~/components/dam/child";
  export default {
    components: {
      child
    },
    methods: {
      fatherMethod() {
        console.log("测试");
      }
    }
  };
</script>
```

子组件

```html
<template>
  <div>
    <button @click="childMethod()">点击</button>
  </div>
</template>
<script>
  export default {
    methods: {
      childMethod() {
        this.$emit("fatherMethod");
      }
    }
  };
</script>
```

第三种是父组件把方法传入子组件中，在子组件里直接调用这个方法

父组件

```html
<template>
  <div>
    <child :fatherMethod="fatherMethod"></child>
  </div>
</template>
<script>
  import child from "~/components/dam/child";
  export default {
    components: {
      child
    },
    methods: {
      fatherMethod() {
        console.log("测试");
      }
    }
  };
</script>
```

子组件

```html
<template>
  <div>
    <button @click="childMethod()">点击</button>
  </div>
</template>
<script>
  export default {
    props: {
      fatherMethod: {
        type: Function,
        default: null
      }
    },
    methods: {
      childMethod() {
        if (this.fatherMethod) {
          this.fatherMethod();
        }
      }
    }
  };
</script>
```

</details>

<b><details><summary>21. vue 中父组件调用子组件的方法</summary></b>

答案：使用\$refs

解析：

父组件

```html
<template>
  <div>
    <button @click="clickParent">点击</button>
    <child ref="mychild"></child>
  </div>
</template>

<script>
  import Child from "./child";
  export default {
    name: "parent",
    components: {
      child: Child
    },
    methods: {
      clickParent() {
        this.$refs.mychild.parentHandleclick("嘿嘿嘿"); // 划重点！！！！
      }
    }
  };
</script>
```

子组件

```html
<template>
  <div>
    child
  </div>
</template>

<script>
  export default {
    name: "child",
    props: "someprops",
    methods: {
      parentHandleclick(e) {
        console.log(e);
      }
    }
  };
</script>
```

</details>

<b><details><summary>22. vue 中 keep-alive 组件的作用</summary></b>

答案：keep-alive 是 Vue 内置的一个组件，可以使被包含的组件保留状态，或避免重新渲染。

解析：

用法也很简单：

```html
<keep-alive>
  <component>
    <!-- 该组件将被缓存！ -->
  </component>
</keep-alive>
```

props
_ include - 字符串或正则表达，只有匹配的组件会被缓存
_ exclude - 字符串或正则表达式，任何匹配的组件都不会被缓存

```js
// 组件 a
export default {
  name: "a",
  data() {
    return {};
  }
};
```

```html
<keep-alive include="a">
  <component>
    <!-- name 为 a 的组件将被缓存！ -->
  </component> </keep-alive
>可以保留它的状态或避免重新渲染
```

```html
<keep-alive exclude="a">
  <component>
    <!-- 除了 name 为 a 的组件都将被缓存！ -->
  </component> </keep-alive
>可以保留它的状态或避免重新渲染
```

但实际项目中,需要配合 vue-router 共同使用.

router-view 也是一个组件，如果直接被包在 keep-alive 里面，所有路径匹配到的视图组件都会被缓存：

```html
<keep-alive>
  <router-view>
    <!-- 所有路径匹配到的视图组件都会被缓存！ -->
  </router-view>
</keep-alive>
```

如果只想 router-view 里面某个组件被缓存，怎么办？

增加 router.meta 属性

```js
// routes 配置
export default [
  {
    path: "/",
    name: "home",
    component: Home,
    meta: {
      keepAlive: true // 需要被缓存
    }
  },
  {
    path: "/:id",
    name: "edit",
    component: Edit,
    meta: {
      keepAlive: false // 不需要被缓存
    }
  }
];
```

```
<keep-alive>
    <router-view v-if="$route.meta.keepAlive">
        <!-- 这里是会被缓存的视图组件，比如 Home！ -->
    </router-view>
</keep-alive>

<router-view v-if="!$route.meta.keepAlive">
    <!-- 这里是不被缓存的视图组件，比如 Edit！ -->
</router-view>
```

</details>

<b><details><summary>23. vue 中如何编写可复用的组件？</summary></b>

答案：总结组件的职能，什么需要外部控制（即 props 传啥），组件需要控制外部吗（\$emit）,是否需要插槽（slot）

</details>

<b><details><summary>24. 什么是 vue 生命周期和生命周期钩子函数？</summary></b>

答案：

vue 的生命周期就是 vue 实例从创建到销毁的过程

解析：

![vue_004](../images/vue_004.jpg)
![vue_005](../images/vue_005.jpg)

</details>

<b><details><summary>25. vue 生命周期钩子函数有哪些？</summary></b>

答案：

![vue_005](../images/vue_005.jpg)

</details>

<b><details><summary>26. vue 如何监听键盘事件中的按键？</summary></b>

答案：

解析：
[参考](https://blog.csdn.net/xiaxiangyun/article/details/80404768)

</details>

<b><details><summary>27. vue 更新数组时触发视图更新的方法</summary></b>

答案：

1.Vue.set 可以设置对象或数组的值，通过 key 或数组索引，可以触发视图更新

```
数组修改

Vue.set(array, indexOfItem, newValue)
this.array.$set(indexOfItem, newValue)
对象修改

Vue.set(obj, keyOfItem, newValue)
this.obj.$set(keyOfItem, newValue)
```

2.Vue.delete 删除对象或数组中元素，通过 key 或数组索引，可以触发视图更新

```
数组修改

Vue.delete(array, indexOfItem)
this.array.$delete(indexOfItem)
对象修改

Vue.delete(obj, keyOfItem)
this.obj.$delete(keyOfItem)
```

3.数组对象直接修改属性，可以触发视图更新

```
this.array[0].show = true;
this.array.forEach(function(item){
    item.show = true;
});
```

4.splice 方法修改数组，可以触发视图更新

```
this.array.splice(indexOfItem, 1, newElement)
```

5.数组整体修改，可以触发视图更新

```
var tempArray = this.array;
tempArray[0].show = true;
this.array = tempArray;
```

6.用 Object.assign 或 lodash.assign 可以为对象添加响应式属性，可以触发视图更新

```
//Object.assign的单层的覆盖前面的属性，不会递归的合并属性
this.obj = Object.assign({},this.obj,{a:1, b:2})

//assign与Object.assign一样
this.obj = _.assign({},this.obj,{a:1, b:2})

//merge会递归的合并属性
this.obj = _.merge({},this.obj,{a:1, b:2})
```

7.Vue 提供了如下的数组的变异方法，可以触发视图更新

```
push()
pop()
shift()
unshift()
splice()
sort()
reverse()
```

</details>

<b><details><summary>28. vue 中对象更改检测的注意事项</summary></b>

答案：

</details>

<b><details><summary>29. 解决非工程化项目初始化页面闪动问题</summary></b>

答案：

</details>

<b><details><summary>30. v-for 产生的列表，实现 active 的切换</summary></b>

答案：

</details>

<b><details><summary>31. v-model 语法糖的组件中的使用</summary></b>

答案：

</details>

<b><details><summary>32. 十个常用的自定义过滤器</summary></b>

答案：

</details>

<b><details><summary>33. vue 等单页面应用及其优缺点</summary></b>

答案：

</details>

<b><details><summary>34. 什么是 vue 的计算属性？</summary></b>

答案：

</details>

<b><details><summary>35. vue-cli 提供的几种脚手架模板</summary></b>

答案：

</details>

<b><details><summary>36. vue 父组件如何向子组件中传递数据？</summary></b>

答案：

</details>

<b><details><summary>37. vue-cli 开发环境使用全局常量</summary></b>

答案：

</details>

<b><details><summary>38. vue-cli 生产环境使用全局常量</summary></b>

答案：

</details>

<b><details><summary>39. vue 弹窗后如何禁止滚动条滚动？</summary></b>

答案：

</details>

<b><details><summary>40. 计算属性的缓存和方法调用的区别</summary></b>

答案：

</details>

<b><details><summary>41. vue-cli 中自定义指令的使用</summary></b>

答案：

</details>

<b><details><summary>42. vue 如何优化首屏加载速度？</summary></b>

答案：

</details>

<b><details><summary>43. vue 打包命令是什么？</summary></b>

答案：

npm run build

</details>

<b><details><summary>44. vue 打包后会生成哪些文件？</summary></b>

答案：

</details>

<b><details><summary>45. 如何配置 vue 打包生成文件的路径？</summary></b>

答案：

</details>

<b><details><summary>46. vue 的服务器端渲染</summary></b>

答案：

</details>

<b><details><summary>47. vue 开发命令 npm run dev 输入后的执行过程</summary></b>

答案：

</details>

<b><details><summary>48. 什么是 Virtual DOM？</summary></b>

答案：

可以看作是一个使用 javascript 模拟了 DOM 结构的树形结构

[详情])(https://www.cnblogs.com/gaosong-shuhong/p/9253959.html)

</details>

<b><details><summary>49. 响应式系统的基本原理</summary></b>

答案：

Object.defineProperty，Vue.js 就是基于它实现「响应式系统」的。

</details>

<b><details><summary>50. Vue.js 全局运行机制</summary></b>

答案：

</details>

<b><details><summary>51. 如何编译 template 模板？</summary></b>

答案：

[详情](http://www.itcast.cn/news/20190110/15320198690.shtml)

</details>

<b><details><summary>52. diff 算法</summary></b>

答案：

</details>

<b><details><summary>53. 批量异步更新策略及 nextTick 原理？</summary></b>

答案：

</details>

<b><details><summary>54. Vue 中如何实现 proxy 代理？</summary></b>

答案：

webpack 自带的 devServer 中集成了 http-proxy-middleware。配置 devServer 的 proxy 选项即可

```js
proxyTable: {
   '/api': {
    target: 'http://192.168.149.90:8080/', // 设置你调用的接口域名和端口号
    changeOrigin: true,   // 跨域
    pathRewrite: {
     '^/api': '/'
    }
   }
  }
```

</details>

<b><details><summary>55. vue 中如何实现 tab 切换功能？</summary></b>

答案：

</details>

<b><details><summary>56. vue 中如何利用 keep-alive 标签实现某个组件缓存功能？</summary></b>

答案：

</details>

<b><details><summary>57. vue 中实现切换页面时为左滑出效果</summary></b>

答案：

</details>

<b><details><summary>58. vue 中央事件总线的使用</summary></b>

答案：

</details>

<b><details><summary>59. vue 的渲染机制</summary></b>

答案：

</details>

<b><details><summary>60. vue 在什么情况下在数据发生改变的时候不会触发视图更新</summary></b>

答案：

v-for 遍历的数组，当数组内容使用的是 arr[0].xx =xx 更改数据，vue 无法监测到
vm.arr.length = newLength 也是无法检测的到的

</details>

<b><details><summary>vue 的优点是什么？</summary></b>

答案：

低耦合。视图（View）可以独立于 Model 变化和修改，一个 ViewModel 可以绑定到不同的"View"上，当 View 变化的时候 Model 可以不变，当 Model 变化的时候 View 也可以不变。

可重用性。你可以把一些视图逻辑放在一个 ViewModel 里面，让很多 view 重用这段视图逻辑。

独立开发。开发人员可以专注于业务逻辑和数据的开发（ViewModel），设计人员可以专注于页面设计。

可测试。界面素来是比较难于测试的，而现在测试可以针对 ViewModel 来写。

</details>

<b><details><summary>vue 如何实现按需加载配合 webpack 设置</summary></b>

答案：

```
webpack 中提供了 require.ensure()来实现按需加载。以前引入路由是通过 import 这样的方式引入，改为 const 定义的方式进行引入。
不进行页面按需加载引入方式：import home from '../../common/home.vue'
进行页面按需加载的引入方式：const home = r => require.ensure( [], () => r (require('../../common/home.vue')))
```

在音乐 app 中使用的路由懒加载方式为：

```
const Recommend = (resolve) => {
  import('components/recommend/recommend').then((module) => {
    resolve(module)
  })
}

const Singer = (resolve) => {
  import('components/singer/singer').then((module) => {
    resolve(module)
  })
}
```

</details>

<b><details><summary>如何让 CSS 只在当前组件中起作用</summary></b>

答案：将当前组件的<style>修改为<style scoped>

</details>

<b><details><summary>指令 v-el 的作用是什么?</summary></b>

答案：提供一个在页面上已存在的 DOM 元素作为 Vue 实例的挂载目标.可以是 CSS 选择器，也可以是一个 HTMLElement 实例

</details>

<b><details><summary>vue-router 有哪几种导航钩子？</summary></b>

答案：三种

第一种是全局导航钩子：router.beforeEach(to,from,next)，作用：跳转前进行判断拦截。
第二种：组件内的钩子；
第三种：单独路由独享组件

</details>

<b><details><summary>vue-loader 是什么？使用它的用途有哪些？</summary></b>

答案：

解析：

.vue 文件的一个加载器。（深入理解见https://www.jb51.net/article/115480.htm）
用途：js 可以写 es6、style 样式可以 scss 或 less、template 可以加 jade 等

</details>

<b><details><summary>为什么避免 v-if 和 v-for 用在一起</summary></b>

 答案：

当 Vue 处理指令时，v-for 比 v-if 具有更高的优先级，这意味着 v-if 将分别重复运行于每个 v-for 循环中。通过 v-if 移动到容器元素，不会再重复遍历列表中的每个值。取而代之的是，我们只检查它一次，且不会在 v-if 为否的时候运算 v-for。

</details>

<b><details><summary>组件的设计原则</summary></b>

 答案：

```
(1)页面上每个独立的可视/可交互区域视为一个组件(比如页面的头部，尾部，可复用的区块)
(2)每个组件对应一个工程目录，组件所需要的各种资源在这个目录下就近维护(组件的就近维护思想体现了前端的工程化思想，为前端开发提供了很好的分治策略，在vue.js中，通过.vue文件将组件依赖的模板，js，样式写在一个文件中)
(每个开发者清楚开发维护的功能单元，它的代码必然存在在对应的组件目录中，在该目录下，可以找到功能单元所有的内部逻辑)
(3)页面不过是组件的容器，组件可以嵌套自由组合成完整的页面
```

</details>
