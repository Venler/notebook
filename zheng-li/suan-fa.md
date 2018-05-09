# Javascript

## 二位数组中查找

在一个二维数组中，每一行都按照从左到右递增的顺序排序，每一列都按照从上到下递增的顺序排序。请完成一个函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数。

```js
function find(array,target){
    var h = array.length;
    var w = array[0].length;
    if(h === 0){
        return false;
    }
    var i = 0;
    var j = h-1;
    while(i <= w-1 && j >= 0){
        if(array[j][i] > target){
            j--;
        }
        else if(array[j][i] < target){
            i++;
        }
        else{
            return true;
        }
    }
    if(i > w-1 || j < 0){
        return false;
    }
}
```

## 跳台阶

一只青蛙一次可以跳上1级台阶，也可以跳上2级。求该青蛙跳上一个n级的台阶总共有多少种跳法。

```js
function jumpFloor(number)
{
    var num1 = 1;
    var num2 = 2;
    var num  = 0;
    if(number === 0){
        return 0;
    }
    else if(number === 1){
        return 1;
    }
    else if(number === 2){
        return 2;
    }
    for(var i = 3; i <= number; i++){
        num = num1+num2;
        num1 = num2;
        num2 = num;
    }
    return num;
}
```

## 变态跳台阶

一只青蛙一次可以跳上1级台阶，也可以跳上2级……它也可以跳上n级。求该青蛙跳上一个n级的台阶总共有多少种跳法。

```js
function jumpFloorII(number)
{
    if(number === 0){
        return 0;
    }
    else if(number === 1){
        return 1;
    }
    else if(number === 2){
        return 2;
    }
    var num1 = 1;
    var num2 = 2;
    var num = 0;
    for(var i = 3; i < number; i++){
        num = num1+num2+num1;
        num1 = num2;
        num2 = num;
    }
    return num;
}
```

## 求和

求1+2+3+...+n，要求不能使用乘除法、for、while、if、else、switch、case等关键字及条件判断语句（A?B:C）

```js
function Sum_Solution(n)
{
    if( n === 0){
        return 0;
    }
    return n + Sum_Solution(n-1);
}
```



