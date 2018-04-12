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



