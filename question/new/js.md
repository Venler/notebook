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



