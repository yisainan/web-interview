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
document.getElementById('id').value
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
var dom = document.getElementById('id');
dom.innerHTML = 'xxxx';
dom.style.color = '#000'; // 'black'
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
  setTimeout(() => {
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

<b><details><summary>46.什么是代理和通知，写一下他们基本的实现方</summary></b>

答案：

</details>

<b><details><summary></summary></b>

答案：

</details>

<b><details><summary></summary></b>

答案：

</details>

<b><details><summary></summary></b>

答案：

</details>

<b><details><summary></summary></b>

答案：

</details>

<b><details><summary></summary></b>

答案：

</details>
