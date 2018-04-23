## MVVM

Model-View-ViewModel的缩写

MVVM最早由微软提出来，它借鉴了桌面应用程序的MVC思想，在前端页面中，把Model用纯JavaScript对象表示，View负责显示，两者做到了最大限度的分离。把Model和View关联起来的就是ViewModel。ViewModel负责把Model的数据同步到View显示出来，还负责把View的修改同步回Model，这就是MVVM的设计思想：关注Model的变化，让MVVM框架去自动更新DOM的状态，从而把开发者从操作DOM的繁琐步骤中解脱出来！

三种常见的模式

> 发布者-订阅者模式（backbone.js）
>
> 脏值检查\(angular.js\)
>
> 数据劫持\(vue.js\)

**发布者-订阅者模式**：

类似于公众号，使用vm.set\('property', value\)来更新数据。

**脏值检查**：

通过脏值检测的方式比对数据是否有变更，在指定的事件触发时进入脏值检测。

**数据劫持：**

vue.js 则是采用数据劫持结合发布者-订阅者模式的方式，通过`Object.defineProperty()`来劫持各个属性的`setter`，`getter`，在数据变动时发布消息给订阅者，触发相应的监听回调。

当使用存取器描述属性的特性的时候，允许设置以下特性属性：

```
var obj = {};
Object.defineProperty(obj,"newKey",{
    get:function (){} | undefined,
    set:function (value){} | undefined
    configurable: true | false
    enumerable: true | false
});
```

**注意：当使用了getter或setter方法，不允许使用writable和value这两个属性**

#### **getter/setter**

当设置或获取对象的某个属性的值的时候，可以提供getter/setter方法。

* getter 是一种获得属性值的方法

* setter是一种设置属性值的方法。

在特性中使用get/set属性来定义对应的方法。

```
var obj = {};
var initValue = 'hello';
Object.defineProperty(obj,"newKey",{
    get:function (){
        //当获取值的时候触发的函数
        return initValue;    
    },
    set:function (value){
        //当设置值的时候触发的函数,设置的新值通过参数value拿到
        initValue = value;
    }
});
//获取值
console.log( obj.newKey );  //hello

//设置值
obj.newKey = 'change value';

console.log( obj.newKey ); //change value
```

**注意：get或set不是必须成对出现，任写其一就可以。如果不设置方法，则get和set的默认值为undefined**

**configurable和enumerable同上面的用法。**

vue的流程

![](/assets/132184689-57b310ea1804f.png)observer:数据监听器

compile:指令解析器

watcher：连接二者

