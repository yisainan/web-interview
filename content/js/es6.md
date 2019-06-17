# [返回主页](../../README.md)

<b><details><summary>27.ES6 都有什么 iterater 遍历器</summary></b>

</details>

<b><details><summary>6、 ES6 中类和定义</summary></b>

</details>

<b><details><summary>7、JS 中的文档碎片</summary></b>

</details>

<b><details><summary>8、解构赋值</summary></b>

</details>

<b><details><summary>9、Array.from 与 Array.reduce</summary></b>

</details>

<b><details><summary>箭头函数需要注意的地方</summary></b>

```
箭头函数有几个使用注意点。
（1）函数体内的this对象，就是定义时所在的对象，而不是使用时所在的对象。
（2）不可以当作构造函数，也就是说，不可以使用new命令，否则会抛出一个错误。
（3）不可以使用arguments对象，该对象在函数体内不存在。如果要用，可以用 rest 参数代替。
（4）不可以使用yield命令，因此箭头函数不能用作 Generator 函数。

```
上面四点中，第一点尤其值得注意。this对象的指向是可变的，但是在箭头函数中，它是固定的。

```js
function foo() {
  setTimeout(() => {
    console.log('id:', this.id);
  }, 100);
}

var id = 21;

foo.call({ id: 42 });
// id: 42
```
[参考地址](https://www.jianshu.com/p/bc28e4f67ef9)

</details>

<b><details><summary>var let 在for循环中的区别</summary></b>

[参考](https://blog.csdn.net/zoelinjf/article/details/79618688)

</details>

<b><details><summary>Set数据结构</summary></b>

* es6方法,Set本身是一个构造函数，它类似于数组，但是成员值都是唯一的。

```js
const set = new Set([1,2,3,4,4])
console.log([...set] )// [1,2,3,4]
console.log(Array.from(new Set([2,3,3,5,6]))); //[2,3,5,6]
```
</details>

<b><details><summary>Class的讲解</summary></b>

* class语法相对原型、构造函数、继承更接近传统语法，它的写法能够让对象原型的写法更加清晰、面向对象编程的语法更加通俗
这是class的具体用法。

[参考](https://www.cnblogs.com/fengxiongZz/p/8191503.html)

</details>

<b><details><summary>模板字符串</summary></b>

* 就是这种形式${varible},在以往的时候我们在连接字符串和变量的时候需要使用这种方式'string' + varible + 'string'但是有了模版语言后我们可以使用string${varible}string这种进行连接。基本用途有如下：

1、基本的字符串格式化，将表达式嵌入字符串中进行拼接，用${}来界定。

```js
//es5 
var name = 'lux';
console.log('hello' + name);
//es6
const name = 'lux';
console.log(`hello ${name}`); //hello lux
```
2、在ES5时我们通过反斜杠(\)来做多行字符串或者字符串一行行拼接，ES6反引号(``)直接搞定。
```js
//ES5
var template = "hello \
world";
console.log(template); //hello world

//ES6
const template = `hello
world`;
console.log(template); //hello 空行 world
```

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