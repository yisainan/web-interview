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

</details>

<b><details><summary>3.(单选题)下面代码的输出是什么 </summary></b>

```js
String.prototype.giveLydiaPizza = ( ) = > {  
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

</details>

<b><details><summary>4.(单选题)下面代码的输出是什么 </summary></b>

```js
const { name: myName } = { name:'Lydia'}

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

</details>

<b><details><summary>7.(单选题)下面代码的输出是什么 </summary></b>

```js
```

```
A：
B:
C:
D:
```

答案：

解析：

</details>

<b><details><summary>8.(单选题)下面代码的输出是什么 </summary></b>

```js
```

```
A：
B:
C:
D:
```

答案：

解析：

</details>

<b><details><summary>9.(单选题)下面代码的输出是什么 </summary></b>

```js
```

```
A：
B:
C:
D:
```

答案：

解析：

</details>

<b><details><summary>10.(单选题)下面代码的输出是什么 </summary></b>

```js
```

```
A：
B:
C:
D:
```

答案：

解析：

</details>