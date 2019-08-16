# [返回主页](https://github.com/yisainan/web-interview/blob/master/README.md)

<b><details><summary>1.你如何获取浏览器 URL 中查询字符串中的参数？</summary></b>

答案：

方法一：(基础版)

```js
function getQueryString() {
  var sHref = window.location.href;
  var args = sHref.split("?");
  if (args[0] == sHref) {
    // 没有参数，直接返回空即可
    return "";
  }
  var arr = args[1].split("&");
  var obj = {};
  for (var i = 0; i < arr.length; i++) {
    var arg = arr[i].split("=");
    obj[arg[0]] = arg[1];
  }
  return obj;
}
var href = getQueryString();
console.log(href["categoryId"]);
```

方法二：(正则版,URL 存在#则不适用)

```js
function getQueryString(name) {
  var reg = new RegExp("(^|&)" + name + "=([^&]*)(&|$)");
  var r = window.location.search.substr(1).match(reg);
  if (r != null) return unescape(r[2]);
  return null;
}
console.log(getQueryString("categoryId"));
```

方法三：(正则升级版)

```js
function getQueryString(name) {
  // 未传参，返回空
  if (!name) return null;
  // 查询参数：先通过search取值，如果取不到就通过hash来取
  var after = window.location.search;
  after = after.substr(1) || window.location.hash.split("?")[1];
  // 地址栏URL没有查询参数，返回空
  if (!after) return null;
  // 如果查询参数中没有"name"，返回空
  if (after.indexOf(name) === -1) return null;
  var reg = new RegExp("(^|&)" + name + "=([^&]*)(&|$)");
  // 当地址栏参数存在中文时，需要解码，不然会乱码
  var r = decodeURI(after).match(reg);
  // 如果url中"name"没有值，返回空
  if (!r) return null;
  return r[2];
}
console.log(getQueryString("categoryId"));
```

</details>

<b><details><summary>2.js 实现一个打点计时器</summary></b>

答案：

问题描述：

1、从 start 到 end（包含 start 和 end），每隔 100 毫秒 console.log 一个数字，每次数字增幅 1
2、返回的对象中需要包含一个 cancel 方法，用于停止定时操作
3、第一个数需要立即输出

```js
// 实现法一（setTimeout()方法）：

function count(start, end) {
  if (start <= end) {
    console.log(start++);
    st = setTimeout(function() {
      count(start, end);
    }, 100);
  }
  return {
    cancel: function() {
      clearTimeout(st);
    }
  };
}
count(1, 10);

// 实现法二（setInterval()方法）：

function count(start, end) {
  console.log(start++);
  var timer = setInterval(function() {
    if (start <= end) {
      console.log(start++);
    }
  }, 100);
  return {
    cancel: function() {
      clearInterval(timer);
    }
  };
}
count(1, 10);
```

知识点：
setTimeout()方法用于在指定的毫秒数后调用函数或计算表达式。
语法：setTimeout(code, millisec)
注意：setTimeout() 只执行 code 一次。如果要多次调用，请使用 setInterval() 或者让 code 自身再次调用 setTimeout()。

setInterval() 方法可按照指定的周期（以毫秒计）来调用函数或计算表达式。
语法：setInterval(code ,millisec[,"lang"])
setInterval() 方法会不停地调用函数，直到 clearInterval() 被调用或窗口被关闭。由 setInterval() 返回的 ID 值可用作 clearInterval() 方法的参数。

</details>

<b><details><summary>3.用 js 实现一个标准的排序算法</summary></b>

答案：

一.冒泡排序

```js
function BubbleSort(array) {
  var length = array.length;
  for (var i = length - 1; i > 0; i--) {
    //用于缩小范围
    for (var j = 0; j < i; j++) {
      //在范围内进行冒泡，在此范围内最大的一个将冒到最后面
      if (array[j] > array[j + 1]) {
        var temp = array[j];
        array[j] = array[j + 1];
        array[j + 1] = temp;
      }
    }
    console.log(array);
    console.log("-----------------------------");
  }
  return array;
}

var arr = [10, 9, 8, 7, 7, 6, 5, 11, 3];
var result = BubbleSort(arr);
console.log(result);
/*
[ 9, 8, 7, 7, 6, 5, 10, 3, 11 ]
-----------------------------
[ 8, 7, 7, 6, 5, 9, 3, 10, 11 ]
-----------------------------
[ 7, 7, 6, 5, 8, 3, 9, 10, 11 ]
-----------------------------
[ 7, 6, 5, 7, 3, 8, 9, 10, 11 ]
-----------------------------
[ 6, 5, 7, 3, 7, 8, 9, 10, 11 ]
-----------------------------
[ 5, 6, 3, 7, 7, 8, 9, 10, 11 ]
-----------------------------
[ 5, 3, 6, 7, 7, 8, 9, 10, 11 ]
-----------------------------
[ 3, 5, 6, 7, 7, 8, 9, 10, 11 ]
-----------------------------
[ 3, 5, 6, 7, 7, 8, 9, 10, 11 ]
*/
```

二.选择排序

```js
function SelectionSort(array) {
  var length = array.length;
  for (var i = 0; i < length; i++) {
    //缩小选择的范围
    var min = array[i]; //假定范围内第一个为最小值
    var index = i; //记录最小值的下标
    for (var j = i + 1; j < length; j++) {
      //在范围内选取最小值
      if (array[j] < min) {
        min = array[j];
        index = j;
      }
    }
    if (index != i) {
      //把范围内最小值交换到范围内第一个
      var temp = array[i];
      array[i] = array[index];
      array[index] = temp;
    }
    console.log(array);
    console.log("---------------------");
  }
  return array;
}

var arr = [1, 10, 100, 90, 65, 5, 4, 10, 2, 4];
var result = SelectionSort(arr);
console.log(result);
/*
[ 1, 10, 100, 90, 65, 5, 4, 10, 2, 4 ]
---------------------
[ 1, 2, 100, 90, 65, 5, 4, 10, 10, 4 ]
---------------------
[ 1, 2, 4, 90, 65, 5, 100, 10, 10, 4 ]
---------------------
[ 1, 2, 4, 4, 65, 5, 100, 10, 10, 90 ]
---------------------
[ 1, 2, 4, 4, 5, 65, 100, 10, 10, 90 ]
---------------------
[ 1, 2, 4, 4, 5, 10, 100, 65, 10, 90 ]
---------------------
[ 1, 2, 4, 4, 5, 10, 10, 65, 100, 90 ]
---------------------
[ 1, 2, 4, 4, 5, 10, 10, 65, 100, 90 ]
---------------------
[ 1, 2, 4, 4, 5, 10, 10, 65, 90, 100 ]
---------------------
[ 1, 2, 4, 4, 5, 10, 10, 65, 90, 100 ]
---------------------
[ 1, 2, 4, 4, 5, 10, 10, 65, 90, 100 ]
*/
```

三.插入排序

```js
function InsertionSort(array) {
  var length = array.length;
  for (var i = 0; i < length - 1; i++) {
    //i代表已经排序好的序列最后一项下标
    var insert = array[i + 1];
    var index = i + 1; //记录要被插入的下标
    for (var j = i; j >= 0; j--) {
      if (insert < array[j]) {
        //要插入的项比它小，往后移动
        array[j + 1] = array[j];
        index = j;
      }
    }
    array[index] = insert;
    console.log(array);
    console.log("-----------------------");
  }
  return array;
}

var arr = [100, 90, 80, 62, 80, 8, 1, 2, 39];
var result = InsertionSort(arr);
console.log(result);
/*
[ 90, 100, 80, 62, 80, 8, 1, 2, 39 ]
-----------------------
[ 80, 90, 100, 62, 80, 8, 1, 2, 39 ]
-----------------------
[ 62, 80, 90, 100, 80, 8, 1, 2, 39 ]
-----------------------
[ 62, 80, 80, 90, 100, 8, 1, 2, 39 ]
-----------------------
[ 8, 62, 80, 80, 90, 100, 1, 2, 39 ]
-----------------------
[ 1, 8, 62, 80, 80, 90, 100, 2, 39 ]
-----------------------
[ 1, 2, 8, 62, 80, 80, 90, 100, 39 ]
-----------------------
[ 1, 2, 8, 39, 62, 80, 80, 90, 100 ]
-----------------------
[ 1, 2, 8, 39, 62, 80, 80, 90, 100 ]
*/
```

四.希尔排序
五.归并排序
六.快速排序

</details>

<b><details><summary>4. 正则表达式，验证手机号码，验证规则：11 位数字，以 1 位开头</summary></b>

答案：

```js
checkphonenumber(number) {
	if (number == null || number.length != 11) {
		return false
	} else {
		// 移动号段正则表达式
		var pat1 = '^((13[4-9])|(147)|(15[0-2,7-9])|(178)|(18[2-4,7-8]))\\d{8}|(1705)\\d{7}$';
		// 联通号段正则表达式
		var pat2 = '^((13[0-2])|(145)|(15[5-6])|(176)|(18[5,6]))\\d{8}|(1709)\\d{7}$';
		// 电信号段正则表达式
		var pat3 = '^((133)|(153)|(177)|(18[0,1,9])|(149))\\d{8}$';
		// 虚拟运营商正则表达式
		var pat4 = '^((170))\\d{8}|(1718)|(1719)\\d{7}$';
		if (!part1.test(number)) {
			return false
		}
		if (!part2.test(number)) {
			return false
		}
		if (!part3.test(number)) {
			return false
		}
		if (!part4.test(number)) {
			return false
		}
	}
	return true
}
```

</details>

<b><details><summary>5. 请给 Array 本地对象增加一个原型方法，他的用途是删除数组中重复的条目并按升序排序，最后返回新数组。</summary></b>

答案：

```js
Array.prototype.distinct = function() {
  var ret = [];
  for (var i = 0; i < this.length; i++) {
    for (var j = i + 1; j < this.length; ) {
      if (this[i] === this[j]) {
        ret.push(this.splice(j, 1)[0]);
      } else {
        j++;
      }
    }
  }
  return ret;
};
console.log(["a", "b", "c", "d", "b", "a", "e"].distinct()); // ["a", "b"]
```

</details>

<b><details><summary>6. 为字符串扩展一个 rewrite 函数，接收一个正则 pattern 和一个字符串 result,如果该字符串符合 pattern， 则以 result 对结果进行转义输出。 如</summary></b>

答案：

```js
"/foo".rewrite(/^\/foo/, "/bar");
"u1234".rewrite(/^\/u(\d+)/, "/user/$1");
"/i".rewrite(/^\o/, "/ooo");
```

</details>

<b><details><summary>7. 实现一个 js 对象序列化函数，将 js 对象序列化为可反序列化的代码，要求 1.尽量和 json 兼容，2.支持不可序列化的值，如 undefined/NaN/Infinify-Infinity，3. 支持特殊对象，如正则、Date 等</summary></b>

答案：

```js
serialize({});
serialize({ a: "b" });
serialize({ a: 0 / 0 });
serialize({ a: /foo/ });
```

</details>

<b><details><summary>8. 设计一道 JavaScript 的 range 算法如下：</summary></b>

答案：

range(1, 10, 3) 返回 [1, 4, 7, 10];
range('A', 'F', 2) 返回 ['A', 'C', 'E']
// 请使用 JavaScript 语言实现该功能（可以使用 ES6）

</details>

<b><details><summary>9. 头条的视频网站上支持了弹幕，假设一个视频有很多弹幕，弹幕的数据是一个数组，格式定义如下：</summary></b>

答案：

```

[
    {
        time: Number,
        content: String
    },
    {
        time: Number,
        content: String
    }...
]
(其中 time 表示时间，content表示弹幕内容)，那么如何快速定位到某个时间点的弹幕，请编码实现（不使用数组的 sort 方法）

```

</details>

<b><details><summary>10. 请写出以下代码的执行结果</summary></b>

答案：

```
(function() {
    fn();
    var fn = function() {
        alert(1);
    }
    fn();
    function fn() {
        alert(2)
    }
})()
```

</details>

<b><details><summary>11. 请说明以下各种情况的执行结果，并注明产生对应结果的理由</summary></b>

答案：

```
function doSomething() {
    alert(this);
}

a) element.onclick = doSomething, 点击 element 元素后
b) element.onclick = function() doSomething(){}, 点击 element 元素后
c) 直接执行 doSomething()
```

</details>

<b><details><summary>12. 请写出以下代码的执行结果</summary></b>

答案：

```
var obj = {};
var events = { m1: "clicked", m2: "changed"};
for(e in events) {
    obj[e] = function() {
        alert(events[e])
    }
}

alert(obj.m1 == obj.m2);
obj.m1();
obj.m2();
```

</details>

<b><details><summary>13. 请写出类 Son 继承类 Father</summary></b>

答案：
function Father() {}
function Son() {}

</details>

<b><details><summary>14. 请用 JS 写出一个遍历 DOM 节点树的方法</summary></b>

答案：

</details>

<b><details><summary>15. 尝试实现注释部分的 JavaScript 代码， 可在其他任何地方添加更多代码。</summary></b>

答案：

```
var Obj = function(msg) {
    this.msg = msg;
    this.shout = function () {
        alert(this.msg)
    }
    this.waitAndShout = function() {
        // 隔五秒钟后执行上面的 shout 方法
    }
}
```

</details>

<b><details><summary>16. 请编写一个 JavaScript 函数 parseQuerySting, 它的用途是把 URL 参数解析为一个对象，如</summary></b>

答案：

```
var url = "http://www.58.com/index.aspx?key0=0&key1=1&key2=2..."
var obj = parseQuerySting(url);
alert(obj.key0) // 输出 0
```

</details>

<b><details><summary>17. 请给 Array 本地对象添加一个原型方法，它用于删除数组条目中重复的条目（可能有多个重复），返回值是一个包含被删除的重复条目的新数组</summary></b>

答案：

</details>

<b><details><summary>18. 我们把一个数字倒着读和原数字相同的数字称之为对称数，例如（1, 121, 88, 8998）,不考虑性能，请找出 1 - 10000 之间的对称数，要求用 JS 实现</summary></b>

答案：

</details>

<b><details><summary>19. 以下代码输出多少</summary></b>

答案：

```js
var name = "world";
(function () {
    if (typeof name === "undefined") {
        var name = "jack";
        console.log("Hi!" + name);
    } else {
        console.log("Hello," + name)
    }
})()

==> Hi!jack

var name = "world";
(function (name) {
    if (typeof name === "undefined") {
        var name = "jack";
        console.log("Hi!" + name);
    } else {
        console.log("Hello," + name)
    }
})(name)

==> Hello,world
```

</details>

<b><details><summary>10. 数组拍平</summary></b>

答案：

</details>

<b><details><summary>21.如何解决数组塌陷问题</summary></b>

答案：

```js
// 1 使用i--
for (var i = 0; i < arr.length; i++) {
  if (arr[i] === 4) {
    arr.splice(i, 1);
    i--;
  }
}
console.log(arr);

// 2 从数组的末尾一项开始遍历
for (var i = arr.length; i >= 0; i--) {
  if (arr[i] === 4) {
    arr.splice(i, 1);
  }
}
console.log(arr);
```

</details>

<b><details><summary>22.计算打印结果</summary></b>

答案：

```js
function fun(n, o) {
  console.log(o);
  return {
    fun: function(m) {
      return fun(m, n);
    }
  };
}
//    var a = fun(0);
//    a.fun(1)
//    a.fun(2)
//    a.fun(3)

// 打印
// undefined 0 0 0

//    var b = fun(0).fun(1).fun(2).fun(3)
// 打印 undefined 0 1 2

var c = fun(0).fun(1);
c.fun(2);
c.fun(3);
// 打印
// undefined 0 1 1
```

</details>

<b><details><summary>23.编写一个数组去重的方法</summary></b>

答案：

</details>

<b><details><summary>24.已知 id 的 input 输入框，希望获取这个输入框的输入值，怎么做？（不使用第三方框架）</summary></b>

答案：

```js
document.getElementById("id").value;
```

</details>

<b><details><summary>25.获取到页面中所有的 checkbox 怎么做？（不使用第三方框架）</summary></b>

答案：

```js
var domList = document.getElementsByTagName("input");
var ckList = []; // 返回的所有的 checkbox
var len = domList.length;
for (var i = 0; i < len; i++) {
  if (domList[i].type == "checkbox") {
    ckList.push(domList[i]);
  }
}
```

</details>

<b><details><summary>26.设置一个已知 id 的 div 的 html 内容为 xxxx，字体颜色设置为黑色（不使用第三方框架）</summary></b>

答案：

```js
var dom = document.getElementById("id");
dom.innerHTML = "xxxx";
dom.style.color = "#000"; // 'black'
```

</details>

<b><details><summary>27.判断相等</summary></b>

答案：

2 == true
[] == false
[] == ![]

</details>

<b><details><summary>28.已知有字符串 foo=“get-element-by-id”,写一个 function 将其转化为驼峰表示法“getElementById”</summary></b>

答案：

```js
var string = "get-element-by-id";

function combo(msg) {
  var arr = msg.split("-"); //split("-")以-为分隔符截取字符串，返回数组
  for (var i = 1; i < arr.length; i++) {
    arr[i] = arr[i].charAt(0).toUpperCase() + arr[i].slice(1);
  }
  msg = arr.join(""); //join()返回字符串
  return msg;
}
console.log(combo(string));
```

</details>

<b><details><summary>29.看下面代码，给出输出结果</summary></b>

```js
for (var i = 1; i <= 3; i++) {
  console.log(i);
}
// 1 2 3
```

但是

```js
for (var i = 1; i <= 3; i++) {
  setTimeout(() => {
    // setTimout在for里面是异步执行的，在延迟输出的时候，i的值已经是4了
    console.log(i);
  }, 0);
}
// 4 4 4
```

如何输出 1 2 3

答案：

立即执行函数

```js
for (var i = 1; i <= 3; i++) {
  setTimeout(
    (i => {
      console.log(i);
    })(i),
    0
  );
}
```

闭包

```js
for (var i = 1; i <= 3; i++) {
  setTimeout(
    (() => {
      var j = i;
      return function() {
        console.log(j);
      };
    })(),
    0
  );
}
```

</details>

<b><details><summary>30. JS 字符串使用堆栈处理 "(a,b,(c,d),f,g)"</summary></b>

答案：

</details>

<b><details><summary>31. 二维数组操作</summary></b>

答案：

</details>

<b><details><summary>32. 用最简单的方式，求一个数组中最大的元素，例如 arr=[5,7,9,42,18,29]</summary></b>

答案：

```js
var a = [1, 2, 3, 5];
alert(Math.max.apply(null, a)); //最大值
alert(Math.min.apply(null, a)); //最小值
```

</details>

<b><details><summary>33.写一个 function，清除字符串前后的空格（兼容所有的浏览器）</summary></b>

答案：

```js
//重写trim方法
if (!String.prototype.trim) {
  String.prototype.trim = function() {
    return this.replace(/^\s+/, "").replace(/\s+$/, "");
  };
}
```

</details>

<b><details><summary>34.运算符面试题</summary></b>

答案：

```js
var a = 10,
  b = 20,
  c = 30;
++a;
a++;
e = ++a + ++b + c++ + a++;
console.log(e); // 77
```

</details>

<b><details><summary>35.this 面试题</summary></b>

答案：

```
 this指向了谁？
 看函数在执行的时候是如何调用的，
 1 如果这个函数是用普通函数调用模式来进行调用，它内部的this指向了window
 2如果一个函数在调用的时候是通过对象方法模式来进行调用，则它内部的this就是我们的对象
 3 如果一个函数在调用的时候通过构造函数模式调用，则它内部的this指向了生成的实例
 4 如果这个函数是通过方法借用模式调用，则这个函数内部的this就是我们手动指定this。
```

```js
//第1题
function Fn() {
  console.log(this);
}
Fn(); //window 普通函数调用模式
new Fn(); //{}  构造函数调用模式
Fn.apply(Fn); // Fn的函数体   方法借用模式

//第2题
var o = {
  f: function() {
    console.log(this);
  },
  2: function() {
    console.log(this);
    console.log(this.__proto__ === o[2].prototype);
  }
};
o.f(); //o   对象调用模式
o[2](); //o  对象调用模式
new o[2](); //存疑，存在着优先级的问题 {}  通过构造函数模式进行调用
o.f.call([1, 2]); //[1,2]   call方法进行方法借用。
o[2].call([1, 2, 3, 4]); // [1,2,3,4]  call方法进行方法借用

//第3题
var name = "out";
var obj = {
  name: "in",
  prop: {
    name: "inside",
    getName: function() {
      return this.name;
    }
  }
};

console.log(obj.prop.getName()); //对象调用模式来进行调用  obj.prop.name  'inside'
var test = obj.prop.getName; // 把test这个变量指向了obj.prop.getName所在的内存地址。
console.log(test()); //普通函数模式来进行调用  window 'out'
console.log(obj.prop.getName.apply(window)); //方法借用模式  'out'
console.log(obj.prop.getName.apply(this)); //方法借用模式  'out'
console.log(this === window); //true

//第4题
var length = 10;
function fn() {
  console.log(this.length);
}
var obj = {
  length: 5,
  method: function(f) {
    console.log(this);
    f(); // f在调用的时候是什么调用模式？普通函数调用模式  window.length  10
    arguments[0](); // 通过什么模式来进行调用的。执行之前有[]和.就是对象调用模式。
    //arguments是一个类数组，也就是一个对象，就是通过arguments来进行调用的
    //arguments.length实参的数量。实参长度是1
    //通过arguments对象进行调用，因此函数内部的this是  arguments
    // 如果一个函数在调用的时候它前面有call和apply那么就肯定是方法借用模式调用
    arguments[0].call(this);
    // 调用method方法是通过obj.method 因此在这里的this就是 obj
    //通过call方法把fn内的this指向了obj
    // 输出obj.length  5
  }
};
obj.method(fn);

//第5题
function Foo() {
  getName = function() {
    console.log(1);
  };
  return this;
}
Foo.getName = function() {
  console.log(2);
};
Foo.prototype.getName = function() {
  console.log(3);
};
var getName = function() {
  console.log(4);
};
function getName() {
  console.log(5);
}
//请写出以下输出结果：
Foo.getName(); //2
getName(); //4
Foo().getName(); //1
getName(); //1
new Foo.getName(); //2
new Foo().getName(); //3
new new Foo().getName(); //3
// new Foo()创建了一个构造函数，然后这个函数再去访问getName这个函数，
//对它进行调用
/*console.log(new Foo().getName)*/
/*var o = new new Foo().getName(); //
    console.log(o.__proto__===Foo.prototype.getName.prototype)*/
//用new Foo创建出来了一个实例，然后这个实例去访问 (new Foo().getName)

/*console.log(new new Foo().getName())

    console.log(new Foo().getName())*/

/*function Foo() {
        getName = function () {
            console.log(1);
        };
        return this;
    }
    var getName;
    Foo.getName = function () {
        console.log(2);
    };
    Foo.prototype.getName = function () {
        console.log(3);
    };
    getName = function () {
        console.log(4);
    };
    //请写出以下输出结果：
    Foo.getName();// 2
    getName();//4
/!*    Foo().getName();//!*!/
    window.getName()//1
    getName();//1
  /!*  var o = new Foo.getName();//2
    console.log(o);// {}
    console.log(o.__proto__===Foo.getName.prototype)//true*!/
    new Foo.getName();// 2
    new Foo().getName();//
    new new Foo().getName();*/

//第6题
var obj = {
  fn: function() {
    console.log(this);
  }
};
obj.fn(); //obj
var f = obj.fn;
f(); //window
console.log(f === obj.fn); // true

// f和obj.fn是同一个函数，但是他们在调用的时候使用的函数调用模式不同，因此，它们内部的this指向也就不同。

// #7题
var arr = [
  function() {
    console.log(this);
  }
];
arr[0](); //数组本身
//数组也是一个复杂数据类型，也是一个对象，那用数组去调用函数，使用的模式就是对象方法调用模式。
function f() {
  console.log(this);
}
function fn() {
  console.log(arguments); // 类数组，也是就一个对象    [0:function f(){}]
  console.log(this); // window
  arguments[0]();
  console.log(arguments[0]); //内部的this就是arguments
  // 通过arguments对f这个方法进行调用，使用的是对象方法调用模式。
}
fn(f);

// #8题
function SuperClass() {
  this.name = "women";
  this.bra = ["a", "b"];
}

SuperClass.prototype.sayWhat = function() {
  console.log("hello");
};

function SubClass() {
  this.subname = "you sister";
  SuperClass.call(this);
}

var sub = new SubClass();
console.log(sub.sayWhat());
```

</details>

<b><details><summary>36.实现一个 new 操作符</summary></b>

答案：

```js
function New(func) {
  var res = {};
  if (func.prototype !== null) {
    res.__proto__ = func.prototype;
  }
  var ret = func.apply(res, Array.prototype.slice.call(arguments, 1));
  if ((typeof ret === "object" || typeof ret === "function") && ret !== null) {
    return;
    ret;
  }
  return;
  res;
}
var obj = New(A, 1, 2);
// equals to
var obj = new A(1, 2);
```

</details>

<b><details><summary>37.实现一个 call 或 apply</summary></b>

答案：
call

```js
Function.prototype.call2 = function(context) {
  var context = context || window;
  context.fn = this;

  var args = [];
  for (var i = 1, len = arguments.length; i < len; i++) {
    args.push("arguments[" + i + "]");
  }

  var result = eval("context.fn(" + args + ")");

  delete context.fn;
  return result;
};
```

apply

```js
Function.prototype.apply2 = function(context, arr) {
  var context = Object(context) || window;
  context.fn = this;

  var result;
  if (!arr) {
    result = context.fn();
  } else {
    var args = [];
    for (var i = 0, len = arr.length; i < len; i++) {
      args.push("arr[" + i + "]");
    }
    result = eval("context.fn(" + args + ")");
  }

  delete context.fn;
  return result;
};
```

</details>

<b><details><summary>38.实现一个 Function.bind</summary></b>

答案：

```js
Function.prototype.bind2 = function(context) {
  if (typeof this !== "function") {
    throw new Error(
      "Function.prototype.bind - what is trying to be bound is not callable"
    );
  }
  var self = this;
  var args = Array.prototype.slice.call(arguments, 1);
  var fNOP = function() {};
  var fbound = function() {
    self.apply(
      this instanceof self ? this : context,
      args.concat(Array.prototype.slice.call(arguments))
    );
  };
  fNOP.prototype = this.prototype;
  fbound.prototype = new fNOP();
  return fbound;
};
```

</details>

<b><details><summary>39.实现一个继承</summary></b>

答案：

```js
function Parent(name) {
  this.name = name;
}

Parent.prototype.sayName = function() {
  console.log("parent name:", this.name);
};

function Child(name, parentName) {
  Parent.call(this, parentName);
  this.name = name;
}

function create(proto) {
  function F() {}
  F.prototype = proto;
  return new F();
}
Child.prototype = create(Parent.prototype);
Child.prototype.sayName = function() {
  console.log("child name:", this.name);
};

Child.prototype.constructor = Child;
var parent = new Parent("汪某");
parent.sayName(); // parent name: 汪某
var child = new Child("son", "汪某");
```

</details>

<b><details><summary>40.手写一个 Promise(中高级必考)</summary></b>

答案：

```js
function myPromise(constructor) {
  let self = this;
  self.status = "pending";
  //定义状态改变前的初始状态
  self.value = undefined;
  //定义状态为resolved的时候的状态
  self.reason = undefined;
  //定义状态为rejected的时候的状态
  function resolve(value) {
    //两个==="pending"，保证了状态的改变是不可逆的
    if (self.status === "pending") {
      self.value = value;
      self.status = "resolved";
    }
  }
  function reject(reason) {
    //两个==="pending"，保证了状态的改变是不可逆的
    if (self.status === "pending") {
      self.reason = reason;
      self.status = "rejected";
    }
  }
  //捕获构造异常
  try {
    constructor(resolve, reject);
  } catch (e) {
    reject(e);
  }
}

//同时，需要在 myPromise的原型上定义链式调用的 then方法：
myPromise.prototype.then = function(onFullfilled, onRejected) {
  let self = this;
  switch (self.status) {
    case "resolved":
      onFullfilled(self.value);
      break;
    case "rejected":
      onRejected(self.reason);
      break;
    default:
  }
};

//测试一下：
var p = new myPromise(function(resolve, reject) {
  resolve(1);
});
p.then(function(x) {
  console.log(x);
});
```

</details>

<b><details><summary>41.手写防抖(Debouncing)和节流(Throttling)</summary></b>

答案：

```js
// 防抖函数
function debounce(fn, wait) {
  let timer;
  return function() {
    if (timer) clearTimeout(timer);
    timer = setTimeout(() => {
      fn.apply(this, arguments);
    }, wait);
  };
}
```

```js
// 节流函数
function throttle(fn, wait) {
  let prev = new Date();
  return function() {
    const args = arguments;
    const now = new Date();
    if (now - prev > wait) {
      fn.apply(this, args);
      prev = new Date();
    }
  };
}
```

</details>

<b><details><summary>42.手写一个 JS 深拷贝</summary></b>

答案：

```js
function deepCopy(obj) {
  //判断是否是简单数据类型，
  if (typeof obj == "object") {
    //复杂数据类型
    var result = obj.constructor == Array ? [] : {};
    for (let i in obj) {
      result[i] = typeof obj[i] == "object" ? deepCopy(obj[i]) : obj[i];
    }
  } else {
    //简单数据类型 直接 == 赋值
    var result = obj;
  }
  return result;
}
```

</details>

<b><details><summary>43.看下面代码，给出输出结果(考察闭包及++运算符)</summary></b>

答案：

```js
function Foo() {
  var i = 0;
  return function() {
    console.log(i++);
  };
}
var f1 = Foo(),
  f2 = Foo();

f1(); // 0
f1(); // 1
f2(); // 0
```

```js
function fn() {
  var a = 1;
  return function() {
    a++;
    console.log(a);
  };
}
var b = fn();
console.log(b());
// 2
```

```js
function fn() {
  var a = 1;
  return function() {
    console.log(a++);
  };
}
var b = fn();
console.log(b());
// 1
```

</details>

<b><details><summary>44. 看下面代码，给出输出结果(考察时间戳)</summary></b>

答案：

```js
//总结：第一个setTimeout，时间间隔<1000的话，输出1000多，>1000的话，输出间隔值多
//     第二个setTimeout，是1000+时间间隔
var dateNum = new Date();
setTimeout(function() {
  console.log(new Date() - dateNum);
}, 1200); //1200多
while (new Date() - dateNum < 1000) {
  var a = 1;
}
setTimeout(function() {
  console.log(new Date() - dateNum);
}, 1500); // 2500左右
```

</details>

<b><details><summary>45.编写一个元素拖拽的插件</summary></b>

答案：

</details>

<b><details><summary>46.什么是代理和通知，写一下他们基本的实现方法</summary></b>

答案：

</details>

<b><details><summary>47.看题写结果</summary></b>

```js
var output = function(i) {
  setTimeout(function() {
    console.log(i);
  }, 1000);
};

for (var i = 0; i < 5; i++) {
  output(i); // 这里传过去的 i 值被复制了
}

console.log(i);
```

答案：

5
0
1
2
3
4

解析：[参考](https://www.cnblogs.com/adouwt/p/6481479.html)

</details>

<b><details><summary>48.告诉我答案是多少</summary></b>

```js
(function(x) {
  delete x;
  alert(x);
})(1 + 5);
```

答案：

</details>

<b><details><summary>49.写一个通用的事件侦听器函数</summary></b>

答案：

```js
// event(事件)工具集，来源：https://github.com/markyun
markyun.Event = {
  // 页面加载完成后
  readyEvent: function(fn) {
    if (fn == null) {
      fn = document;
    }
    var oldonload = window.onload;
    if (typeof window.onload != "function") {
      window.onload = fn;
    } else {
      window.onload = function() {
        oldonload();
        fn();
      };
    }
  },
  // 视能力分别使用dom0||dom2||IE方式 来绑定事件
  // 参数： 操作的元素,事件名称 ,事件处理程序
  addEvent: function(element, type, handler) {
    if (element.addEventListener) {
      //事件类型、需要执行的函数、是否捕捉
      element.addEventListener(type, handler, false);
    } else if (element.attachEvent) {
      element.attachEvent("on" + type, function() {
        handler.call(element);
      });
    } else {
      element["on" + type] = handler;
    }
  },
  // 移除事件
  removeEvent: function(element, type, handler) {
    if (element.removeEnentListener) {
      element.removeEnentListener(type, handler, false);
    } else if (element.datachEvent) {
      element.detachEvent("on" + type, handler);
    } else {
      element["on" + type] = null;
    }
  },
  // 阻止事件 (主要是事件冒泡，因为IE不支持事件捕获)
  stopPropagation: function(ev) {
    if (ev.stopPropagation) {
      ev.stopPropagation();
    } else {
      ev.cancelBubble = true;
    }
  },
  // 取消事件的默认行为
  preventDefault: function(event) {
    if (event.preventDefault) {
      event.preventDefault();
    } else {
      event.returnValue = false;
    }
  },
  // 获取事件目标
  getTarget: function(event) {
    return event.target || event.srcElement;
  },
  // 获取event对象的引用，取到事件的所有信息，确保随时能使用event；
  getEvent: function(e) {
    var ev = e || window.event;
    if (!ev) {
      var c = this.getEvent.caller;
      while (c) {
        ev = c.arguments[0];
        if (ev && Event == ev.constructor) {
          break;
        }
        c = c.caller;
      }
    }
    return ev;
  }
};
```

</details>

<b><details><summary>50.谈一下 JS 中的递归函数，并且用递归简单实现阶乘</summary></b>

答案：递归即是程序在执行过程中不断调用自身的编程技巧，当然也必须要有一个明确的结束条件，不然就会陷入死循环。

</details>

<b><details><summary>51.请用正则表达式写一个简单的邮箱验证</summary></b>

答案：

</details>

<b><details><summary>52.完成 foo()函数的内容，要求能够弹出对话框提示当前选中的是第几个单选框</summary></b>

答案：

</details>

<b><details><summary>53.完成函数 showImg()，要求能够动态根据下拉列表的选项变化，更新图片的显示</summary></b>

答案：

</details>

<b><details><summary>54.截取字符串 abcdefg 中的 efg</summary></b>

答案：

</details>

<b><details><summary>55.JSON 的了解</summary></b>

答案：JSON(JavaScript Object Notation) 是一种轻量级的数据交换格式。它是基于 JavaScript 的一个子集。数据格式简单, 易于读写, 占用带宽小

</details>

<b><details><summary>56.判断一个字符串中出现次数最多的字符，统计这个次数</summary></b>

答案：

```js
var str = "asdfssaaasasasasaa";
var json = {};
for (var i = 0; i < str.length; i++) {
  if (!json[str.charAt(i)]) {
    json[str.charAt(i)] = 1;
  } else {
    json[str.charAt(i)]++;
  }
}
var iMax = 0;
var iIndex = "";
for (var i in json) {
  if (json[i] > iMax) {
    iMax = json[i];
    iIndex = i;
  }
}
alert("出现次数最多的是:" + iIndex + "出现" + iMax + "次");
```

</details>

<b><details><summary>57.写一个获取非行间样式的函数</summary></b>

答案：

```js
function getStyle(obj, attr, value) {
  if (!value) {
    if (obj.currentStyle) {
      return obj.currentStyle(attr);
    } else {
      obj.getComputedStyle(attr, false);
    }
  } else {
    obj.style[attr] = value;
  }
}
```

</details>

<b><details><summary>58.字符串反转，如将 '12345678' 变成 '87654321'</summary></b>

答案：

```js
//思路：先将字符串转换为数组 split()，利用数组的反序函数 reverse()颠倒数组，再利用 jion() 转换为字符串
var str = "12345678";
str = str
  .split("")
  .reverse()
  .join("");
```

</details>

<b><details><summary>59.将数字 12345678 转化成 RMB 形式 如： 12,345,678</summary></b>

答案：

```js
//个人方法；
//思路：先将数字转为字符， str= str + '' ;
//利用反转函数，每三位字符加一个 ','最后一位不加； re()是自定义的反转函数，最后再反转回去！
for (var i = 1; i <= re(str).length; i++) {
  tmp += re(str)[i - 1];
  if (i % 3 == 0 && i != re(str).length) {
    tmp += ",";
  }
}
```

</details>

<b><details><summary>60.生成 5 个不同的随机数</summary></b>

答案：

```js
//思路：5个不同的数，每生成一次就和前面的所有数字相比较，如果有相同的，则放弃当前生成的数字！
var num1 = [];
for (var i = 0; i < 5; i++) {
  num1[i] = Math.floor(Math.random() * 10) + 1; //范围是 [1, 10]
  for (var j = 0; j < i; j++) {
    if (num1[i] == num1[j]) {
      i--;
    }
  }
}
```

</details>

<b><details><summary>61.去掉数组中重复的数字</summary></b>

答案：

方法一

```js
//思路：每遍历一次就和之前的所有做比较，不相等则放入新的数组中！
//这里用的原型 个人做法；
Array.prototype.unique = function() {
  var len = this.length,
    newArr = [],
    flag = 1;
  for (var i = 0; i < len; i++, flag = 1) {
    for (var j = 0; j < i; j++) {
      if (this[i] == this[j]) {
        flag = 0; //找到相同的数字后，不执行添加数据
      }
    }
    flag ? newArr.push(this[i]) : "";
  }
  return newArr;
};
```

方法二

```js
(function(arr) {
  var len = arr.length,
    newArr = [],
    flag;
  for (var i = 0; i < len; i += 1, flag = 1) {
    for (var j = 0; j < i; j++) {
      if (arr[i] == arr[j]) {
        flag = 0;
      }
    }
    flag ? newArr.push(arr[i]) : "";
  }
  alert(newArr);
})([1, 1, 22, 3, 4, 55, 66]);
```

</details>

<b><details><summary>62.阶乘函数</summary></b>

答案：

```js
//原型方法
Number.prototype.N = function() {
  var re = 1;
  for (var i = 1; i <= this; i++) {
    re *= i;
  }
  return re;
};
var num = 5;
alert(num.N());
```

</details>

<b><details><summary>63.看题做答</summary></b>

答案：

```js
	function f1(){
    var tmp = 1;
    this.x = 3;
    console.log(tmp);    //A
    console.log(this.x)；     //B
}
var obj = new f1(); //1
console.log(obj.x)     //2
console.log(f1());        //3
```

解析：   
     这道题让我重新认识了对象和函数，首先看代码（1），这里实例话化了 f1 这个类。相当于执行了 f1 函数。所以这个时候 A 会输出 1， 而 B 这个时候的 this 代表的是 实例化的当前对象 obj B 输出 3.。 代码（2）毋庸置疑会输出 3， 重点 代码（3）首先这里将不再是一个类，它只是一个函数。那么 A 输出 1， B 呢？这里的 this 代表的其实就是 window 对象，那么 this.x 就是一个全局变量 相当于在外部 的一个全局变量。所以 B 输出 3。最后代码由于 f 没有返回值那么一个函数如果没返回值的话，将会返回 underfined ，所以答案就是 ： 1， 3， 3， 1， 3， underfined 。

</details>

<b><details><summary>64.下面输出多少？</summary></b>

答案：

```js
var o1 = new Object();
var o2 = o1;
o2.name = "CSSer";
console.log(o1.name);
```

解析：

如果不看答案，你回答真确了的话，那么说明你对 javascript 的数据类型了解的还是比较清楚了。js 中有两种数据类型，分别是：基本数据类型和引用数据类型（object Array）。对于保存基本类型值的变量，变量是按值访问的，因为我们操作的是变量实际保存的值。对于保存引用类型值的变量，变量是按引用访问的，我们操作的是变量值所引用（指向）的对象。答案就清楚了：  //CSSer;

</details>

<b><details><summary>65.下面输出多少？</summary></b>

答案：

```js
function changeObjectProperty(o) {
  o.siteUrl = "http://www.csser.com/";
  o = new Object();
  o.siteUrl = "http://www.popcg.com/";
}
var CSSer = new Object();
changeObjectProperty(CSSer);
console.log(CSSer.siteUrl); //
```

解析：

如果 CSSer 参数是按引用传递的，那么结果应该是"http://www.popcg.com/"，但实际结果却仍是"http://www.csser.com/"。事实是这样的：在函数内部修改了引用类型值的参数，该参数值的原始引用保持不变。我们可以把参数想象成局部变量，当参数被重写时，这个变量引用的就是一个局部变量，局部变量的生存期仅限于函数执行的过程中，函数执行完毕，局部变量即被销毁以释放内存。    
    （补充：内部环境可以通过作用域链访问所有的外部环境中的变量对象，但外部环境无法访问内部环境。每个环境都可以向上搜索作用域链，以查询变量和函数名，反之向下则不能。）

</details>

<b><details><summary>66.输出多少？</summary></b>

答案：

```js
var a = 6;
setTimeout(function() {
  var a = 666;
  alert(a); // 输出666，
}, 1000);
a = 66;
```

因为 var a = 666;定义了局部变量 a，并且赋值为 666，根据变量作用域链，
全局变量处在作用域末端，优先访问了局部变量，从而覆盖了全局变量 。

```js
var a = 6;
setTimeout(function() {
  alert(a); // 输出undefined
  var a = 666;
}, 1000);
a = 66;
```

因为 var a = 666;定义了局部变量 a，同样覆盖了全局变量，但是在 alert(a);之前
a 并未赋值，所以输出 undefined。

```js
var a = 6;
setTimeout(function() {
  alert(a);
  var a = 66;
}, 1000);
a = 666;
alert(a);
// 666, undefined;
```

记住： 异步处理，一切 OK 声明提前

</details>

<b><details><summary>67.JS 的继承性？</summary></b>

答案：

```js
window.color = "red";
var o = { color: "blue" };
function sayColor() {
  alert(this.color);
}
sayColor(); //red
sayColor.call(this); //red this-window对象
sayColor.call(window); //red
sayColor.call(o); //blue
```

</details>

<b><details><summary>68.精度问题: JS 精度不能精确到 0.1 所以  。。。。同时存在于值和差值中</summary></b>

答案：

```js
var n = 0.3,
  m = 0.2,
  i = 0.2,
  j = 0.1;
alert(n - m == i - j); //false
alert(n - m == 0.1); //false
alert(i - j == 0.1); //true
```

</details>

<b><details><summary>69.加减运算</summary></b>

答案：

```js
alert("5" + 3); //53 string
alert("5" + "3"); //53 string
alert("5" - 3); //2 number
alert("5" - "3"); //2 number
```

</details>

<b><details><summary>70.结果是什么？</summary></b>

答案：

```js
function foo() {
  foo.a = function() {
    alert(1);
  };
  this.a = function() {
    alert(2);
  };
  a = function() {
    alert(3);
  };
  var a = function() {
    alert(4);
  };
}
foo.prototype.a = function() {
  alert(5);
};
foo.a = function() {
  alert(6);
};
foo.a(); //6
var obj = new foo();
obj.a(); //2
foo.a(); //1
```

</details>

<b><details><summary>71.输出结果</summary></b>

答案：

```js
var a = 5;
function test() {
  a = 0;
  alert(a);
  alert(this.a); //没有定义 a这个属性
  var a;
  alert(a);
}
test(); // 0, 5, 0
new test(); // 0, undefined, 0 //由于类它自身没有属性a， 所以是undefined
```

</details>

<b><details><summary>72.计算字符串字节数</summary></b>

答案：

```js
new (function(s) {
  if (!arguments.length || !s) return null;
  if ("" == s) return 0;
  var l = 0;
  for (var i = 0; i < s.length; i++) {
    if (s.charCodeAt(i) > 255) l += 2;
    else l += 1; //charCodeAt()得到的是unCode码
  } //汉字的unCode码大于 255bit 就是两个字节
  alert(l);
})("hello world!");
```

</details>

<b><details><summary>73.结果是</summary></b>

答案： var bool = !!2; alert(bool)；//true;
双向非操作可以把字符串和数字转换为布尔值

</details>

<b><details><summary>74.声明对象，添加属性，输出属性</summary></b>

答案：

```js
var obj = {
  name: "leipeng",
  showName: function() {
    alert(this.name);
  }
};
obj.showName();
```

</details>

<b><details><summary>75.匹配输入的字符：第一个必须是字母或下划线开头，长度 5-20</summary></b>

答案：

```js
var reg = /^[a-zA-Z][a-zA-Z0-9_]{5,20}/,
  name1 = "leipeng",
  name2 = "0leipeng",
  name3 = "你好leipeng",
  name4 = "hi";
alert(reg.test(name1));
alert(reg.test(name2));
alert(reg.test(name3));
alert(reg.test(name4));
```

</details>

<b><details><summary>76.检测变量类型</summary></b>

答案：

```js
function checkStr(str) {
  typeof str == "string" ? alert("true") : alert("false");
}
checkStr("leipeng");
```

</details>

<b><details><summary>77.如何在 HTML 中添加事件，几种方法？</summary></b>

答案：

```
1、标签之中直接添加 onclick="fun()";
2、JS 添加 Eobj.onclick = method;
3、现代事件  IE： obj.attachEvent('onclick', method)；
            FF: obj.addEventListener('click', method, false);
```

</details>

<b><details><summary>78.请问代码实现 outerHTML</summary></b>

答案：

```js
//说明：outerHTML其实就是innerHTML再加上本身；
Object.prototype.outerHTML = function() {
  var innerCon = this.innerHTML, //获得里面的内容
    outerCon = this.appendChild(innerCon); //添加到里面
  alert(outerCon);
};
```

演示代码：

```html     
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <title>Document</title>
  </head>
  <body>
    <div id="outer">
      hello
    </div>
    <script>
      Object.prototype.outerHTML = function() {
        var innerCon = this.innerHTML, //获得里面的内容
          outerCon = this.appendChild(innerCon); //添加到里面
        alert(outerCon);
      };
      function $(id) {
        return document.getElementById(id);
      }
      alert($("outer").innerHTML);
      alert($("outer").outerHTML);
    </script>
  </body>
</html>
```

</details>

<b><details><summary>79.JS 中的简单继承 call 方法！</summary></b>

答案：

```js
//顶一个父母类，注意：类名都是首字母大写的哦！
function Parent(name, money) {
  this.name = name;
  this.money = money;
  this.info = function() {
    alert("姓名： " + this.name + " 钱： " + this.money);
  };
} //定义孩子类
function Children(name) {
  Parent.call(this, name); //继承 姓名属性，不要钱。
  this.info = function() {
    alert("姓名： " + this.name);
  };
} //实例化类
var per = new Parent("parent", 800000000000);
var chi = new Children("child");
per.info();
chi.info();
```

</details>

<b><details><summary>80.解析 URL 成一个对象？</summary></b>

答案：

```js
String.prototype.urlQueryString = function() {
  var url = this.split("?")[1].split("&"),
    len = url.length;
  this.url = {};
  for (var i = 0; i < len; i += 1) {
    var cell = url[i].split("="),
      key = cell[0],
      val = cell[1];
    this.url["" + key + ""] = val;
  }
  return this.url;
};
var url = "?name=12&age=23";
console.log(url.urlQueryString().age);
```

</details>

<b><details><summary>81.看下列代码输出什么？</summary></b>

答案：

```js
var foo = "11"+2-"1";
console.log(foo);
console.log(typeof foo);
// 执行完后foo的值为111，foo的类型为Number。
```

</details>

<b><details><summary>82.看下列代码,输出什么？</summary></b>

答案：
```js
var a = new Object();
a.value = 1;
b = a;
b.value = 2;
alert(a.value);
// 执行完后输出结果为2
```

</details>

<b><details><summary>83.已知数组var stringArray = ["This”, "is”, "Baidu”, "Campus”]，Alert出”This is Baidu Campus”。</summary></b>

答案：alert(stringArray.join(""))

</details>

<b><details><summary>84.请描述出下列代码运行的结果</summary></b>

答案：

```js
function d(){
		console.log(this);
}
d();
```

</details>

<b><details><summary>85.需要将变量e的值修改为“a+b+c+d”,请写出对应的代码</summary></b>

答案：

var e=”abcd”;

</details>

<b><details><summary>86.设计一段代码能够遍历下列整个DOM节点</summary></b>

```html
<div>
    <p>
      <span><a></a></span>
      <span><a></a></span>
    </p>
    <ul>
      <li></li>
      <li></li>
    </ul>
</div>
```

答案：

</details>

<b><details><summary>87.怎样实现两栏等高？</summary></b>

答案：

</details>

<b><details><summary>88.使用js实现这样的效果：在文本域里输入文字时，当按下enter键时不换行，而是替换成“{{enter}}”,(只需要考虑在行尾按下enter键的情况).</summary></b>

答案：

</details>

<b><details><summary>89.以下代码中end字符串什么时候输出</summary></b>

```js
var t=true;
setTimeout(function(){
	console.log(123);
	t=false;
	},1000);
while(t){}
console.log(‘end’);
```

答案：

</details>

<b><details><summary>90.specify(‘hello,world’)//=>’h,e,l,l,o,w,o,r,l,d’实现specify函数</summary></b>

答案：

</details>

<b><details><summary>91.请将一个URL的search部分参数与值转换成一个json对象</summary></b>

答案：

</details>

<b><details><summary>92.请用原生js实现jquery的get\post功能，以及跨域情况下</summary></b>

答案：

</details>

<b><details><summary>93.判断一个字符吕串出现次数最多的字符，统计这个次数并输出</summary></b>

答案：

</details>

<b><details><summary>94.写出3个使用this的典型应用</summary></b>

答案：

</details>

<b><details><summary></summary></b>

答案：

</details>

<b><details><summary></summary></b>

答案：

</details>
