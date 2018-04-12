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
        if(newArr.indexof(element) === -1){
            newArr.push(element);
        }
    })
    return newArr;
}
```



