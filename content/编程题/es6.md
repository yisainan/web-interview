# [返回主页](https://github.com/yisainan/web-interview/blob/master/README.md)

<b><details><summary>1.箭头函数问题</summary></b>

答案：

第 1 题

在使用=>定义函数的时候，this 的指向是定义时所在的对象，而不是使用时所在的对象；

```js
class Animal {
  constructor() {
    this.type = "animal";
  }
  say(val) {
    setTimeout(function() {
      console.log(this); //window
      console.log(this.type + " says " + val);
    }, 1000);
  }
}
var animal = new Animal();
animal.say("hi"); //undefined says hi
```

```js
class Animal {
  constructor() {
    this.type = "animal";
  }
  say(val) {
    setTimeout(() => {
      console.log(this); //Animal
      console.log(this.type + " says " + val);
    }, 1000);
  }
}
var animal = new Animal();
animal.say("hi"); //animal says hi
```

第二题：

箭头函数里面根本没有自己的 this，而是引用外层的 this

```js
// ES6
function foo() {
  setTimeout(() => {
    console.log("id:", this.id);
  }, 100);
}

// 转成ES5
function foo() {
  var _this = this;

  setTimeout(function() {
    console.log("id:", _this.id);
  }, 100);
}
```


</details>

<b><details><summary>2.把以下代码使用两种方法，依次输出 0-9</summary></b>

答案：

```js
var funcs = [];
for (var i = 0; i < 10; i++) {
  funcs.push(function() {
    console.log(i);
  });
}
funcs.forEach(function(func) {
  func(); //输出十个10
});
```

解决办法：

方法一：使用立即执行函数

```js
var funcs = [];
for (var i = 0; i < 10; i++) {
  funcs.push(
    (function(value) {
      return function() {
        console.log(value);
      };
    })(i)
  );
}
funcs.forEach(function(func) {
  func(); //依次输出0-9
});
```

方法二：使用闭包

```js
function show(i) {
  return function() {
    console.log(i);
  };
}
var funcs = [];
for (var i = 0; i < 10; i++) {
  funcs.push(show(i));
}
funcs.forEach(function(func) {
  func(); //0 1 2 3 4 5 6 7 8 9
});
```

方法三：使用 let

```js
var funcs = [];
for (let i = 0; i < 10; i++) {
  funcs.push(function() {
    console.log(i);
  });
}
funcs.forEach(function(func) {
  func(); //依次输出0-9
});
```

</details>

<b><details><summary>4.手写一个 promise</summary></b>

答案：

```js
var promise = new Promise((resolve, reject) => {
  if (success) {
    // 操作成功
    resolve(value);
  } else {
    reject(error);
  }
});

promise
  .then(res => console.log(res))
  .catch(err => {
    console.log(err);
  });
```

</details>

<b><details><summary>5.怎么解决回调函数里面回调另一个函数，另一个函数的参数需要依赖这个回调函数。需要被解决的代码如下：</summary></b>

```js
$http.get(url).success(function (res) {
  if (success != undefined) {
    success(res);
  }
}).error(function (res) {
  if (error != undefined) {
    error(res);
  }
});

function success(data) {
  if（ data.id != 0） {
    var url = "getdata/data?id=" + data.id + "";
    $http.get(url).success(function (res) {
      showData(res);
    }).error(function (res) {
      if (error != undefined) {
        error(res);
      }
    });
  }
}
```

答案：使用 Promise/async/await 解决

解析：

```js
function awaitMethod(num) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve(2 * num); // 此处模拟接口的请求
    }, 2000);
  });
}
// 打个比方，await是学生，async是校车，必须等人齐了再开车
async function test() {
  let result = await awaitMethod(30); // await 这个关键字只能在使用async定义的函数里面使用
  console.log(result); // 2秒钟之后控制台输出60 ; 后面利用 result 继续调用函数
  let next = await awaitMethod(result);
  console.log(next); // 4秒钟之后控制台输出120
  return next;
}
// 在async里，必须要将结果return回来，不然的话.then .catch获取不到值
test()
  .then(success => console.log("成功", success))
  .catch(error => console.log("失败", error));
```

</details>

<b><details><summary>6.以下代码依次输出的内容是？</summary></b>

```js
setTimeout(function() {
  console.log(1);
}, 0);
new Promise(function executor(resolve) {
  console.log(2);
  for (var i = 0; i < 10000; i++) {
    i == 9999 && resolve();
  }
  console.log(3);
}).then(function() {
  console.log(4);
});
console.log(5);
```

答案：打印顺序 2 3 5 4 1

解析：

首先先碰到一个 setTimeout，于是会先设置一个定时，在定时结束后将传递这个函数放到任务队列里面，因此开始肯定不会输出 1 。

然后是一个 Promise，里面的函数是直接执行的，因此应该直接输出 2 3 。

然后，Promise 的 then 应当会放到当前 tick 的最后，但是还是在当前 tick 中。

因此，应当先输出 5，然后再输出 4 ， 最后在到下一个 tick，就是 1 。

[参考](https://juejin.im/post/5b1ffff96fb9a01e345ba704)

</details>

<b><details><summary>7.jQuery 的 ajax 返回的是 promise 对象吗？</summary></b>

答案：

jquery 的 ajax 返回的是 deferred 对象，通过 promise 的 resolve()方法将其转换为 promise 对象。

var jsPromise = Promise.resolve(\$.ajax('/whatever.json'));

</details>

<b><details><summary>8.promise 只有 2 个状态，成功和失败，怎么让一个函数无论成功还是失败都能被调用？</summary></b>

答案：

```
使用promise.all()

Promise.all方法用于将多个Promise实例，包装成一个新的Promise实例。

Promise.all方法接受一个数组作为参数，数组里的元素都是Promise对象的实例，如果不是，就会先调用下面讲到的Promise.resolve方法，将参数转为Promise实例，再进一步处理。（Promise.all方法的参数可以不是数组，但必须具有Iterator接口，且返回的每个成员都是Promise实例。）

示例：
var p =Promise.all([p1,p2,p3]);
p的状态由p1、p2、p3决定，分为两种情况。
当该数组里的所有Promise实例都进入Fulfilled状态：Promise.all**返回的实例才会变成Fulfilled状态。并将Promise实例数组的所有返回值组成一个数组，传递给Promise.all返回实例的回调函数**。

当该数组里的某个Promise实例都进入Rejected状态：Promise.all返回的实例会立即变成Rejected状态。并将第一个rejected的实例返回值传递给Promise.all返回实例的回调函数。
```

</details>

<b><details><summary>9.Promise 编程题</summary></b>

答案：

第 1 题

```js
const promise = new Promise((resolve, reject) => {
  console.log(1);
  resolve();
  console.log(2);
});
promise.then(() => {
  console.log(3);
});
console.log(4);
```

```
运行结果及原因

运行结果：
1 2 4 3

原因：
Promise 构造函数是同步执行的，promise.then 中的函数是异步执行的。
```

第 2 题

```js
const promise1 = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve("success");
  }, 1000);
});
const promise2 = promise1.then(() => {
  throw new Error("error!!!");
});

console.log("promise1", promise1);
console.log("promise2", promise2);

setTimeout(() => {
  console.log("promise1", promise1);
  console.log("promise2", promise2);
}, 2000);
```

运行结果及原因

```
运行结果：
promise1 Promise { <pending> }
promise2 Promise { <pending> }
Uncaught (in promise) Error: error!!!
promise1 Promise { 'success' }
promise2 Promise {
  <rejected> Error: error!!!
    at promise.then (...)
    at <anonymous> }


原因：
promise 有 3 种状态：pending（进行中）、fulfilled（已完成，又称为Resolved） 或 rejected（已失败）。状态改变只能是 pending->fulfilled 或者 pending->rejected，状态一旦改变则不能再变。上面 promise2 并不是 promise1，而是返回的一个新的 Promise 实例。
```

第 3 题

```js
const promise = new Promise((resolve, reject) => {
  resolve("success1");
  reject("error");
  resolve("success2");
});

promise
  .then(res => {
    console.log("then: ", res);
  })
  .catch(err => {
    console.log("catch: ", err);
  });
```

```
运行结果及原因

运行结果：
then：success1

原因：
构造函数中的 resolve 或 reject 只有第一次执行有效，多次调用没有任何作用，呼应代码二结论：promise 状态一旦改变则不能再变。
```

第 4 题

```js
Promise.resolve(1)
  .then(res => {
    console.log(res); // 打印1
    return 2;
  })
  .catch(err => {
    return 3;
  })
  .then(res => {
    console.log(res); // 打印2
  });
```

运行结果：
1 2

原因：
promise 可以链式调用。提起链式调用我们通常会想到通过 return this 实现，不过 Promise 并不是这样实现的。promise 每次调用 .then 或者 .catch 都会返回一个新的 promise，从而实现了链式调用。

第 5 题

```js
Promise.resolve()
  .then(() => {
    return new Error("error!!!");
  })
  .then(res => {
    console.log("then: ", res);
  })
  .catch(err => {
    console.log("catch: ", err);
  });
```

```
运行结果
then: Error: error!!!
    at Promise.resolve.then (...)
    at ...

原因
.then 或者 .catch 中 return 一个 error 对象并不会抛出错误，所以不会被后续的 .catch 捕获，需要改成其中一种：
return Promise.reject(new Error('error!!!'))
throw new Error('error!!!')

因为返回任意一个非 promise 的值都会被包裹成 promise 对象，即 return new Error('error!!!') 等价于 return Promise.resolve(new Error('error!!!'))。
```

第 6 题

```js
const promise = new Promise((resolve, reject) => {
  setTimeout(() => {
    console.log("once");
    resolve("success");
  }, 1000);
});

const start = Date.now();
promise.then(res => {
  console.log(res, Date.now() - start);
});
promise.then(res => {
  console.log(res, Date.now() - start);
});
```

```
运行结果：
once
success 1001
success 1001
注：1001不是准确数值，也可能是998、999、1000、1002 等

原因：
promise 的 .then 或者 .catch 可以被调用多次，但这里 Promise 构造函数只执行一次。或者说 promise 内部状态一经改变，并且有了一个值，那么后续每次调用 .then 或者 .catch 都会直接拿到该值。
```

第 7 题

```js
const promise = Promise.resolve().then(() => {
  return promise;
});
promise.catch(console.error);
```

```
运行结果
TypeError: Chaining cycle detected for promise #<Promise>...

原因
.then 或 .catch 返回的值不能是 promise 本身，否则会造成死循环。
```

第 8 题

```js
Promise.resolve(1)
  .then(2)
  .then(Promise.resolve(3))
  .then(console.log);
```

```
运行结果
1

原因
.then 或者 .catch 的参数期望是函数，传入非函数则会发生值穿透。
```

第 9 题

```js
Promise.resolve()
  .then(
    function success(res) {
      throw new Error("error");
    },
    function fail1(e) {
      console.error("fail1: ", e);
    }
  )
  .catch(function fail2(e) {
    console.error("fail2: ", e);
  });
```

```
运行结果
fail2: Error: error
    at success (...)
    at ...

原因
.then 可以接收两个参数，第一个是处理成功的函数，第二个是处理错误的函数。.catch 是 .then 第二个参数的简便写法，但是它们用法上有一点需要注意：.then 的第二个处理错误的函数捕获不了第一个处理成功的函数抛出的错误，而后续的 .catch 可以捕获之前的错误。
```

第 10 题

```js
process.nextTick(() => {
  console.log("nextTick");
});
Promise.resolve().then(() => {
  console.log("then");
});
setImmediate(() => {
  console.log("setImmediate");
});
console.log("end");
```

```
运行结果
end
nextTick
then
setImmediate

原因
process.nextTick 和 promise.then 都属于 microtask，而 setImmediate 属于 macrotask，在事件循环的 check 阶段执行。事件循环的每个阶段（macrotask）之间都会执行 microtask，事件循环的开始会先执行一次 microtask。
```

</details>

<b><details><summary>10.看题算结果</summary></b>

```js
var tasks = []; // 这里存放异步操作的 Promise
var output = i =>
  new Promise(resolve => {
    setTimeout(() => {
      console.log(new Date(), i);
      resolve();
    }, 1000 * i);
  });

// 生成全部的异步操作
for (var i = 0; i < 5; i++) {
  tasks.push(output(i));
}

console.log(new Date, i);
```

答案：
```
Mon Aug 12 2019 09:37:36 GMT+0800 (中国标准时间) 5
Mon Aug 12 2019 09:33:55 GMT+0800 (中国标准时间) 0
然后每隔1s打印
Mon Aug 12 2019 09:33:56 GMT+0800 (中国标准时间) 1
Mon Aug 12 2019 09:33:57 GMT+0800 (中国标准时间) 2
Mon Aug 12 2019 09:33:58 GMT+0800 (中国标准时间) 3
Mon Aug 12 2019 09:33:59 GMT+0800 (中国标准时间) 4
```

解析：[参考](https://www.cnblogs.com/adouwt/p/6481479.html)

</details>

<b><details><summary>11.看题算结果</summary></b>

```js
// 模拟其他语言中的 sleep，实际上可以是任何异步操作
const sleep = timeountMS =>
  new Promise(resolve => {
    setTimeout(resolve, timeountMS);
  });

(async () => {
  // 声明即执行的 async 函数表达式
  for (var i = 0; i < 5; i++) {
    await sleep(1000);
    console.log(new Date(), i);
  }

  await sleep(1000);
  console.log(new Date(), i);
})();
```

答案：每隔1s打印
```
Mon Aug 12 2019 09:39:02 GMT+0800 (中国标准时间) 0
Mon Aug 12 2019 09:39:03 GMT+0800 (中国标准时间) 1
Mon Aug 12 2019 09:39:04 GMT+0800 (中国标准时间) 2
Mon Aug 12 2019 09:39:05 GMT+0800 (中国标准时间) 3
Mon Aug 12 2019 09:39:06 GMT+0800 (中国标准时间) 4
Mon Aug 12 2019 09:39:07 GMT+0800 (中国标准时间) 5
```


解析：[参考](https://www.cnblogs.com/adouwt/p/6481479.html)

</details>

<b><details><summary></summary></b>

答案：

</details>
