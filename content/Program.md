# [返回主页](../README.md)


<b><details><summary>1.你如何获取浏览器 URL 中查询字符串中的参数？</summary></b>

```

function showWindowHref(){
    var sHref = window.location.href;
    var args = sHref.split('?');
    if(args[0] == sHref){
        return "";
    }
    var arr = args[1].split('&');
    var obj = {};
    for(var i = 0;i< arr.length;i++){
        var arg = arr[i].split('=');
        obj[arg[0]] = arg[1];
    }
    return obj;
}
var href = showWindowHref(); // obj
console.log(href['name']); // xiaoming

```

</details>

<b><details><summary>2.js实现一个打点计时器</summary></b>

问题描述：

1、从 start 到 end（包含 start 和 end），每隔 100 毫秒 console.log 一个数字，每次数字增幅 1
2、返回的对象中需要包含一个 cancel 方法，用于停止定时操作
3、第一个数需要立即输出

```

实现法一（setTimeout()方法）：

function count(start, end) {
    if(start <= end){
        console.log(start++);
        st = setTimeout(function(){count(start, end)}, 100);
    }
    return {
        cancel: function(){clearTimeout(st);}
    }
}
count(1, 10);


实现法二（setInterval()方法）：

function count(start, end) {
    console.log(start++);
    var timer = setInterval(function () {
        if (start <= end) {
            console.log(start++)
        }
    }, 100);
    return {
        cancel: function () {
            clearInterval(timer)
        }
    }
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

<b><details><summary>3.用js实现一个标准的排序算法</summary></b>

一.冒泡排序
```

function BubbleSort(array) {
  var length = array.length;
  for (var i = length - 1; i > 0; i--) { //用于缩小范围
    for (var j = 0; j < i; j++) { //在范围内进行冒泡，在此范围内最大的一个将冒到最后面
      if (array[j] > array[j+1]) { 
        var temp = array[j];
        array[j] = array[j+1];
        array[j+1] = temp;
      }
    }
    console.log(array);
    console.log("-----------------------------");
  }
  return array;
}
 
 
var arr = [10,9,8,7,7,6,5,11,3];
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

```

function SelectionSort(array) {
  var length = array.length;
  for (var i = 0; i < length; i++) { //缩小选择的范围
    var min = array[i]; //假定范围内第一个为最小值
    var index = i; //记录最小值的下标
    for (var j = i + 1; j < length; j++) { //在范围内选取最小值
      if (array[j] < min) {
        min = array[j];
        index = j;
      }
    }
    if (index != i) { //把范围内最小值交换到范围内第一个
      var temp = array[i];
      array[i] = array[index];
      array[index] = temp;
    }
    console.log(array);
    console.log("---------------------");
  }
  return array;
}
 
var arr = [ 1, 10, 100, 90, 65, 5, 4, 10, 2, 4 ];
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

```

function InsertionSort(array) {
  var length = array.length;
  for (var i = 0; i < length - 1; i++) {
    //i代表已经排序好的序列最后一项下标
    var insert = array[i+1];
    var index = i + 1;//记录要被插入的下标
    for (var j = i; j >= 0; j--) {
      if (insert < array[j]) {
        //要插入的项比它小，往后移动
        array[j+1] = array[j];
        index = j;
      }
    }
    array[index] = insert;
    console.log(array);
    console.log("-----------------------");
  }
  return array;
}
 
var arr = [100,90,80,62,80,8,1,2,39];
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

<b><details><summary>1. JS 字符串使用堆栈处理 "(a,b,(c,d),f,g)"</summary></b>

</details>

<b><details><summary>2. 二维数组操作</summary></b>

</details>

<b><details><summary>3. 用最简单的方式，求一个数组中最大的元素，例如 arr=[5,7,9,42,18,29]</summary></b>

</details>

<b><details><summary>4. 正则表达式，验证手机号码，验证规则：11位数字，以1位开头</summary></b>

</details>

<b><details><summary>5. 以下代码求结果</summary></b>

```

function SuperClass() {
    this.name = "women";
    this.bra = ["a", "b"];
}

SuperClass.prototype.sayWhat = function() {
    console.log("hello")
}

function SubClass() {
    this.subname = "you sister";
    SuperClass.call(this);
}

var sub = new SubClass();
console.log(sub.sayWhat());

```

</details>

<b><details><summary>7. 请给 Array 本地对象增加一个原型方法，他的用途是删除数组中重复的条目并按升序排序，最后返回新数组。</summary></b>

</details>

<b><details><summary>8. 为字符串扩展一个 rewrite 函数，接收一个正则 pattern 和一个字符串 result,如果该字符串符合pattern， 则以 result 对结果进行转义输出。 如</summary></b>

```

'/foo'.rewrite(/^\/foo/, '/bar')
'u1234'.rewrite(/^\/u(\d+)/, '/user/$1')
'/i'.rewrite(/^\o/, '/ooo')

```

</details>

<b><details><summary>9. 实现一个 js 对象序列化函数，将 js 对象序列化为可反序列化的代码，要求1.尽量和json兼容，2.支持不可序列化的值，如undefined/NaN/Infinify-Infinity，3. 支持特殊对象，如正则、Date等</summary></b>

```

serialize({})
serialize({ a: 'b' })
serialize({ a: 0/0 })
serialize({ a: /foo/ })

```

</details>

<b><details><summary>10. 设计一道 JavaScript 的 range 算法如下：</summary></b>

range(1, 10, 3) 返回 [1, 4, 7, 10];
range('A', 'F', 2) 返回 ['A', 'C', 'E']
// 请使用 JavaScript 语言实现该功能（可以使用 ES6）

</details>

<b><details><summary>11. 头条的视频网站上支持了弹幕，假设一个视频有很多弹幕，弹幕的数据是一个数组，格式定义如下：</summary></b>

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

<b><details><summary>12. 请写出以下代码的执行结果</summary></b>
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

<b><details><summary>13. 请说明以下各种情况的执行结果，并注明产生对应结果的理由</summary></b>
```
function doSomething() {
    alert(this);
}

a) element.onclick = doSomething, 点击 element 元素后
b) element.onclick = function() doSomething(){}, 点击 element 元素后
c) 直接执行 doSomething()
```
</details>

<b><details><summary>14. 请写出以下代码的执行结果</summary></b>
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

<b><details><summary>15. 请写出类 Son 继承类 Father</summary></b>
function Father() {}
function Son() {}
</details>

<b><details><summary>16. 请用 JS 写出一个遍历 DOM 节点树的方法</summary></b>

</details>

<b><details><summary>17. 尝试实现注释部分的 JavaScript 代码， 可在其他任何地方添加更多代码。</summary></b>
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

<b><details><summary>18. 请编写一个 JavaScript 函数 parseQuerySting, 它的用途是把 URL 参数解析为一个对象，如</summary></b>
```
var url = "http://www.58.com/index.aspx?key0=0&key1=1&key2=2..."
var obj = parseQuerySting(url);
alert(obj.key0) // 输出 0
```
</details>

<b><details><summary>19. 请给 Array 本地对象添加一个原型方法，它用于删除数组条目中重复的条目（可能有多个重复），返回值是一个包含被删除的重复条目的新数组</summary></b>

</details>

<b><details><summary>20. 我们把一个数字倒着读和原数字相同的数字称之为对称数，例如（1, 121, 88, 8998）,不考虑性能，请找出 1 - 10000 之间的对称数，要求用 JS 实现</summary></b>

</details>

<b><details><summary>21. 以下代码输出多少</summary></b>
```
var name = "world";
(function () {
    if (typeof name === "undefined") {
        var name = "jack";
        console.log("Hi!" + name);
    } else {
        console.log("Hello," + name)
    }
})()
```
</details>

<b><details><summary>22. 数组拍平</summary></b>

</details>

<b><details><summary>如何解决数组塌陷问题</summary></b>

```

    // 1 使用i--
    for(var i=0;i<arr.length;i++){
        if(arr[i]===4){
            arr.splice(i,1);
            i--;
        }
    }
    console.log(arr)

    // 2 从数组的末尾一项开始遍历
    for(var i =arr.length;i>=0;i--){
        if(arr[i]===4){
            arr.splice(i,1);
        }
    }
    console.log(arr)

```

</details>

<b><details><summary></summary></b>

</details>

<b><details><summary></summary></b>

</details>