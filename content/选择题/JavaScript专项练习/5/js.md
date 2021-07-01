# [返回主页](https://github.com/yisainan/web-interview/blob/master/README.md)

<b><details><summary>1.(单选题)下面代码的输出是什么 </summary></b>

```js
Promise.resolve(5)
```

```
A: 5
B: Promise {<pending>: 5}
C: Promise {<resolved>: 5}
D: Error
```

答案: C

解析：

我们可以将我们想要的任何类型的值传递Promise.resolve , 无论是否promise。该方法本身返回带有已解析值的Promise。如果您传递常规函数, 它将是具有常规值的已解决promise。如果你通过了promise , 它将是一个已经resolved的且带有传的值的promise。
上述情况，我们传了数字5 , 因此返回一个resolved状态的promise , resolve值为 5

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>2.(单选题)下面代码的输出是什么 </summary></b>

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

答案: D

解析：

在ES2020中，通过#我们可以给class添加私有变量。
在class的外部我们无法获取该值。当我们尝试输出counter.#number , 语法错误被抛出：我们无法在class Counter外部获取它！

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>3.(单选题)哪个选项不正确？ </summary></b>

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

答案: A

解析：

在JavaScript中，所有对象键都是字符串（ 除了 Symbol）。尽管有时我们可能不会给定字符串类型， 但它们总是被转换为字符串。 JavaScript解释语句。 当我们使用方括号表示法时， 它会看到第一个左括号［, 然后继续， 直到找到右括号］。 只有在那个时候， 它才会对这个语句求值。 

mouse[bird, size]: 首先它会对 bird.size 求值， 得到small。 mouse["small”]返回 true。

但是，使用点表示法，这不会发生。 mouse没有名为bird的键， 这意味着mouse.bird是undefined。 然后，我们使用点符号来询问size： mouse.bird.size 。由于mouse.bird是undefined, 我们实际上是在询问undefined.size。 这是无效的，并将抛出Cannot read Property 'size' of undefined

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>4.(单选题)下面代码的输出是什么 </summary></b>

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

答案: C

解析：

使用||运算符，我们可以返回第一个真值。如果所有值都是假值，则返回最后一个值。
（false || {} || null）: 空对象{}是一个真值。 
这是第一个（也是唯一的）真值，它将被返回。one等于{}

（null || false || ""）：所有值都是假值。这意味着返回传递的值'', two等于''。

（［］|| 0 || ""）: 空教组［］是一个真值。这是第一个返回的真值。three等于[]。

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>5.(单选题)下面哪个选项将会返回6 </summary></b>

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

答案: 

解析：

通过展开操作符...， 我们可以暂开单个可迭代的元素。 函数sumValues function接收三个参数: x, y和z，[1, 2, 3] 的执行结果为1, 2, 3， 将会传递给函数：sumValues

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>6.(单选题)下面代码的输出是什么 </summary></b>

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

答案: A

解析：

我们可以用delete关键字删除对象的属性，对原型也是适用的。删除了原型的属性后，该属性在原型链上就不可用了。在本例中，函数bark在执行了 delete Dog.prototype.bark后不可用，然而后面的代码还在调用它。
当我们尝试调用一个不存在的函数时TypeError 
异常被抛出。在本例中就是TypeError: pet.bark is not a function，因为 pet.bark 是 undefined

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>7.(单选题)下面代码的输出是什么 </summary></b>

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

答案: B

解析：

通过 += 操作符， 我们对值num进行加1操作。 num有初始值1, 因此1 + 1 的执行结果为2。 数组list的第二项为"c"

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>8.(单选题)下面哪一项会对对象person有副作用 </summary></b>

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

答案: A

解析：

使用Object.seal我们可以防止新属性被添加， 或者存在属性被移除。然而，你仍然可以对存在属性进行更改。

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>9.(单选题)下面代码的输出是什么 </summary></b>

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

答案: D

解析：

Set对象是独一无二的值的集合： 也就是说同一个值在其中仅出现一次。
我们传入了数组[1, 1, 2, 3, 4], 他 有 一 个 重 复 值 为1
因为一个集合里不能有两个重复的值， 其中一个就被移除了。 所以结果是｛ 1, 2, 3, 4 }.

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>10.(单选题)下面代码的输出是什么 </summary></b>

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

答案: C

解析：

typeof name 返回 'string'。字符串 'string'
是一个truthy的值， 因此!typeof name返回一个布尔值false 。false === 'object'和false === 'string'
都返回false。（ 如果我们想检测一个值的类型， 这里我们应该用 !== 而不是!typeof）

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>
