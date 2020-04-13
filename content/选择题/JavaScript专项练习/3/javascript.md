# [返回主页](https://github.com/yisainan/web-interview/blob/master/README.md)

<b><details><summary>1.(单选题)下面代码的输出是什么 </summary></b>

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

答案：B

解析：

请注意, diameter 是普通函数,而 perimeter 是箭头函数。对于箭头函数,this 关键字指向是它所在上下文(定义时的位置)的环境,与普通函数不同!这意味着当我们调用 perimeter 时,它不是指向 shape 对象,而是指其定义时的环境
( window)。没有值 radius 属性,返回 undefined。

[参与互动](https://github.com/yisainan/web-interview/issues/543)

</details>

<b><details><summary>2.(单选题)下面代码的输出是什么 </summary></b>

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

答案：C

解析：

函数 addHobby 接受两个参数，hobby 和有看对象 person 中数组 hobbies 默认值的 hobbies。

首先，我们调用函数 addHobby ,并给 hobby 传递'running'以及 hobbies 传递一个空数组。因为我们给 hobbies 传递了空数组，'running' 被 添加到这个空数组。

然后，我们调用函数 addHobby ,并给 hobby 传递'dancing'。我们不向 hobbies 传递值，因此它获取其默认值---对象 person 的属性 hobbies。我们向数组 person.hobbies push dancing

最后，我们调用函数 addHobby ,并向 hobby 传递值'baking'，并且向 hobbies 传递 person.hobbies。我们向数组 person.hobbies push dancing。

pushing dancing 和 baking 之后，person.hobbies 的值为['coding','dancing’，'baking']

[参与互动](https://github.com/yisainan/web-interview/issues/543)

</details>

<b><details><summary>3.(单选题)下面代码的输出是什么 </summary></b>

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
D: 0 1 2 3 and {0:'a',1:'b',2:'c',3:'d'}
```

答案：A

解析：

通过 for-in 循环，我们可以遍历一个对象自有的、继承的、可枚举的、非 symbol 的属性。在数组中，可枚举属性是数组元素的键，即它们的索引。类似于下面的这个对象：

```js
{0:'a',1:'b',2:'c',3:'d'}
```

其中键则是可枚举属性，因此 0,1,2,3 被记录。通过 for-of 循环，我们可以迭代可迭代对象（包括 Array，Map，Set，String，arguments 等）。当我们迭代数组时，在每次迭代中，不同属性的值将被分配给变量 item，因此'a' 'b' 'c' 'd'被打印

</details>

<b><details><summary>4.(单选题)下面代码的输出是什么 </summary></b>

```js
const myFunc = ({ x, y, z }) => {
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

答案：D

解析：

myFunc 期望接收一个包含 x，y 和 z 属性的对象作为它的参数，因为我们仅仅传递三个单独的数字值（1,2,3）不是一个含有 x，y 和 z 属性的对象({x:1,y:2,z:3}),x,y 和 z 有着各自的默认值 undefined

</details>

<b><details><summary>5.(单选题)输出什么 </summary></b>

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

答案：D

解析：

在 JavaScript 中，我们有两种访问对象属性的方法：括号表示法或点表示法。在此示例中，我们使用点表示法(colorConfig.colors) 代替括号表示法(colorConfig["colors"]) 。

使用点表示法，JavaScript 会尝试使用该确切名称在对象 上查找属性。在此示例中，JavaScript 尝试在 colorconfig 对象上找到名为 colors 的属性。没有名为"colors"的属性，因此返回"undefined"。然后，我们尝试使用[1]访问第一个元 素 的 值 。 我 们 无 法 对 未 定 义 的 值执 行 此 操 作 ， 因此会抛出 Cannot read property '1' of undefined。JavaScript 解释（或取消装箱）语句。当我们使用方括号表示法时，它会看到第一个左方括号[并一直进行下去， 直到找到右方括号]。只有这样，它才会评估该语句。
如果我们使用了 colorConfig [colors [1]],它将返回 colorConfig 对象上 red 属性的值。

</details>

<b><details><summary>6.(单选题)输出什么 </summary></b>

```js
const food = ["A", "B", "C", "D"];
const info = { favoriteFood: food[0] };
info.favoriteFood = "E";
console.log(food);
```

```
A：['A','B','C','D']
B: ['E','B','C','D']
C: ['E', 'A', 'B','C','D']
D: ReferenceError
```

答案：A

解析：

我们将 info 对象上的 favoriteFood 属性的值设置为"E"。字符串是原始数据类型。在 javaScript 中，原始数据类型通过值起作用。在这种情况下.我们将 info 对象上的 favoriteFood 属性

性的值设置为等于 food 数组中的第一个元素的值，"A"。字符串是原始数据类型， 并且通过值进行交互，我们更改 info 对象上 favoriteFood 属性的值。food 数组没有改变，因为 favoriteFood 的值只是该数组中第一个元素的值的复制，并且与该元素上的元素没有相同的内存引用 food[0]。当我们记录 food 时，它仍然是原始数组['A','B','C','D']

</details>

<b><details><summary>7.(单选题)输出什么 </summary></b>

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

答案：D

解析：

通过 const 关键字声明的变量在被初始化之前不可被引用：这被称之为暂时性死区。在函数 getlnfo 中，变量 randomValue 声明在 getlnfo 的作用域的词法环境中。
在想要对 typeof randomValue 进行 log 之前，变量 randomValue 仍未被初始化：错误 ReferenceError 被抛出! JS 引擎并不会根据作用域链网上寻找该变量，因为我们已经在 getlnfo 函数中声明了randomValue 变量。

</details>

<b><details><summary>8.(单选题)以下哪—项会对对象 person有副作用？</summary></b>

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

答案：C

解析：

便用方法Object.freeze对一个对象进行冻结。不能对属性进行添加，修改，删除。然而，它仅对对象进行浅冻结，意味着只有对象中的直接属性被冻结。如果属性是另一个object,像案例中的address, address中的属性没有被冻结，仍然可以被修改。

</details>

<b><details><summary>9.(单选题)输出什么？</summary></b>

```js

```

```
A：person.name = "Evan Bacon" 
B: delete person.address
C: person.address.street = "101 Main St" 
D: person.pet = { name: "Mara"}
```


</details>