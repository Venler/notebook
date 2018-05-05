## Vue

数据监听器:

```js
object.definepropty(key,{
    value:"",
    writable:true,
    enumrable:true,//是否可删除或者再次修改特性值
    configurable:true,//是否可枚举
    set:function(){},
    get:function(){}
})
```

object.definepropty\(key,{

}\)

指令解析器

watcher

## Babel

Babel的编译过程跟绝大多数其他语言的编译器大致同理，分为三个阶段：

1. **解析**：将代码字符串解析成抽象语法树
2. **变换**：对抽象语法树进行变换操作
3. **再建**：根据变换后的抽象语法树再生成代码字符串

像我们在.babelrc里配置的presets和plugins都是在第2步工作的。

[https://zhuanlan.zhihu.com/p/27289600](https://zhuanlan.zhihu.com/p/27289600)

