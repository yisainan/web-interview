# [返回主页](https://github.com/yisainan/web-interview/blob/master/README.md)

<b><details><summary>1.(单选题)下面代码的输出是什么 </summary></b>

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

答案：C

解析：

new Number ()是一个内置的函数构造函数。虽然它看起来像一个数字，但它并 不是一个真正的 数 字 ： 它 有 一堆额外的功能，是一个对象。

当我们使用 == 运算符时，它只检查它是否具有相同的值。他们都有3的值，所以返回true

译者注：==会引发隐式类型转换，右侧的对象类型会自动转换为Number类型

然而，当我们使用 === 操作符是，类型和值都需要相等，Number()不是一个数字，是对象类型。两者都返回false

[参与互动](https://github.com/yisainan/web-interview/issues/1022)

</details>

<b><details><summary>2.(单选题）当我们这样做时会发生什么? </summary></b>

```js
function bark() {
    console.log('Woof!');
}
bark.animal - 'dog';
```

```
A：Nothing, this is totally fine!
B: SyntaxError. You cannot add properties to a function this way.
C: undefined
D: ReferenceError
```

答案：A

解析：

这在JavaScript中是可能的，因为函数也是对象！（ 原始类型之外的所有东西都是对象）

函数是一种特殊类型的对象。您自己编写的代码并不是实际的函数。该函数是具有属性的对象，此属性是可调用的。

[参与互动](https://github.com/yisainan/web-interview/issues/1023)

</details>

<b><details><summary>3.(单选题)下面代码的输出是什么 </summary></b>

```js
String.prototype.giveLydiaPizza = () = > {
    return 'Just give Lydia pizza already!';
};

const name = 'Lydia';
name.giveLydiaPizza();
```

```
A："Just give Lydia pizza already!"
B: TypeError: not a function
C: SyntaxError 
D: undefined
```

答案：A

解析：

String是一个内置的构造函数，我们可以为它添加属性。我刚给它的原型添加了一t方法。原始类型的字符串自动转换为字符串对象，由字符串原型函数生成。因此，所有字符串（字符串对象）都可以访问该方法！

当使用基本类型的字符串调用giveLydiaPizza时，实际上发生了下面的过程：

* 创 建 一 个String的包装类型实例 
* 在 实 例 上 调 用substring方法 
* 销毁实例

[参与互动](https://github.com/yisainan/web-interview/issues/1024)

</details>

<b><details><summary>4.(单选题)下面代码的输出是什么 </summary></b>

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

答案：D

解析：

当我们从右侧的对象解构属性name时，我们将其值Lydia分配给名为myName的变量。

使用{name: myName}，我们是在告诉JavaScript我们要创建一个名为myName的新变量，并且其值是右侧对象的name属性的值。

当我们尝试打印name，一个未定义的变量时，就会引发 ReferenceError

[参与互动](https://github.com/yisainan/web-interview/issues/1025)

</details>

<b><details><summary>5.(单选题)下面代码的输出是什么 </summary></b>

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

答案：C

解析：

变量name保存字符串的值，该字符串不是函数，因此无法调用。

当值不是预期类型时，到抛出TypeErrors。JavaScript期望name是一个函数，因为我们试图调用它。但它是一个字符串，因此抛出TypeError : name is not a function

当你编写了一些非有效的JavaScript时，会拋出语法错误，例如当你把return这个词写成retrun时。当Script无法找到您尝试访问的值的引用时，抛出ReferenceErrors

[参与互动](https://github.com/yisainan/web-interview/issues/1026)

</details>

<b><details><summary>6.(单选题)下面代码的输出是什么 </summary></b>

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

答案：B

解析：

this关键字的指向取决于使用它的位置。在函数中, 比如 getStatus, this指向的是调用它的对象, 上述例子中data对象调用了 getStatus因此this指向的就是data对象, 当我们打印this.status时, data对象
的 status属性被打印, 即'🐍'。

使用call方法, 可以更政this指向的对象。data.getStatus.call(this)是将this的指向由data对象更改为全局对象。在全局对象上, 有一个名为 status的变量, 其值为'🐰'。因此打印this.status时, 会打印'🐰'

[参与互动](https://github.com/yisainan/web-interview/issues/1027)

</details>

<b><details><summary>7.(单选题)下面代码的输出是什么 </summary></b>

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

答案：A

解析：

我们将变量city设置为等于person对象上名为city的属性的值。这个对象上沒有名为city的属性，因此变量city 的值为 undefined。

请注意，我们没有引用person对象本身，只是将变量city设置为等于person对象上city属性的当前值。
然后，我们将city设置为等于字符串"Amsterdam'。这不会更改person对象：没有对该对象的引用。因此打印person对象时，会返回未修改的对象。

[参与互动](https://github.com/yisainan/web-interview/issues/1028)

</details>

<b><details><summary>8.(单选题)下面代码的输出是什么 </summary></b>

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

答案：B

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

<b><details><summary>9.(单选题)下面代码的输出是什么 </summary></b>

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

答案：C

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

<b><details><summary>10.(单选题)下面代码的输出是什么 </summary></b>

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

答案：D

解析：

Set对象是独一无 二 的 值 的 集 合 ： 也 就 是 说 同 一 在 其中仅出现一次。

我 们 传 入 了 数 组 [ 1 , 1 , 2 , 3 , 4 ] , 他 有 一个重复值以为一个集合里不能有两个重复的值，其中一个就被移除了。所以结果是{1, 2, 3, 4}.

[参与互动](https://github.com/yisainan/web-interview/issues/1031)

</details>
