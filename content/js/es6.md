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

答案：

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

答案：我的书签

解析：

</details>

<b><details><summary>5.Array.from() 与 Array.reduce()</summary></b>

答案：

Array.from()方法就是将一个类数组对象或者可遍历对象转换成一个真正的数组
Array.reduce()方法对累加器和数组中的每个元素 (从左到右)应用一个函数，将其减少为单个值。

解析：

### Array.from()

```js
// 那么什么是类数组对象呢？所谓类数组对象，最基本的要求就是具有length属性的对象。

// 1、将类数组对象转换为真正数组：

let arrayLike = {
  0: "tom",
  1: "65",
  2: "男",
  3: ["jane", "john", "Mary"],
  length: 4
};
let arr = Array.from(arrayLike);
console.log(arr); // ['tom','65','男',['jane','john','Mary']]

// 那么，如果将上面代码中length属性去掉呢？实践证明，答案会是一个长度为0的空数组。

// 这里将代码再改一下，就是具有length属性，但是对象的属性名不再是数字类型的，而是其他字符串型的，代码如下：

let arrayLike = {
  name: "tom",
  age: "65",
  sex: "男",
  friends: ["jane", "john", "Mary"],
  length: 4
};
let arr = Array.from(arrayLike);
console.log(arr); // [ undefined, undefined, undefined, undefined ]

// 会发现结果是长度为4，元素均为undefined的数组

// 由此可见，要将一个类数组对象转换为一个真正的数组，必须具备以下条件：

// 1、该类数组对象必须具有length属性，用于指定数组的长度。如果没有length属性，那么转换后的数组是一个空数组。

// 2、该类数组对象的属性名必须为数值型或字符串型的数字

// ps: 该类数组对象的属性名可以加引号，也可以不加引号

// 2、将Set结构的数据转换为真正的数组：

let arr = [12, 45, 97, 9797, 564, 134, 45642];
let set = new Set(arr);
console.log(Array.from(set)); // [ 12, 45, 97, 9797, 564, 134, 45642 ]

// 　Array.from还可以接受第二个参数，作用类似于数组的map方法，用来对每个元素进行处理，将处理后的值放入返回的数组。如下：

let arr = [12, 45, 97, 9797, 564, 134, 45642];
let set = new Set(arr);
console.log(Array.from(set, item => item + 1)); // [ 13, 46, 98, 9798, 565, 135, 45643 ]

// 3、将字符串转换为数组：

let str = "hello world!";
console.log(Array.from(str)); // ["h", "e", "l", "l", "o", " ", "w", "o", "r", "l", "d", "!"]

// 4、Array.from参数是一个真正的数组：

console.log(Array.from([12, 45, 47, 56, 213, 4654, 154]));
// 像这种情况，Array.from会返回一个一模一样的新数组
```

参考：https://www.cnblogs.com/jf-67/p/8440758.html

### Array.reduce()

```
语法：

array.reduce(function(accumulator, currentValue, currentIndex, array), initialValue)；

accumulator：累加器，即函数上一次调用的返回值。第一次的时候为 initialValue || arr[0]

currentValue：数组中函数正在处理的的值。第一次的时候initialValue || arr[1]

currentIndex：数据中正在处理的元素索引，如果提供了 initialValue ，从0开始；否则从1开始

array： 调用 reduce 的数组

initialValue：可选项，累加器的初始值。没有时，累加器第一次的值为currentValue；注意：在对没有设置初始值的空数组调用reduce方法时会报错。
```

```js
//无初始值
[1, 2, 3, 4].reduce(function(accumulator, currentValue, currentIndex, array) {
  return accumulator + currentValue;
}); // 10
```

| callback    | accumulator       | currentValue      | currentIndex    | array        | return value |
| ----------- | ----------------- | ----------------- | --------------- | ------------ | ------------ |
| first call  | 1(数组第一个元素) | 2(数组第二个元素) | 1(无初始值为 1) | [1, 2, 3, 4] | 3            |
| second call | 3                 | 3                 | 2               | [1, 2, 3, 4] | 6            |
| third call  | 6                 | 4                 | 3               | [1, 2, 3, 4] | 10           |

```js
//有初始值
[1, 2, 3, 4].reduce(function(accumulator, currentValue, currentIndex, array) {
  return accumulator + currentValue;
}, 10); // 20
```

| callback    | accumulator | currentValue      | currentIndex    | array        | return value |
| ----------- | ----------- | ----------------- | --------------- | ------------ | ------------ |
| first call  | 10(初始值)  | 1(数组第一个元素) | 0(有初始值为 0) | [1, 2, 3, 4] | 11           |
| second call | 11          | 2                 | 1               | [1, 2, 3, 4] | 13           |
| third call  | 13          | 3                 | 2               | [1, 2, 3, 4] | 16           |
| fourth call | 16          | 4                 | 3               | [1, 2, 3, 4] | 20           |

```js
//1.数组元素求和
[1, 2, 3, 4].reduce((a, b) => a + b); //10

//2.二维数组转化为一维数组
[[1, 2], [3, 4], [5, 6]]
  .reduce((a, b) => a.concat(b), []) //[1, 2, 3, 4, 5, 6]

  [
    //3.计算数组中元素出现的次数
    (1, 2, 3, 1, 2, 3, 4)
  ].reduce((items, item) => {
    if (item in items) {
      items[item]++;
    } else {
      items[item] = 1;
    }
    return items;
  }, {}) //{1: 2, 2: 2, 3: 2, 4: 1}

  [
    //数组去重①
    (1, 2, 3, 1, 2, 3, 4, 4, 5)
  ].reduce((init, current) => {
    if (init.length === 0 || init.indexOf(current) === -1) {
      init.push(current);
    }
    return init;
  }, []) //[1, 2, 3, 4, 5]
  [
    //数组去重②
    (1, 2, 3, 1, 2, 3, 4, 4, 5)
  ].sort()
  .reduce((init, current) => {
    if (init.length === 0 || init[init.length - 1] !== current) {
      init.push(current);
    }
    return init;
  }, []); //[1, 2, 3, 4, 5]
```

参考：https://www.cnblogs.com/xuejiangjun/p/8523313.html

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
[参考](https://www.jianshu.com/p/bc28e4f67ef9)

</details>

<b><details><summary>7.var let 在 for 循环中的区别</summary></b>
答案：

解析：
[参考](https://blog.csdn.net/zoelinjf/article/details/79618688)

</details>

<b><details><summary>8.Set 数据结构</summary></b>

答案：

- es6 方法,Set 本身是一个构造函数，它类似于数组，但是成员值都是唯一的。

```js
const set = new Set([1, 2, 3, 4, 4]);
console.log([...set]); // [1,2,3,4]
console.log(Array.from(new Set([2, 3, 3, 5, 6]))); //[2,3,5,6]
```

</details>

<b><details><summary>9.Class 的讲解</summary></b>

答案：

- class 语法相对原型、构造函数、继承更接近传统语法，它的写法能够让对象原型的写法更加清晰、面向对象编程的语法更加通俗
  这是 class 的具体用法。

解析：
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

<b><details><summary>41.ES6 如何动态加载import</summary></b>

答案：
```js
import('lodash').then(_ => {
  // Do something with lodash (a.k.a '_')...
 })
 ```

解析：[参考](https://webpack.js.org/api/module-methods/#import)

</details>

<b><details><summary>42.说说你对promise的了解</summary></b>

</details>

<b><details><summary>43.谈谈你对ES6的理解</summary></b>

</details>

<b><details><summary>44.ECMAScript6 怎么写class么，为什么会出现class这种东西?</summary></b>

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
