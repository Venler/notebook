## 作用域

变量的作用域无非就是两种：全局变量和局部变量。[  
https://blog.csdn.net/whd526/article/details/70990994  ](/ https://blog.csdn.net/whd526/article/details/70990994)

#### 作用域链（Scope Chain）

那什么是作用域链？ 我的理解就是，根据在内部函数可以访问外部函数变量的这种机制，用链式查找决定哪些数据能被内部函数访问。 想要知道js怎么链式查找，就得先了解js的执行环境

## 闭包

定义在函数内部的函数，可以访问到其他函数内部变量的函数，函数和声明该函数的词法环境的组合

#### 为什么需要闭包呢

局部变量无法共享和长久的保存，而全局变量可能造成变量污染，所以我们希望有一种机制既可以长久的保存变量又不会造成全局污染。而 JavaScript 没有这种原生支持，但我们可以使用闭包来模拟私有方法。私有方法不仅仅有利于限制对代码的访问：还提供了管理全局命名空间的强大能力，避免非核心的方法弄乱了代码的公共接口部分。

#### 特点

占用更多内存

不容易被释放

#### 何时使用

既想反复使用，又想避免全局污染

#### 如何使用

1.定义外层函数，封装被保护的局部变量。 2.定义内层函数，执行对外部函数变量的操作。 3.外层函数返回内层函数的对象，并且外层函数被调用，结果保存在一个全局的变量中。[  
https://zhuanlan.zhihu.com/p/27857268      ](/ https://zhuanlan.zhihu.com/p/27857268)

垃圾回收机制[  
https://segmentfault.com/a/1190000002778015      ](/ https://segmentfault.com/a/1190000002778015)

## 原型链

#### 那什么是原型链呢？

简单理解就是原型组成的链，对象的\_\_proto\_\_它的是原型，而原型也是一个对象，也有\_\_proto\_\_属性，原型的\_\_proto\_\_又是原型的原型，就这样可以一直通过\_\_proto\_\_想上找，这就是原型链，当向上找找到Object的原型的时候，这条原型链就算到头了。

instanceof是判断实例对象的\_\_proto\_\_和生成该实例的构造函数的prototype是不是引用的同一个地址

#### 原型继承

##### 原型继承

```js
function Class(name){
    this.name = name;
}
Class.prototype.say = function(){
    console.log(2)
}

function student(name){
    Class.call(this,name);
}
student.prototype = Object.create(Class.prototype);
student.protitype.constructor = student;
```

##### es6继承

```js
class Student {
    constructor(name) {
        this.name = name;
    }

    hello() {
        alert('Hello, ' + this.name + '!');
    }
}
class PrimaryStudent extends Student {
    constructor(name, grade) {
        super(name); // 记得用super调用父类的构造方法!
        this.grade = grade;
    }

    myGrade() {
        alert('I am at grade ' + this.grade);
    }
}
```

##### new操作符

```js
var obj = {};
obj.prototype = fn.prototype;
fn.call(obj);
return obj;
```

##### object.create\(fn\)

```
var fn2 = function(){};
fn2.prototype = fn;
return new fn2();
```

## debounce

使用闭包强制函数在某段时间内只执行一次

## throttle

强制函数以固定的速度执行

## ES6

[http://es6.ruanyifeng.com/\#docs/let](http://es6.ruanyifeng.com/#docs/let)

#### let

ES6 新增了`let`命令，用来声明变量。它的用法类似于`var`，但是所声明的变量，只在`let`命令所在的代码块内有效。

#### ES6 的块级作用域

`let`实际上为 JavaScript 新增了块级作用域。

#### const 命令

`const`声明一个只读的常量。一旦声明，常量的值就不能改变。

#### 箭头函数

（1）函数体内的`this`对象，就是定义时所在的对象，而不是使用时所在的对象。

（2）不可以当作构造函数，也就是说，不可以使用`new`命令，否则会抛出一个错误。

（3）不可以使用`arguments`对象，该对象在函数体内不存在。如果要用，可以用 rest 参数代替。

（4）不可以使用`yield`命令，因此箭头函数不能用作 Generator 函数。

上面四点中，第一点尤其值得注意。`this`对象的指向是可变的，但是在箭头函数中，它是固定的。

#### Promise 的含义

Promise 是异步编程的一种解决方案，比传统的解决方案——回调函数和事件——更合理和更强大。它由社区最早提出和实现，ES6 将其写进了语言标准，统一了用法，原生提供了`Promise`对象。

`Promise`对象有以下两个特点。

（1）对象的状态不受外界影响。`Promise`对象代表一个异步操作，**有三种状态**：`pending`（进行中）、`fulfilled`（已成功）和`rejected`（已失败）。只有异步操作的结果，可以决定当前是哪一种状态，任何其他操作都无法改变这个状态。这也是`Promise`这个名字的由来，它的英语意思就是“承诺”，表示其他手段无法改变。

（2）一旦状态改变，就不会再变，任何时候都可以得到这个结果。`Promise`对象的状态改变，只有两种可能：从`pending`变为`fulfilled`和从`pending`变为`rejected`。只要这两种情况发生，状态就凝固了，不会再变了，会一直保持这个结果，这时就称为 resolved（已定型）。如果改变已经发生了，你再对`Promise`对象添加回调函数，也会立即得到这个结果。这与事件（Event）完全不同，事件的特点是，如果你错过了它，再去监听，是得不到结果的。

#### 原生JS实现promise

[https://blog.csdn.net/Donspeng/article/details/78313891](https://blog.csdn.net/Donspeng/article/details/78313891)

## 事件循环

简单说，就是在程序中设置两个线程：一个负责程序本身的运行，称为"**主线程**"；另一个负责主线程与其他进程（主要是各种I/O操作）的通信，被称为"**Event Loop线程**"（可以译为"消息线程"）。

每当遇到I/O的时候，主线程就让Event Loop线程去通知相应的I/O程序，然后接着往后运行，所以不存在红色的等待时间。等到I/O程序完成操作，Event Loop线程再把结果返回主线程。主线程就调用事先设定的回调函数，完成整个任务。

这种运行方式称为"[异步模式](http://en.wikipedia.org/wiki/Asynchronous_I/O)"（asynchronous I/O）或"非堵塞模式"（non-blocking mode）。

单线程模型虽然对JavaScript构成了很大的限制，但也因此使它具备了其他语言不具备的优势。如果部署得好，JavaScript程序是不会出现堵塞的，这就是为什么node.js平台可以用很少的资源，应付大流量访问的原因。



