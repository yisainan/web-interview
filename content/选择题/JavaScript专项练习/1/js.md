# [返回主页](https://github.com/yisainan/web-interview/blob/master/README.md)

<b><details><summary>1.(单选题)下面代码的输出是什么 </summary></b>

```js
const name = "Lydia";
age = 21;

console.log(delete name);
console.log(delete age);
```

```
A：false, true
B: "Lydia", 21
C: true, true
D: undefined, undefined
```

答案：A

解析：

delete 操作符返回一个布尔值：true 指删除成功，否则返回 false .但是通过 var , const 或 let 关键字声明的变量无法用 delete 操作符来删除。

name 变量由 const 关键字声明，所以删除不成功:返回 false 而我们设定 age 等于 21 时，我们实际上添加了一个名为 age 的属性给全局对象。对象中的属性是可以删除的，全局对象也是如此，所以 delete age 返回 true

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
A：不需要，对象默认就是可迭代的
B: *[Symbol.iterator]() { for (let x in this) yield* this
[x]}
C: *[Symbol.iterator]() {yield* Object.values(this)}
D: *[Symbol.iterator]() { for (let x in this) yield this }
```

答案：C

解析：

对象默认是不可迭代的。如果迭代规则被定义，则一个对象是可迭代的（ An iterable is an iterable if the iterator protocol is present)。我们可以通过添加迭代器 symbol [Symbol.iterator]来定义迭代规则，其返回一个 generator 对象，比如说构建一个 generator 函数 _[Symbol.iterator](){}。如果我们想要返回数担['Lydia Halli', 21] :yield_ Object.values(this),这个 geneator 函数一定要 yield 对象 person 的 Object.values

</details>

<b><details><summary>3.(单选题)下面代码的输出是什么 </summary></b>

```js
const set = new Set();

set.add(1);
set.add("Lydia");
set.add({ name: "Lydia" });

for (let item of set) {
  console.log(item + 2);
}
```

```
A：3, NaN, NaN
B: 3, 7, NaN
C: 3, Lydia2( [Object object]2
D: "12", Lydia2, [Object object]2
```

答案：C

解析：

“+”运算符不仅用于添加数值，还可以使用它来连接字符
串。每当 JavaScript 引擎发现一个或多个值不是数字时，就会持数字强制为字符串。
第一个是数字 1。1+2 返回数字 3。
但是，第二个是字符串“Lydia”。“Lydia”是一 t 字符串，2 是一数字：2 被强制转换为字符串。“Lydia”和“2”被连接起来，产生字符串“Lydia2”。
{name : "Lydia"}是一个对象。数字和对象都不是字符串，因此将二者都字符串化。每当我们对常规对象进行字符串化时，它就会变成[Object object]。与“2”串联的“[Object object]”成为“[Object object]2”。

</details>

<b><details><summary>4.(单选题)下面代码的输出是什么 </summary></b>

```js
const settings = {
    username: 'lydiahallie',
    level: 19,
    health: 90
}；
const data = JSON.stringify(settings, ['level', 'health']
console.log(data);
```

```
A："{"level":19, "health":90}"
B: "{"username": "lydiahallie"}"
C: "{"level", "health"]"
D: "{"username": "lydiahallie", "level":19, "health":90}"
```

答案：A

解析：

JSON.stringify 的第二个参数是替代者（replacer）.替代者(replacer)可以是个函数或数组，用以控制哪些值如何被转换为字符串。
如果替代者(replacer)是个数组，那么就只有包含在数组中的属性将会被转化为字符串。在本例中，只有名为'level'和'health'的属性被包括进来，'username'则被排除在外。data 就等于 "{"level":19, "health":90}"

而如果替代者(replacer)是个函数，这个函数将被对象的每个属性都调用一遍。函数返回的值会成为这个属性的值，最终体现在转化后的 JSON 字符串中（译者注：Chrome 下，经过实验，如果所有属性均返回同一个值的时候有异
常，会直接将返回值作为结果输出而不会输出 JSON 字符串），而如果返回值为 undefined ,则该属性会被排除在外。

</details>

<b><details><summary>5.(单选题)下面代码的输出是什么 </summary></b>

```js
const name = "Lydia";

console.log(name());
```

```
A：SyntaxError
B: ReferenceError
C: TypeError
D: undefined
```

答案：C

解析：

变量 name 保存字符串的值，该字符串不是函数，因此无
法调用。

当值不是预期类型时，到抛出 TypeErrors。JavaScript 期望 name 是一个函数，因为我们试图调用它。但它是一个字符串，因此抛出 TypeError : name is not a function

</details>

<b><details><summary>6.(单选题)下面代码的输出是什么 </summary></b>

```js
console.log("🐭" + "🐍");
```

```
A：🐭🐍
B:257548
C:A string containing their code points
D:Error
```

答案：A

解析：

使用+运算符，您可以连接字符串。上述情况，我们将字符串"🐭" 与 字 符 串 "🐍"连 接 起 来 ， 产 生 🐭🐍

</details>

<b><details><summary>7.(单选题)下面代码的输出是什么 </summary></b>

```js
let newList = [1, 2, 3].push(4);

console.log(newList.push(5));
```

```
A：[1,2,3,4,5]
B: [1,2,3,5]
C: [1,2,3,4]
D: Error
```

答案：D

解析：

.push()方法返回数组的长度，而不是数组的本身。

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
A：Lydia
B: Sarah
C: undefined
D: ReferenceError
```

答案：D

解析：

每个函数都有其自己的执行上下文。getName 函数首先在其自身的上下文（范围）内查找，以查看其是否包含我们尝试访问的变量 name。上述情况，getName
函数包含其自己的 name 变量：我们用 let 关键字和 Sarah 的值声明变量 name。

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

</details>

<b><details><summary>9.(单选题)下面代码的输出是什么 </summary></b>

```js
function getAge(...args) { 
  console.log(typeof args);
}
getAge(21);
```

```
A："number"
B: "array"
C: "object"
D: "NaN"
```

答案：C

解析：

扩展运算符（...args )返回一个带参数的数组。 
数组是一个对象，因此typeof args返回object。

</details>

<b><details><summary>10.(单选题)下面代码的输出是什么 </summary></b>

```js
[1, 2, 3, 4].reduce((x, y) => console.log(x,y))
```

```
A：1 2 and 3 3 and 6 4 
B: 1 2 and 2 3 and 3 4
C: 1 undefined and 2 undefined and 3 undefined and 4 undefined
D: 1 2 and undefined 3 and undefined 4 
```

答案：D

解析：

reducer函数接收4个参数：
• Accumulator (acc)(累计器）
• Current Value (cur)(当前值）
• Current Index (idx)(当前索引）
• Source Array (src)(源数组）

reducer 函数的返回值将会分配给累计器，该返回值在数组的每个迭代中被记住，并最后成为最终的单个结果值。

reducer函数还有一个可选参数initialValue ,该参数将作为第一次调用回调函数时的第一个参数的值。如果没有提供initialValue ,则将使用数组中的第一个元素。
在上述例子,reduce方法接收的第一个参数(Accumulator)是 x,第二个参数(Current Value)是 y。
在第一次调用时，累加器x为1 , 当 前 值'y'为 2  , 打印出累加器和当前值：1和2。

例子中我们的回调函数没有返回任何值，只是打印累加器的值和当前值。如果函数没有返回值，则默认返回undefined。在下一次调用时，累加器为undefined ,当前值为'3'，因此undefined和3被打印出。

在第四次调用时，回调函数依然没有返回值。累加器再次为 undefined ,当前值为“4”。undefined 和 4 被打印出

</details>
