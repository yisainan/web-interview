# [返回主页](https://github.com/yisainan/web-interview/blob/master/README.md)

<b><details><summary>1.原型链面试题</summary></b>

答案：

```js
// 1
function A() {}
function B() {}
B.prototype = new A();
var a = new A();
B.prototype = a;
var b = new B();
console.log(b.constructor); // 构造函数A

//2

console.log(Function.constructor === Function);
// Function 是一个构造函数
console.log(Function.__proto__.constructor === Function);

// 默认原型上面的constructor属性指向了原型所在的构造函数。

console.log(Object.constructor === Function);
// Object本身没有constructor这个属性，那么就到它的原型链上去查找，
Object.__proto__ === Function.prototype;

console.log(Function.__proto__.__proto__ === Object.prototype);
Function.__proto__ === Function.prototype;
Function.prototype.__proto__ === Object.prototype;
```

</details>

<b><details><summary>2.原型链面试题</summary></b>

答案：

```js
var o = new Object();
function foo(obj) {
  obj.name = "腐女";
  obj = new Object();
  obj.name = "屌丝"; //这是另一个新对象的name
}
foo(o);
console.log(o.name); //想要的是原来对象的name，所以输出腐女
```

</details>
