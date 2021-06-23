# [返回主页](https://github.com/yisainan/web-interview/blob/master/README.md)

<b><details><summary>1.(单选题)下面代码的输出是什么 </summary></b>

```js
function Person(firstName, lastName) {
    this.firstName = firstName;
    this.lastName = lastName;
}
const member = new Person("Lydia', 'Hallie");
Person.getFullName = () => this.firstName + this.lastName；
console.log(member.getFullName());
TypeError（ B） SyntaxError（ C） Lydia Hallie
undefined undefined
正确答案： A你的答案： D（ 错误）
    |
    参考答案©
分享
您不能像使用常规对象月蹄向构造函数添加属性。 如果要
一次向所有对象添加功能， 则必须使用原型。 所以在这种
    ``
`
```

A：
B:
C:
D:

（C）Lydia Hallie
undefined undefined
正确答案：A你的答案：D （错误）
|参考答案
您不能像使用常规对象月睢向构造函数添加属性。如果要 
一次向所有对象添加功能，则必须使用原型。所以在这种 
情况下应该这样写：
Person.prototype.getFullName = function () { 
return '${this.firstName} ${this.lastName}'; 
}
这样会使member.getFullName。是可用的，为什么样 
做是对的？假设我们将此方法添加到构造函数本身。也 
许不是每个Person实例都需要这种方法。这会浪费大量 
内存空间，因为它们仍然具有该属性，这占用了每个实 
的内存空间。相反，如果我们只将它添加到原型中, 暇 
只需将它放在内存中的一个位置，但它们都可以访问它！ '
``
`
答案：

解析：

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>2.(单选题)下面代码的输出是什么 </summary></b>

```js
2 / 10（ 单选题） 输出什么 ?
    const person = {
        name: 'Lydia", 
        age: 21
    }
let city = person.city
city = 'Amsterdam"
console.log(person) {
    name: "Lydia",
    age: 21
}（
B） {
    name: "Lydia",
    age: 21,
    city: "Amsterdam"
}（
C） {
    name: "Lydia",
    age: 21,
    city: undefined
}（
D） "Amsterdam"
正确答案： A你的答案： A（ 正确）
    |
    参考答案©
分享
我们将变量city设置为等于person对象上名为city的
属性的值。 这个对象上没有名为city的属性， 因此变量
city 的值为 undefined。
请注意， 我们没有引用person对象本身， 只是将变量ci
ty设置为等于person对象上city属性的当前值。
然后， 我们将city设置为等于字符串“ Amsterdam”。
这不会更改person对象： 没有对该对象的引用。 @
分享
因此打印person对象时， 会返回未修改的对象。
    ``
`
```

A：
B:
C:
D:
``
`
答案：

解析：

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>3.(单选题)下面代码的输出是什么 </summary></b>

```js
``
`
```

A：
B:
C:
D:
``
`
答案：

解析：

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>4.(单选题)下面代码的输出是什么 </summary></b>

```js
``
`
```

A：
B:
C:
D:
``
`
答案：

解析：

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>5.(单选题)下面代码的输出是什么 </summary></b>

```js
``
`
```

A：
B:
C:
D:
``
`
答案：

解析：

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>6.(单选题)下面代码的输出是什么 </summary></b>

```js
``
`
```

A：
B:
C:
D:
``
`
答案：

解析：

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>7.(单选题)下面代码的输出是什么 </summary></b>

```js
``
`
```

A：
B:
C:
D:
``
`
答案：

解析：

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>8.(单选题)下面代码的输出是什么 </summary></b>

```js
``
`
```

A：
B:
C:
D:
``
`
答案：

解析：

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>9.(单选题)下面代码的输出是什么 </summary></b>

```js
``
`
```

A：
B:
C:
D:
``
`
答案：

解析：

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>10.(单选题)下面代码的输出是什么 </summary></b>

```js
``
`
```

A：
B:
C:
D:
``
`
答案：

解析：

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>
