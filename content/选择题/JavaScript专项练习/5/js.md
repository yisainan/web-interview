# [返回主页](https://github.com/yisainan/web-interview/blob/master/README.md)

<b><details><summary>1.(单选题)下面代码的输出是什么 </summary></b>

```js
Promise.resolve(5)
@ 5
Promise {<pending>: 5}
Promise {<resolved>: 5}
（D）Error
正确答案：C你的答案：B（错误）
|参考答案
我们可以将我们想要的任何类型的值传递Promise.resol 
ve ,无论是否promise o该方法本身返回带有已解析值 
的Promise。如果您传递常规函数,它将是具有常规值 
的已解决promise。如果你通过了promise ,它将是一个 
已经「esolved的且带有传的值的promise。 @
上述情况，我们传了数字5 ,因此返回一个「esolved状态— 
的promise ,「esolve值为 5
```

```
A: 
B: 
C: 
D: 
```

答案: 

解析：

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
@ 1。
@ 11
undefined
SyntaxError
④ 
```

```
A: 
B: 
C: 
D: 
```

答案: 

解析：

正确答案：D你的答案：C（错误）
|参考答案
在ES2020中，通过#我们可以给class添加私有变量。
在class的外部我们无法获取该值。当我们尝试输出coun
ter.#number ,语法错误被抛出：我们无法在class
分享
ter外部获取它！

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>3.(单选题)下面代码的输出是什么 </summary></b>

```js
const bird = { 
size: ,small'
}；
const mouse = { 
name: 'Mickey', 
small: true
}；
mouse.bird.size
（B）mouse[bird.size]
（C）mouse[bird["sizen]]
All of them are valid
正确答案：A你的答案：D （错误） 
|参考答案 
在JavaScript中，所有对象键都是字符串（除了 Sym席字
1 ）o尽管有时我们可能不会给定字符串类型，但它们总
目5由仕的;*•=依中

在JavaScript中，所有对象键都是字符串（除了 Symbo 
1 ）o尽管有时我们可能不会给定字符串类型，但它们总 
是被转换为字符串。
JavaScript解释语句。当我们使用方括号表示法时，它 
会看到第一个左括号［,然后继续，直到找到右括号］。 
只有在那个时候，它才会对这个语句求值。
mouse [bird, size]:首先它会对 bird.size 求值，得 
到 small。mouse ["small”]返回 true。
但是，使用点表示法，这不会发生。mouse没有名为bir
d的键，这意味着mouse. bird是undefined。然后， 
我们使用点符号来询问size ： mouse.bird.size o由
于mouse.bird是undefined ,我们实际上是在询问und 
efined. size。这是无效的，并将抛出Cannot read 
roperty 'size' of undefined o
```

```
A: 
B: 
C: 
D: 
```

答案: 

解析：

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>4.(单选题)下面代码的输出是什么 </summary></b>

```js
const one = (false || {} || null) 
const two = (null || false || '') 
const three = ([] || 0 || true)
console.log(onetwo, three)
(A)false null 口
null "" true
Q {}""D
(D)null null true
正确答案：C你的答案：B(错误) 
|参考答案
使用II运算符，我们可以返回第一个真值。如果所有值
都是假值，则返回最后一个值。 @
（false || {} || null）：空对象{}是一个真值产享
这是第一个（也是唯一的）真值，它将被返回。one等
```

```
A: 
B: 
C: 
D: 
```

答案: 

解析：

正确答案：C你的答案：B（错误）
|参考答案
使用II运算符，我们可以返回第一个真值。如果所有值 
都是假值，则返回最后一个值。
（false || {} || null）:空对象{}是一个真值。 
这是第一个（也是唯一的）真值，它将被返回。one等 
于{} O
（null || false | |“"）：所有值都是假值。这意味 
着返回传递的值‘二two等于一。
（［］II 0 II"）:空教组［］是一个真值。这是第S 
分字 
个返回的真值。three等于［］。

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>5.(单选题)下面代码的输出是什么 </summary></b>

```js
function sumValues(x, y, z) { 
return x + y + z;
)
(A)sumValues([...l, 2, 3])
@ sumValues([...[l, 2, 3]])
sumValues(...[l, 2, 3])
(D)sumValues([l, 2, 3])
正 确 答 案 ： C 你 的 答 案 ： C ( 正 确 ) 
|参考答案 
通过展开操作符.一，我们可以暂开单个可迭代的元 
素。函数sumValues function接收三个参数:x , y和 
[1, 2, 3]的执行结果为1, 2, 3，将会传递给函数： 
mValues。
z <
```

```
A: 
B: 
C: 
D: 
```

答案: 

解析：

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>1.(单选题)下面代码的输出是什么 </summary></b>

```js

```

```
A: 
B: 
C: 
D: 
```

答案: 

解析：

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>1.(单选题)下面代码的输出是什么 </summary></b>

```js

```

```
A: 
B: 
C: 
D: 
```

答案: 

解析：

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>1.(单选题)下面代码的输出是什么 </summary></b>

```js

```

```
A: 
B: 
C: 
D: 
```

答案: 

解析：

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>1.(单选题)下面代码的输出是什么 </summary></b>

```js

```

```
A: 
B: 
C: 
D: 
```

答案: 

解析：

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>1.(单选题)下面代码的输出是什么 </summary></b>

```js

```

```
A: 
B: 
C: 
D: 
```

答案: 

解析：

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>
