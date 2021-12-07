# [返回主页](https://github.com/yisainan/web-interview/blob/master/README.md)

> 转载自 微信小程序：高级前端面试-选择题

<b><details><summary>1.(单选题)下面代码的输出是什么 </summary></b>

```js
const name = "Lydia";
age = 21;

console.log(delete name);
console.log(delete age);
```

```
A: false, true
B: "Lydia", 21
C: true, true
D: undefined, undefined
```

参考答案: A

解析: 

delete 操作符返回一个布尔值: true 指删除成功，否则返回 false . 但是通过 var , const 或 let 关键字声明的变量无法用 delete 操作符来删除。

name 变量由 const 关键字声明，所以删除不成功: 返回 false 而我们设定 age 等于 21 时，我们实际上添加了一个名为 age 的属性给全局对象。对象中的属性是可以删除的，全局对象也是如此，所以 delete age 返回 true

[参与互动](https://github.com/yisainan/web-interview/issues/1012)

</details>

<b><details><summary>2.(单选题)我们需要向对象 person 添加什么，以致执行[…person]时获得形如['Lydia Hallie', 21]的输出？ </summary></b>

```js
const person = {
    name: 'Lydia Hallie',
    age: 21
}
[...person] // ['Lydia Hallie', 21]
```

```
A: 不需要，对象默认就是可迭代的
B: *[Symbol.iterator]() { for (let x in this) yield* this
[x]}
C: *[Symbol.iterator]() {yield* Object.values(this)}
D: *[Symbol.iterator]() { for (let x in this) yield this }
```

参考答案: C

解析: 

对象默认是不可迭代的。如果迭代规则被定义，则一个对象是可迭代的（ An iterable is an iterable if the iterator protocol is present)。我们可以通过添加迭代器 symbol [Symbol.iterator]来定义迭代规则，其返回一个 generator 对象，比如说构建一个 generator 函数 _[Symbol.iterator](){}。如果我们想要返回数组['Lydia Halli', 21] :yield_ Object.values(this), 这个 geneator 函数一定要 yield 对象 person 的 Object.values

[参与互动](https://github.com/yisainan/web-interview/issues/1013)

</details>

<b><details><summary>3.(单选题)下面代码的输出是什么 </summary></b>

```js
const set = new Set();

set.add(1);
set.add("Lydia");
set.add({
    name: "Lydia"
});

for (let item of set) {
    console.log(item + 2);
}
```

```
A: 3, NaN, NaN
B: 3, 7, NaN
C: 3, Lydia2, [Object object]2
D: "12", Lydia2, [Object object]2
```

参考答案: C

解析: 

“+”运算符不仅用于添加数值，还可以使用它来连接字符串。每当 JavaScript 引擎发现一个或多个值不是数字时，就会持数字强制为字符串。第一个是数字 1。1+2 返回数字 3。

但是，第二个是字符串“Lydia”。“Lydia”是一字符串，2 是一数字: 2 被强制转换为字符串。“Lydia”和“2”被连接起来，产生字符串“Lydia2”。

{name : "Lydia"}是一个对象。数字和对象都不是字符串，因此将二者都字符串化。每当我们对常规对象进行字符串化时，它就会变成[Object object]。与“2”串联的“[Object object]”成为“[Object object]2”。

[参与互动](https://github.com/yisainan/web-interview/issues/1014)

</details>

<b><details><summary>4.(单选题)下面代码的输出是什么 </summary></b>

```js
const settings = {
    username: 'lydiahallie',
    level: 19,
    health: 90
};
const data = JSON.stringify(settings, ['level', 'health']);
console.log(data);
```

```
A: "{"level":19, "health":90}"
B: "{"username": "lydiahallie"}"
C: "{"level", "health"]"
D: "{"username": "lydiahallie", "level":19, "health":90}"
```

参考答案: A

解析: 

JSON.stringify 的第二个参数是替代者（replacer）. 替代者(replacer)可以是个函数或数组，用以控制哪些值如何被转换为字符串。

如果替代者(replacer)是个数组，那么就只有包含在数组中的属性将会被转化为字符串。在本例中，只有名为'level'和'health'的属性被包括进来，'username'则被排除在外。data 就等于 "{"level":19, "health":90}"

而如果替代者(replacer)是个函数，这个函数将被对象的每个属性都调用一遍。函数返回的值会成为这个属性的值，最终体现在转化后的 JSON 字符串中（译者注: Chrome 下，经过实验，如果所有属性均返回同一个值的时候有异常，会直接将返回值作为结果输出而不会输出 JSON 字符串），而如果返回值为 undefined , 则该属性会被排除在外。

[参与互动](https://github.com/yisainan/web-interview/issues/1015)

</details>

<b><details><summary>5.(单选题)下面代码的输出是什么 </summary></b>

```js
const name = "Lydia";

console.log(name());
```

```
A: SyntaxError
B: ReferenceError
C: TypeError
D: undefined
```

参考答案: C

解析: 

变量 name 保存字符串的值，该字符串不是函数，因此无法调用。

当值不是预期类型时，到抛出 TypeError。JavaScript 期望 name 是一个函数，因为我们试图调用它。但它是一个字符串，因此抛出 TypeError : name is not a function

[参与互动](https://github.com/yisainan/web-interview/issues/1016)

</details>

<b><details><summary>6.(单选题)下面代码的输出是什么 </summary></b>

```js
console.log("🐭" + "🐍");
```

```
A: 🐭🐍
B:257548
C:A string containing their code points
D:Error
```

参考答案: A

解析: 

使用+运算符，您可以连接字符串。上述情况，我们将字符串"🐭" 与 字 符 串 "🐍"连 接 起 来 ， 产 生 🐭🐍

[参与互动](https://github.com/yisainan/web-interview/issues/1017)

</details>

<b><details><summary>7.(单选题)下面代码的输出是什么 </summary></b>

```js
let newList = [1, 2, 3].push(4);

console.log(newList.push(5));
```

```
A: [1,2,3,4,5]
B: [1,2,3,5]
C: [1,2,3,4]
D: Error
```

参考答案: D

解析: 

.push()方法返回数组的长度，而不是数组的本身。

[参与互动](https://github.com/yisainan/web-interview/issues/1018)

</details>

<b><details><summary>8.(单选题)下面代码的输出是什么 </summary></b>

```js
let name = "Lydia";

function getName() {
    console.log(name);
    let name = "Sarah";
}
getName();
```

```
A: Lydia
B: Sarah
C: undefined
D: ReferenceError
```

参考答案: D

解析: 

每个函数都有其自己的执行上下文。getName 函数首先在其自身的上下文（范围）内查找，以查看其是否包含我们尝试访问的变量 name。上述情况，getName函数包含其自己的 name 变量: 我们用 let 关键字和 Sarah 的值声明变量 name。

带有 let 关键字（和 const)的变量被提升，但是与 var 不同，它不会被初始化。在我们声明（初始化） 它们之前，无法访问它们。这称为“暂时性死区”。当我们尝试在声明变量之前访问变量时，JavaScript 会抛出 ReferenceError: Cannot access 'name' before initialization。

如果我们不在 getName 函数中声明 name 变量，则 javascript 引擎会查看原型链。会找到其外部作用域有一个名为 name 的变量，其值为 Lydia。在这种情况下，它
将打印 Lydia :

```js
let name = 'Lydia'

function getName()
console.log(name)
}
getName() // Lydia
```

[参与互动](https://github.com/yisainan/web-interview/issues/1019)

</details>

<b><details><summary>9.(单选题)下面代码的输出是什么 </summary></b>

```js
function getAge(...args) {
    console.log(typeof args);
}
getAge(21);
```

```
A: "number"
B: "array"
C: "object"
D: "NaN"
```

参考答案: C

解析: 

扩展运算符（...args )返回一个带参数的数组。 
数组是一个对象，因此typeof args返回object。

[参与互动](https://github.com/yisainan/web-interview/issues/1020)

</details>

<b><details><summary>10.(单选题)下面代码的输出是什么 </summary></b>

```js
[1, 2, 3, 4].reduce((x, y) => console.log(x, y))
```

```
A: 1 2 and 3 3 and 6 4 
B: 1 2 and 2 3 and 3 4
C: 1 undefined and 2 undefined and 3 undefined and 4 undefined
D: 1 2 and undefined 3 and undefined 4 
```

参考答案: D

解析: 

![001](../images/001.png)

reduce函数接收4个参数: 
• total (累加器）
• currentValue (当前值）
• currentIndex (当前索引）
• arr (源数组）

reduce 函数的返回值将会分配给累加器，该返回值在数组的每个迭代中被记住，并最后成为最终的单个结果值。

reduce函数还有一个可选参数initialValue, 该参数将作为第一次调用回调函数时的第一个参数的值。如果没有提供initialValue , 则将使用数组中的第一个元素。

在上述例子, reduce方法接收的第一个参数(total)是 x, 第二个参数(currentValue)是 y。

在第一次调用时，累加器x为1 , 当 前 值'y'为 2  , 打印出累加器和当前值: 1 和 2。

在第二次调用时，我们的回调函数没有返回任何值，只是打印累加器的值和当前值。如果函数没有返回值，则默认返回undefined。在下一次调用时，累加器为undefined , 当前值为'3'，因此undefined和3被打印出来。

在第三次调用时，回调函数依然没有返回值。累加器再次为 undefined , 当前值为“4”。undefined 和 4 被打印出来。

如果改造成以下代码：
```js
[1, 2, 3, 4].reduce((x, y) => { console.log(x, y); return x + y; }, 100)

// 打印
// 100 1
// 101 2
// 103 3
// 106 4
```

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>11.(单选题)下面代码的输出是什么 </summary></b>

```js
let a = 3;
let b = new Number(3)
let c = 3;

console.log(a == b);
console.log(a === b);
console.log(b === c);
```

```
A：true false true
B: false false true
C: true false false
D: false true true
```

参考答案：C

解析：

new Number ()是一个内置的函数构造函数。虽然它看起来像一个数字，但它并不是一个真正的数 字：它有一堆额外的功能，是一个对象。

当我们使用 == 运算符时，它只检查它是否具有相同的值。他们都有3的值，所以返回true

译者注：==会引发隐式类型转换，右侧的对象类型会自动转换为Number类型

然而，当我们使用 === 操作符是，类型和值都需要相等，Number()不是一个数字，是对象类型。两者都返回false

[参与互动](https://github.com/yisainan/web-interview/issues/1022)

</details>

<b><details><summary>12.(单选题）当我们这样做时会发生什么? </summary></b>

```js
function bark() {
    console.log('Woof!');
}
bark.animal = 'dog';
```

```
A：Nothing, this is totally fine!
B: SyntaxError. You cannot add properties to a function this way.
C: undefined
D: ReferenceError
```

参考答案：A

解析：

这在JavaScript中是可能的，因为函数也是对象！（ 原始类型之外的所有东西都是对象）

函数是一种特殊类型的对象。您自己编写的代码并不是实际的函数。该函数是具有属性的对象，此属性是可调用的。

[参与互动](https://github.com/yisainan/web-interview/issues/1023)

</details>

<b><details><summary>13.(单选题)下面代码的输出是什么 </summary></b>

```js
String.prototype.giveLydiaPizza = () => {
  return "Just give Lydia pizza already!";
};

const name = "Lydia";
name.giveLydiaPizza();
```

```
A: "Just give Lydia pizza already!"
B: TypeError: not a function
C: SyntaxError
D: undefined
```

参考答案：A

解析：

String是一个内置的构造函数，我们可以为它添加属性。 我刚给它的原型添加了一个方法。 原始类型的字符串自动转换为字符串对象，由字符串原型函数生成。 因此，所有字符串（字符串对象）都可以访问该方法！

当使用基本类型的字符串调用giveLydiaPizza时，实际上发生了下面的过程：

* 创建一个String的包装类型实例
* 在实例上调用substring方法
* 销毁实例

[参与互动](https://github.com/yisainan/web-interview/issues/1024)

</details>

<b><details><summary>14.(单选题)下面代码的输出是什么 </summary></b>

```js
const {
    name: myName
} = {
    name: 'Lydia'
}

console.log(name)
```

```
A："Lydia" 
B: "myName" 
C: undefined 
D: ReferenceError
```

参考答案：D

解析：

当我们从右侧的对象解构属性name时，我们将其值Lydia分配给名为myName的变量。

使用{name: myName}，我们是在告诉JavaScript我们要创建一个名为myName的新变量，并且其值是右侧对象的name属性的值。

当我们尝试打印name，一个未定义的变量时，就会引发 ReferenceError

[参与互动](https://github.com/yisainan/web-interview/issues/1025)

</details>

<b><details><summary>15.(单选题)下面代码的输出是什么 </summary></b>

```js
const name = 'Lydia'

console.log(name())
```

```
A：SyntaxError 
B: ReferenceError 
C: TypeError 
D: undefined
```

参考答案：C

解析：

变量name保存字符串的值，该字符串不是函数，因此无法调用。

当值不是预期类型时，到抛出TypeErrors。JavaScript期望name是一个函数，因为我们试图调用它。但它是一个字符串，因此抛出TypeError : name is not a function

当你编写了一些非有效的JavaScript时，会拋出语法错误，例如当你把return这个词写成retrun时。当Script无法找到您尝试访问的值的引用时，抛出ReferenceErrors

[参与互动](https://github.com/yisainan/web-interview/issues/1026)

</details>

<b><details><summary>16.(单选题)下面代码的输出是什么 </summary></b>

```js
var status = '🐰'
setTimeout(() => {
    const status = '🐎'
    const data = {
        status: '🐍'
        getStatus() {
            return this.status
        }
    }
    console.log(data.getStatus())
    console.log(data.getStatus.call(this))
}, 0)
```

```
A：'🐍' and '🐎'
B: '🐍' and '🐰'
C: '🐎' and '🐰'
D: '🐰' and '🐰'
```

参考答案：B

解析：

this关键字的指向取决于使用它的位置。在函数中, 比如 getStatus, this指向的是调用它的对象, 上述例子中data对象调用了 getStatus因此this指向的就是data对象, 当我们打印this.status时, data对象
的 status属性被打印, 即'🐍'。

使用call方法, 可以更政this指向的对象。data.getStatus.call(this)是将this的指向由data对象更改为全局对象。在全局对象上, 有一个名为 status的变量, 其值为'🐰'。因此打印this.status时, 会打印'🐰'

[参与互动](https://github.com/yisainan/web-interview/issues/1027)

</details>

<b><details><summary>17.(单选题)下面代码的输出是什么 </summary></b>

```js
const person = {
    name: 'Lydia',
    age: 21
}

let city = person.city
city = 'Amsterdam'
console.log(person)
```

```
A：{ name: "Lydia", age: 21}
B: { name: "Lydia", age: 21, city: "Amsterdam"}
C: { name: "Lydia", age: 21, city: undefined }
D: "Amsterdam"
```

参考答案：A

解析：

我们将变量city设置为等于person对象上名为city的属性的值。这个对象上沒有名为city的属性，因此变量city 的值为 undefined。

请注意，我们没有引用person对象本身，只是将变量city设置为等于person对象上city属性的当前值。
然后，我们将city设置为等于字符串"Amsterdam'。这不会更改person对象：没有对该对象的引用。因此打印person对象时，会返回未修改的对象。

[参与互动](https://github.com/yisainan/web-interview/issues/1028)

</details>

<b><details><summary>18.(单选题)下面代码的输出是什么 </summary></b>

```js
function sum(numl, num2 = numl) {
    console.log(numl + num2)
}
sum(10)
```

```
A：NaN
B: 20
C: ReferenceError
D: undefined
```

参考答案：B

解析：

您可以将默认参数的值设置为函数的另一个参数，只要另一个参数定义在其之前即可。我们将值10传递给sum函数。如果sum函数只接收1个参数，则意味看没有传递 num2 的 值 . 这 种 情 况 下 的 值 等 于 传 递 的 值 10。num2 的默认值是num1 的值，即10 。 num1  + num2 返回 20。

如果您尝试将默认参数的值设置为后面定义的参数，则可能导致参数的值尚未初始化，从而引发错误。比如：

```js
function test(m = n, n = 2) {
    console.log(m, n)
}
test() // Uncaught ReferenceEmor: Cannot access 
test(3) // 3 2
test(3, 4) // 3 4
```

[参与互动](https://github.com/yisainan/web-interview/issues/1029)

</details>

<b><details><summary>19.(单选题)下面代码的输出是什么 </summary></b>

```js
function* generatorOne() {
    yield ['a', 'b', 'c'];
}

function* generatorTwo() {
    yield*['a', 'b', 'c'];
}

const one = generatorOne()
const two = generatorTwo()

console.log(one.next().value)
console.log(two.next().value)
```

```
A：a and a
B: a and undefined 
C: ['a', 'b', 'c'] and a
D: a and ['a', 'b', 'c']
```

参考答案：C

解析：

通过yield关键字, 我们在Generator函数里执行yield表达式. 通过yield*关键字，我们可以在一个Generator函数里面执行（yield表达式）另一个Generator 函数，或可遍历的对象(如数组).

在函数generatorOne中，我们通过yield关键字yield 了一个完整的数组['a', 'b', 'c']。函数one通过next方法返回的对象的value属性的值（one.next().value)等价于数组['a', 'b', 'c']

```js
console.log(one.next().value) // ['a', 'b', 'c'] 
console.log(one.next().value) // undefined
```

在函数generatorTwo中，我们使用yield*关键字。就相当于函数two第一个yield的值, 等价于在迭代器中第一个yield的值。数组 ['a', 'b', 'c'] 就是个迭代器. 第一个 yield的值就是a , 所以我们第_次调用two.next().value 时，就返回 a。

```js
console.log(two.next().value) // 'a'
console.log(two.next().value) // 'b'
console.log(two.next().value) // 'c'
console.log(two.next().value) // underfined
```

[参与互动](https://github.com/yisainan/web-interview/issues/1030)

</details>

<b><details><summary>20.(单选题)下面代码的输出是什么 </summary></b>

```js
const set = new Set([1, 1, 2, 3, 4]);
console.log(set);
```

```
A：[1,1, 2, 3, 4]
B: [1,2, 3, 4]
C: {1,1, 2, 3, 4}
D: {1, 2, 3, 4}
```

参考答案：D

解析：

Set对象是独一无 二 的 值 的 集 合 ： 也 就 是 说 同 一 在 其中仅出现一次。

我 们 传 入 了 数 组 [ 1 , 1 , 2 , 3 , 4 ] , 他 有 一个重复值以为一个集合里不能有两个重复的值，其中一个就被移除了。所以结果是{1, 2, 3, 4}.

[参与互动](https://github.com/yisainan/web-interview/issues/1031)

</details>

<b><details><summary>21.(单选题)下面代码的输出是什么 </summary></b>

```js
const shape = {
    radius: 10,
    diameter() {
        return this.radius * 2;
    },
    perimeter: () => 2 * Math.PI * this.radius
};

shape.diameter();
shape.perimeter();
```

```
A：20 and 62.83185307179586
B: 20 and NaN
C: 20 and 63
D: NaN and 63
```

参考答案：B

解析：

请注意, diameter 是普通函数, 而 perimeter 是箭头函数。对于箭头函数, this 关键字指向是它所在上下文(定义时的位置)的环境, 与普通函数不同! 这意味着当我们调用 perimeter 时, 它不是指向 shape 对象, 而是指其定义时的环境
( window)。没有值 radius 属性, 返回 undefined。

[参与互动](https://github.com/yisainan/web-interview/issues/1032)

</details>

<b><details><summary>22.(单选题)下面代码的输出是什么 </summary></b>

```js
const person = {
    name: "Lydia Hallie",
    hobbies: ["coding"]
};

function addHobby(hobby, hobbies = person.hobbies) {
    hobbies.push(hobby);
    return hobbies;
}

addHobby("running", []);
addHobby("dancing");
addHobby("baking", person.hobbies);
console.log(person.hobbies);
```

```
A：["coding"]
B: ["coding", "dancing"]
C: ["coding", "dancing", "baking"]
D: ["coding", "running", "dancing","baking"]
```

参考答案：C

解析：

函数 addHobby 接受两个参数，hobby 和有看对象 person 中数组 hobbies 默认值的 hobbies。

首先，我们调用函数 addHobby , 并给 hobby 传递'running'以及 hobbies 传递一个空数组。因为我们给 hobbies 传递了空数组，'running' 被 添加到这个空数组。

然后，我们调用函数 addHobby , 并给 hobby 传递'dancing'。我们不向 hobbies 传递值，因此它获取其默认值---对象 person 的属性 hobbies。我们向数组 person.hobbies push dancing

最后，我们调用函数 addHobby , 并向 hobby 传递值'baking'，并且向 hobbies 传递 person.hobbies。我们向数组 person.hobbies push dancing。

pushing dancing 和 baking 之后，person.hobbies 的值为['coding', 'dancing’，'baking']

[参与互动](https://github.com/yisainan/web-interview/issues/1033)

</details>

<b><details><summary>23.(单选题)下面代码的输出是什么 </summary></b>

```js
const myLifeSummedUp = ["a", "b", "c", "d"];

for (let item in myLifeSummedUp) {
    console.log(item);
}

for (let item of myLifeSummedUp) {
    console.log(item);
}
```

```
A：0 1 2 3 and 'a' 'b' 'c' 'd'
B: 'a' 'b' 'c' 'd' and 'a' 'b' 'c' 'd'
C: 0 1 2 3 and 0 1 2 3
D: 0 1 2 3 and {
    0: 'a',
    1: 'b',
    2: 'c',
    3: 'd'
}
```

参考答案：A

解析：

通过 for-in 循环，我们可以遍历一个对象自有的、继承的、可枚举的、非 symbol 的属性。在数组中，可枚举属性是数组元素的键，即它们的索引。类似于下面的这个对象：

```js
{
    0: 'a',
    1: 'b',
    2: 'c',
    3: 'd'
}
```

其中键则是可枚举属性，因此 0, 1, 2, 3 被记录。通过 for-of 循环，我们可以迭代可迭代对象（包括 Array，Map，Set，String，arguments 等）。当我们迭代数组时，在每次迭代中，不同属性的值将被分配给变量 item，因此'a' 'b' 'c' 'd'被打印

[参与互动](https://github.com/yisainan/web-interview/issues/1034)

</details>

<b><details><summary>24.(单选题)下面代码的输出是什么 </summary></b>

```js
const myFunc = ({
    x,
    y,
    z
}) => {
    console.log(x, y, z);
};

myFunc(1, 2, 3);
```

```
A：1 2 3
B: {1: 1} {2:2} {3:3}
C: {1: undefined} undefined undefined
D: undefined undefined undefined
```

参考答案：D

解析：

myFunc 期望接收一个包含 x，y 和 z 属性的对象作为它的参数，因为我们仅仅传递三个单独的数字值（1, 2, 3）不是一个含有 x，y 和 z 属性的对象({x:1, y:2, z:3}), x, y 和 z 有着各自的默认值 undefined

[参与互动](https://github.com/yisainan/web-interview/issues/1035)

</details>

<b><details><summary>25.(单选题)输出什么 </summary></b>

```js
const colorConfig = {
    red: true,
    blue: false,
    green: true,
    black: true,
    yellow: false
};

const colors = ["pink", "red", "blue"];

console.log(colorConfig.colors[1]);
```

```
A：true
B: false
C: undefined
D: TypeError
```

参考答案：D

解析：

在 JavaScript 中，我们有两种访问对象属性的方法：括号表示法或点表示法。在此示例中，我们使用点表示法(colorConfig.colors) 代替括号表示法(colorConfig["colors"]) 。

使用点表示法，JavaScript 会尝试使用该确切名称在对象 上查找属性。在此示例中，JavaScript 尝试在 colorconfig 对象上找到名为 colors 的属性。没有名为"colors"的属性，因此返回"undefined"。然后，我们尝试使用[1]访问第一个元 素 的 值 。 我 们 无 法 对 未 定 义 的 值执 行 此 操 作 ， 因此会抛出 Cannot read property '1' of undefined。JavaScript 解释（或取消装箱）语句。当我们使用方括号表示法时，它会看到第一个左方括号[并一直进行下去， 直到找到右方括号]。只有这样，它才会评估该语句。
如果我们使用了 colorConfig [colors [1]], 它将返回 colorConfig 对象上 red 属性的值。

[参与互动](https://github.com/yisainan/web-interview/issues/1036)

</details>

<b><details><summary>26.(单选题)输出什么 </summary></b>

```js
const food = ["A", "B", "C", "D"];
const info = {
    favoriteFood: food[0]
};
info.favoriteFood = "E";
console.log(food);
```

```
A：['A','B','C','D']
B: ['E','B','C','D']
C: ['E', 'A', 'B','C','D']
D: ReferenceError
```

参考答案：A

解析：

我们将 info 对象上的 favoriteFood 属性的值设置为"E"。字符串是原始数据类型。在 javaScript 中，原始数据类型通过值起作用。在这种情况下. 我们将 info 对象上的 favoriteFood 属性

性的值设置为等于 food 数组中的第一个元素的值，"A"。字符串是原始数据类型， 并且通过值进行交互，我们更改 info 对象上 favoriteFood 属性的值。food 数组没有改变，因为 favoriteFood 的值只是该数组中第一个元素的值的复制，并且与该元素上的元素没有相同的内存引用 food[0]。当我们记录 food 时，它仍然是原始数组['A', 'B', 'C', 'D']

[参与互动](https://github.com/yisainan/web-interview/issues/1037)

</details>

<b><details><summary>27.(单选题)输出什么 </summary></b>

```js
const randomValue = 21;

function getInfo() {
    console.log(typeof randomValue);
    const randomValue = "Lydia Hallie";
}
getInfo();
```

```
A："number"
B: "string"
C: undefined
D: ReferenceError
```

参考答案：D

解析：

通过 const 关键字声明的变量在被初始化之前不可被引用：这被称之为暂时性死区。在函数 getlnfo 中，变量 randomValue 声明在 getlnfo 的作用域的词法环境中。
在想要对 typeof randomValue 进行 log 之前，变量 randomValue 仍未被初始化：错误 ReferenceError 被抛出! JS 引擎并不会根据作用域链网上寻找该变量，因为我们已经在 getlnfo 函数中声明了randomValue 变量。

[参与互动](https://github.com/yisainan/web-interview/issues/1038)

</details>

<b><details><summary>28.(单选题)以下哪—项会对对象 person有副作用？</summary></b>

```js
const person = {
    name: 'Lydia Hallie',
    address: {
        street: '100 Main St'
    }
};
Object.freeze(person);
```

```
A：person.name = "Evan Bacon" 
B: delete person.address
C: person.address.street = "101 Main St" 
D: person.pet = { name: "Mara"}
```

参考答案：C

解析：

便用方法Object.freeze对一个对象进行冻结。不能对属性进行添加，修改，删除。然而，它仅对对象进行浅冻结，意味着只有对象中的直接属性被冻结。如果属性是另一个object, 像案例中的address, address中的属性没有被冻结，仍然可以被修改。

[参与互动](https://github.com/yisainan/web-interview/issues/1039)

</details>

<b><details><summary>29.(单选题)输出什么？</summary></b>

```js
// module.js
export default () => 'Hello world'
export const name s 'Lydia'
// index.js
import * as data from './module'
console.log(data)
```

```
A：{ default: function default(), name: "Lydia"}  
B: { default: function default() }
C: { default: "Hello world", name: "Lydia"}
D: Global object of module.js 
```

参考答案：A

解析：

使用import * as name语法，我们将module.js文件中所有export导入到index, js文件中，并且创建了一个名为data的新对象。在module.js文件中，有两个导出：默认导出和命名导出，默认导出是一个返回字符串'Hello world'的函数，命名导出是一个名为name的变量，其值为字符串
'Lydia'。

data对象具有默认导出的default属性，其他属性具有指定exports的名称及其对应的值

[参与互动](https://github.com/yisainan/web-interview/issues/1040)

</details>

<b><details><summary>30.(单选题）我们怎样才能在indexjs中调用sum.js中的sum ?</summary></b>

```js
// sum.js
export default function sum(x) {
    return x + x;
}

// index.js
import * as sum from './sum';
```

```
A：sum(4)
B: sum.sum(4)
C: sum.default(4)
D: 默认导出不用*来导入，只能具名导出 
```

参考答案：C

解析：

使用符号*，我们引入文件中的所有值，包括默认和具分章 
名。如果我们有以下文件：

```js
// info.js
export const name = 'Lydia';
export const age = 21;
export default 'I love JavaScript';

// index.js
import * as info from './info';
console.log(info);
```

将会输出以下内容：

```js
{
    default: 'I love JavaScript',
    name: 'Lydia',
    age: 21
}
```

以sum为例，相当于以下形式引入值sum :

```js
{
    default: function sum(x) {
        return x + x
    }
}
```

我们可以通过调用sum.default来调用该函数

[参与互动](https://github.com/yisainan/web-interview/issues/1041)

</details>

<b><details><summary>31.(单选题)下面代码的输出是什么 </summary></b>

```js
function Person(firstName, lastName) {
    this.firstName = firstName;
    this.lastName = lastName;
}
const member = new Person("Lydia', 'Hallie");
Person.getFullName = () => this.firstName + this.lastName；
console.log(member.getFullName());
```

```
A: TypeError
B: SyntaxError
C: Lydia Hallie
D: undefined undefined
```

参考答案: A

解析：

您不能像使用常规对象那样向构造函数添加属性。如果要 
一次向所有对象添加功能，则必须使用原型。所以在这种 
情况下应该这样写：

```js
Person.prototype.getFullName = function() {
    return '${this.firstName} ${this.lastName}';
}
```

这样会使member.getFullName()是可用的，为什么样 
做是对的？假设我们将此方法添加到构造函数本身。也 
许不是每个Person实例都需要这种方法。这会浪费大量 
内存空间，因为它们仍然具有该属性，这占用了每个实 
的内存空间。相反，如果我们只将它添加到原型中, 我们只需将它放在内存中的一个位置，但它们都可以访问它！

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>32.(单选题)下面代码的输出是什么 </summary></b>

```js
const person = {
    name: 'Lydia',
    age: 21
}
let city = person.city
city = 'Amsterdam'
console.log(person)
```

```

A: { name: "Lydia",age: 21}
B: { name: "Lydia",age: 21,city: "Amsterdam"}
C: { name: "Lydia",age: 21,city: undefined}
D: "Amsterdam"
```

参考答案：A

解析：

我们将变量city设置为等于person对象上名为city的属性的值。 这个对象上没有名为city的属性， 因此变量city 的值为 undefined。
请注意， 我们没有引用person对象本身， 只是将变量city设置为等于person对象上city属性的当前值。然后，我们将city设置为等于字符串“Amsterdam”。
这不会更改person对象： 没有对该对象的引用。
因此打印person对象时， 会返回未修改的对象。

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>33.(单选题)下面代码的输出是什么 </summary></b>

```js
(() => {
    let x, y;
    try {
        throw new Error。；
    } catch (x) {
        (x = 1), (y = 2);
        console.log(x);
    )
    console.log(x);
    console.log(y);
))()；
```

```
A: 1 undefined 2
B: undefined undefined undefined
C: 1 1 2
D: 1 undefined undefined
```

参考答案：A

解析：

catch块接收参数x。当我们传递参数时，这与变量的x不同。这个变量x是属于catch作用域的。
之后，我们将这个块级作用域的变量设置为1, 并设置变量y的值。现在，我们打印块级作用域的变量x , 它等于1。
在catch块之外，x仍然是undefined，而y是2。
我们想在catch块之外的console.log(x)时，它返回undefined , 而 y 返回 2。

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>34.(单选题)下面代码的输出是什么 </summary></b>

```js
let num = 1;
const list = ['A', 'B', 'C', 'D'];
console.log(list[(num += 1)]);
```

```
A: B
B: C
C: SyntaxError
D: ReferenceError
```

参考答案：B

解析：

通过 += 操作符， 我们对值num进行加1操作。 num有初始值1, 因此1 + 1 的执行结果为2。 数组list的第二项为'C'， console.log(list[2]) 输出'C'

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>35.(单选题)下面代码的输出是什么 </summary></b>

```js
class Chameleon {
    static colorChange(newColor) {
        this.newColor = newColor;
    }
    constructor({
        newColor = 'green'
    } = {}) {
        this.newColor = newColor;
    }
}
const freddie = new Chameleon({
    newColor: 'purple'
})
freddie.colorChange('orange');
```

```
A: orange
B: purple
C: green
D: TypeError
```

参考答案：D

解析：
colorChange方法是静态的。静态方法仅在创建它们的构造函数中存在，并且不能传递给任何子级。由于freddie是一个子级对象，函数不会传递，所以在freddie实例上不存在freddie方法：抛出TypeError。

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>36.(单选题)下面代码的输出是什么 </summary></b>

```js
const user = {
    name: 'Lydia',
    age: 21
};
const admin = {
    admin: true,
    ...user
};
console.log(admin);
```

```
A: {
    admin: true,
    user: {
        name: "Lydia",
        age: 21
    }
}

B: {
    admin: true,
    name: "Lydia",
    age: 21
}

C: {
    admin: true,
    user: ["Lydia", 21]
}

D: {admin: true}
```

参考答案：B

解析：

扩展运算符... 为对象的组合提供了可能。 你可以复制对象中的键值对， 然后把它们加到另一个对象里去。 在本例中， 我们复制了user对象键值对，然后把它们加入到admin对象中。 admin对象就拥有了这些键值对, 
所以结果为 

```js
{
    admin: true,
    name: 'Lydia',
    age: 21
}
```

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>37.(单选题)下面代码的输出是什么 </summary></b>

```js
let newList = [1, 2, 3].push(4)
console.log(newList.push(5))
```

```
A: [1, 2, 3, 4, 5]
B: [1, 2, 3, 5]
C: [1, 2, 3, 4]
D: Error
```

参考答案：D

解析：

.push方法返回数组的长度，而不是数组本身！ 通过将newList 设置为[1, 2, 3].push(4), 实际上 newList 等于数组的新长度： 4。
然后， 尝试在newList上使用.push方法。 由于newList是数值4, 抛出Error。

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>38.(单选题)下面代码的输出是什么 </summary></b>

```js
function compareMembers(person1, person2 = person) {
    if (person1 !== person2) {
        console.log('Not the same!')
    } else {
        console.log('They are the same!')
    }
}
const person = {
    name: 'Lydia'
}
compareMembers(person)
```

```
A: Not the same!
B: They are the same!
C: ReferenceError
D: SyntaxError
```

参考答案：B

解析：

对象通过引用传递。当我们检查对象的严格相等性（===）时，我们正在比较它们的引用。
我们将"person2"的默认值设置为“person”对象, 并将“person"对象作为"person1”的值传递。
这意味着两个值都引用内存中的同一位置，因此它们是相等的。
运行else语句中的代码块，并记录They are the same!

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>39.(单选题)下面代码的输出是什么 </summary></b>

```js
const box = {
    x: 10,
    y: 20
};
Object.freeze(box);
const shape = box;
shape.x = 100;
console.log(shape);
```

```
A: {x: 100, y:20}
B: {x: 10, y:20}
C: {x: 100}
D: ReferenceError
```

参考答案：B

解析：
Object.freeze使得无法添加、删除或修改对象的属性（除非属性的值是另一个对象）。
当我们创建变量shape并将其设置为等于冻结对象box时 
shape指向的也是冻结对象。你可以使用Object.isFrozen检查一个对象是否被冻结, 上述情况, Object.isFrozen （ shape ）将返回 true。
由于shape被冻结，并且x的值不是对象，所以我们不能修改属性X。x仍然等于10 , {x ： 10 , y ： 20}被打印。
注意，上述例子我们对属性x进行修改, 可能会导致抛出TypeError异常（最常见但不仅限于严格模式下时）。

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>40.(单选题)下面代码的输出是什么 </summary></b>

```js
const spookyltems = ['A', 'B', 'C'];
({
    item: spookyItems[3]
} = {
    item: 'D'
});
console.log(spookyltems);
```

```
A: ['A', 'B', 'C']
B: ['A', 'B', 'C', 'D']
C: ['A', 'B', 'C', {item: 'D'}]
D: ['A', 'B', 'C', "[object Object]"]
```

参考答案：B

解析：

通过解构对象们，我们可以从右手边的对象中拆出值，并且将拆出的值分配给左手边对象同名的属性。在这种情况下，我们将值'D'分配给spookyltems[3], 相当于我们正在篡改数组spookyltems , 我们给它添加了值'D'。当输出spookyltems时，结果为磅['A', 'B', 'C', 'D']

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>41.(单选题)下面代码的输出是什么 </summary></b>

```js
Promise.resolve(5)
```

```
A: 5
B: Promise {<pending>: 5}
C: Promise {<resolved>: 5}
D: Error
```

参考答案: C

解析：

我们可以将我们想要的任何类型的值传递Promise.resolve , 无论是否promise。该方法本身返回带有已解析值的Promise。如果您传递常规函数, 它将是具有常规值的已解决promise。如果你通过了promise , 它将是一个已经resolved的且带有传的值的promise。
上述情况，我们传了数字5 , 因此返回一个resolved状态的promise , resolve值为 5

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>42.(单选题)下面代码的输出是什么 </summary></b>

```js
class Counter {
    #number = 10
    increment() {
        this.#number++
    )
    getNum() {
        return this.#number
    )
}
const counter = new Counter()
counter.increment()
console.log(counter.#number)
```

```
A: 10
B: 11
C: undefined
D: SyntaxError
```

参考答案: D

解析：

在ES2020中，通过#我们可以给class添加私有变量。
在class的外部我们无法获取该值。当我们尝试输出counter.#number , 语法错误被抛出：我们无法在class Counter外部获取它！

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>43.(单选题)哪个选项不正确？ </summary></b>

```js
const bird = {
    size: 'small'
}；
const mouse = {
    name: 'Mickey',
    small: true
}；
```

```
A: mouse.bird.size
B: mouse[bird.size]
C: mouse[bird["sizen"]]
D: All of them are valid
```

参考答案: A

解析：

在JavaScript中，所有对象键都是字符串（ 除了 Symbol）。尽管有时我们可能不会给定字符串类型， 但它们总是被转换为字符串。 JavaScript解释语句。 当我们使用方括号表示法时， 它会看到第一个左括号［, 然后继续， 直到找到右括号］。 只有在那个时候， 它才会对这个语句求值。 

mouse[bird, size]: 首先它会对 bird.size 求值， 得到small。 mouse["small”]返回 true。

但是，使用点表示法，这不会发生。 mouse没有名为bird的键， 这意味着mouse.bird是undefined。 然后，我们使用点符号来询问size： mouse.bird.size 。由于mouse.bird是undefined, 我们实际上是在询问undefined.size。 这是无效的，并将抛出Cannot read Property 'size' of undefined

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>44.(单选题)下面代码的输出是什么 </summary></b>

```js
const one = (false || {} || null)
const two = (null || false || '')
const three = ([] || 0 || true)
console.log(one, two, three)
```

```
A: false null []
B: null "" true
C: {} "" []
D: null null true
```

参考答案: C

解析：

使用||运算符，我们可以返回第一个真值。如果所有值都是假值，则返回最后一个值。
（false || {} || null）: 空对象{}是一个真值。 
这是第一个（也是唯一的）真值，它将被返回。one等于{}

（null || false || ""）：所有值都是假值。这意味着返回传递的值'', two等于''。

（［］|| 0 || ""）: 空教组［］是一个真值。这是第一个返回的真值。three等于[]。

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>45.(单选题)下面哪个选项将会返回6 </summary></b>

```js
function sumValues(x, y, z) {
    return x + y + z;
)
```

```
A: sumValues([...1, 2, 3])
B: sumValues([...[1, 2, 3]])
C: sumValues(...[1, 2, 3])
D: sumValues([1, 2, 3])
```

参考答案: 

解析：

通过展开操作符...， 我们可以暂开单个可迭代的元素。 函数sumValues function接收三个参数: x, y和z，[1, 2, 3] 的执行结果为1, 2, 3， 将会传递给函数：sumValues

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>46.(单选题)下面代码的输出是什么 </summary></b>

```js
class Dog {
    constructor(name) {
        this.name = name;
    )
}
Dog.prototype.bark = function() {
    console.log(`Woof I am ${this.name}`);
)；
const pet = new Dog("Mara");
pet.bark();
delete Dog.prototype.bark;

pet.bark();
```

```
A: "Woof I am Mara", TypeError
B: "Woof I am Mara","Woof I am Mara"
C: "Woof I am Mara", undefined
D: TypeError, TypeError
```

参考答案: A

解析：

我们可以用delete关键字删除对象的属性，对原型也是适用的。删除了原型的属性后，该属性在原型链上就不可用了。在本例中，函数bark在执行了 delete Dog.prototype.bark后不可用，然而后面的代码还在调用它。
当我们尝试调用一个不存在的函数时TypeError 
异常被抛出。在本例中就是TypeError: pet.bark is not a function，因为 pet.bark 是 undefined

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>47.(单选题)下面代码的输出是什么 </summary></b>

```js
let num = 1;
const list = ["a", "b", "c", "d"];
console.log(list[(num += 1)]);
```

```
A: "b"
B: "c"
C: SyntaxError
D: ReferenceError
```

参考答案: B

解析：

通过 += 操作符， 我们对值num进行加1操作。 num有初始值1, 因此1 + 1 的执行结果为2。 数组list的第二项为"c"

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>48.(单选题)下面哪一项会对对象person有副作用 </summary></b>

```js
const person = {
    name: 'Lydia Hallie'
};
Object.seal（ person）;
```

```
A: person.name = "Evan Bacon"
B: person.age = 21
C: delete person.name
D: Object.assign(person,{ age: 21})
```

参考答案: A

解析：

使用Object.seal我们可以防止新属性被添加， 或者存在属性被移除。然而，你仍然可以对存在属性进行更改。

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>49.(单选题)下面代码的输出是什么 </summary></b>

```js
const set = new Set([1, 1, 2, 3, 4]);
console.log(set);
```

```
A: [1, 1, 2, 3, 4]
B: [1, 2, 3, 4]
C: {1, 1, 2, 3, 4}
D: {1, 2, 3, 4}
```

参考答案: D

解析：

Set对象是独一无二的值的集合： 也就是说同一个值在其中仅出现一次。
我们传入了数组[1, 1, 2, 3, 4], 他 有 一 个 重 复 值 为1
因为一个集合里不能有两个重复的值， 其中一个就被移除了。 所以结果是｛ 1, 2, 3, 4 }.

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>50.(单选题)下面代码的输出是什么 </summary></b>

```js
const name = "Lydia Hallie";
console.log(!typeof name === 'object');
console.log(!typeof name === 'string');
```

```
A: false true
B: true false
C: false false
D: true true
```

参考答案: C

解析：

typeof name 返回 'string'。字符串 'string'
是一个truthy的值， 因此!typeof name返回一个布尔值false 。false === 'object'和false === 'string'
都返回false。（ 如果我们想检测一个值的类型， 这里我们应该用 !== 而不是!typeof）

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>
