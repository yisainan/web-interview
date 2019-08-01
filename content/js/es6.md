# [返回主页](https://github.com/yisainan/web-interview/blob/master/README.md)

<b><details><summary>1.ES6 都有什么 Iterator 遍历器</summary></b>

答案：Set、Map

解析：

1、遍历器（Iterator）是一种接口，为各种不同的数据结构提供统一的访问机制。任何数据结构只要部署 Iterator 接口，就可以完成遍历操作（即依次处理该数据结构的所有成员）

2、Iterator 的作用有三个：

- 一是为各种数据结构，提供一个统一的、简便的访问接口；
- 二是使得数据结构的成员能够按某种次序排列；
- 三是 ES6 创造了一种新的遍历命令 for...of 循环，Iterator 接口主要供 for...of 消费。

3、默认部署了 Iterator 的数据有 Array、Map、Set、String、TypedArray、arguments、NodeList 对象，ES6 中有的是 Set、Map、

</details>

<b><details><summary>2. ES6 中类的定义</summary></b>



```js
// 1、类的基本定义
class Parent {
  constructor(name = "小白") {
    this.name = name;
  }
}
```

```js
// 2、生成一个实例
let g_parent = new Parent();
console.log(g_parent); //{name: "小白"}
let v_parent = new Parent("v"); // 'v'就是构造函数name属性 , 覆盖构造函数的name属性值
console.log(v_parent); // {name: "v"}
```

```js
// 3、继承
class Parent {
  //定义一个类
  constructor(name = "小白") {
    this.name = name;
  }
}

class Child extends Parent {}

console.log("继承", new Child()); // 继承 {name: "小白"}
```

```js
// 4、继承传递参数
class Parent {
  //定义一个类
  constructor(name = "小白") {
    this.name = name;
  }
}

class Child extends Parent {
  constructor(name = "child") {
    // 子类重写name属性值
    super(name); // 子类向父类修改 super一定放第一行
    this.type = "preson";
  }
}
console.log("继承", new Child("hello")); // 带参数覆盖默认值  继承{name: "hello", type: "preson"}
```

```js
// 5、ES6重新定义的ES5中的访问器属性
class Parent {
  //定义一个类
  constructor(name = "小白") {
    this.name = name;
  }

  get longName() {
    // 属性
    return "mk" + this.name;
  }

  set longName(value) {
    this.name = value;
  }
}

let v = new Parent();
console.log("getter", v.longName); // getter mk小白

v.longName = "hello";
console.log("setter", v.longName); // setter mkhello
```

```js
// 6、类的静态方法
class Parent {
  //定义一个类
  constructor(name = "小白") {
    this.name = name;
  }

  static tell() {
    // 静态方法:通过类去调用，而不是实例
    console.log("tell");
  }
}

Parent.tell(); // tell
```

```js
// 7、类的静态属性：

class Parent {
  //定义一个类
  constructor(name = "小白") {
    this.name = name;
  }

  static tell() {
    // 静态方法:通过类去调用，而不是实例
    console.log("tell"); // tell
  }
}

Parent.type = "test"; // 定义静态属性

console.log("静态属性", Parent.type); // 静态属性 test

let v_parent = new Parent();
console.log(v_parent); // {name: "小白"}  没有tell方法和type属性
```

</details>

<b><details><summary>4.解构赋值及其原理</summary></b>
答案：

解析：
</details>

<b><details><summary>5.Array.from 与 Array.reduce</summary></b>
答案：

解析：
</details>

<b><details><summary>6.箭头函数需要注意的地方</summary></b>

答案：
```

箭头函数有几个使用注意点。
（1）函数体内的 this 对象，就是定义时所在的对象，而不是使用时所在的对象。
（2）不可以当作构造函数，也就是说，不可以使用 new 命令，否则会抛出一个错误。
（3）不可以使用 arguments 对象，该对象在函数体内不存在。如果要用，可以用 rest 参数代替。
（4）不可以使用 yield 命令，因此箭头函数不能用作 Generator 函数。

```

上面四点中，第一点尤其值得注意。this 对象的指向是可变的，但是在箭头函数中，它是固定的。

```js
function foo() {
  setTimeout(() => {
    console.log("id:", this.id);
  }, 100);
}

var id = 21;

foo.call({ id: 42 });
// id: 42
```
解析：
[参考地址](https://www.jianshu.com/p/bc28e4f67ef9)

</details>

<b><details><summary>7.var let 在 for 循环中的区别</summary></b>
答案：

解析：
[参考](https://blog.csdn.net/zoelinjf/article/details/79618688)

</details>

<b><details><summary>8.Set 数据结构</summary></b>

- es6 方法,Set 本身是一个构造函数，它类似于数组，但是成员值都是唯一的。

```js
const set = new Set([1, 2, 3, 4, 4]);
console.log([...set]); // [1,2,3,4]
console.log(Array.from(new Set([2, 3, 3, 5, 6]))); //[2,3,5,6]
```

</details>

<b><details><summary>9.Class 的讲解</summary></b>

- class 语法相对原型、构造函数、继承更接近传统语法，它的写法能够让对象原型的写法更加清晰、面向对象编程的语法更加通俗
  这是 class 的具体用法。

[参考](https://www.cnblogs.com/fengxiongZz/p/8191503.html)

</details>

<b><details><summary>10.模板字符串</summary></b>

- 就是这种形式${varible},在以往的时候我们在连接字符串和变量的时候需要使用这种方式'string' + varible + 'string'但是有了模版语言后我们可以使用string${varible}string 这种进行连接。基本用途有如下：

1、基本的字符串格式化，将表达式嵌入字符串中进行拼接，用\${}来界定。

```js
//es5
var name = "lux";
console.log("hello" + name);
//es6
const name = "lux";
console.log(`hello ${name}`); //hello lux
```

2、在 ES5 时我们通过反斜杠(\)来做多行字符串或者字符串一行行拼接，ES6 反引号(``)直接搞定。

```js
//ES5
var template =
  "hello \
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
