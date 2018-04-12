## window.onload和document.ready的区别 {#articleHeader0}

前者是页面全部加载完，包括图片等媒体文件

后者是文档结构加载完成，不包括媒体文件，快于前者

## 数组去重

```
//es6语法

[...new Set(arr)]

//Set是ES6标准新增的数据类型,Set对象允许你存储任何类型的唯一值,无论是原始值或者是对象引用
```

```js
//使用indexof来判断
function manangeArr(array){
    var newArr = [];
    array.forEach(elment => {
        if(newArr.indexOf(element) === -1){
            newArr.push(element);
        }
    });
    return newArr;
}
```

```js
//排序去除相邻重复元素
function manangeArr2(arr){
    var arrSort = arr.sort();  
    var arr4 = [];  
    for(let i = 0; i< arrSort.length; i++) {  
        if(arrSort[i] != arrSort[i+1]) {  
            arr4.push(arrSort[i]);  
        }  
    }  
    return arr4;
}
```

## 事件委托 {#articleHeader2}

得益于事件冒泡，当多个元素有相同的事件，将事件绑定在父元素

## 判断变量类型 {#articleHeader3}

typeof\(\)用于判断简单数据；

```js
Object.prototype.toString.call();
```

## 闭包

**闭包就是能够读取其他函数内部变量的函数，在JS中可以理解为定义在一个函数内部的函数，嵌套的函数可以访问在其外部声明的变量**

```js
function init(){
    var name = "wei";
    function display(){
        console.log(name);
    }
    display();
}
init();
```





