## CSS

## 盒子模型

是css所使用的一种思维模型，由内容\(content\)、填充\(padding\)、边框\(border\)、边界\(margin\)组成

![](/assets/79462090jw1f1it8lp6ssj20kq0cnjs4.jpg)

### 标准盒子模型

标准模型content部分不包含其他部分。

占用大小为 content+border+padding+margin

实际大小为content+padding+boder

style.width = content的宽度

offsetWidth = 实际大小

clientWidth = content+padding

### IE盒子模型

![](/assets/79462090jw1f1it9z7ugkj20lz0cu0tf.jpg)

ie 盒子模型的 content 部分包含了 border 和 pading

占用大小为 content+margin

实际大小为content

### 怪异盒子模型

主要体现在IE5到IE6

根据 W3C 的规范，元素内容占据的空间是由 width 属性设置的，而内容周围的 padding 和 border 值是另外计算的。不幸的是，IE5.X 和 6 在怪异模式中使用自己的非标准模型。这些浏览器的 width 属性不是内容的宽度，而是内容、内边距和边框的宽度的总和。虽然有方法解决这个问题。但是目前最好的解决方案是回避这个问题。也就是，不要给元素添加具有指定宽度的内边距，而是尝试将内边距或外边距添加到元素的父元素和子元素

**让网页能兼容各个浏览器，我们用标准 w3c 盒子模型，在网页的顶部加上 doctype 声明**

### box-sizing

`box-sizing`属性允许您以特定的方式定义匹配某个区域的特定元素。

`box-sizing`有两个值一个是`content-box`，另一个是`border-box`。

当设置为`box-sizing:content-box`时，将采用`*标准模式*`解析计算，也是默认模式；

当设置为`box-sizing:border-box`时，将采用`*怪异模式*`解析计算，**除外边距，其他都限定在设定的width之内**

目前使用此属性需要前缀如下:

```
-webkit-box-sizing: content-box;
-moz-box-sizing: content-box;
box-sizing: content-box|border-box|inherit;
```

例如，假如您需要并排放置两个带边框的框，可通过将 box-sizing 设置为 "border-box"。这可令浏览器以**怪异模式**呈现出带有指定宽度和高度的框，并把边框和内边距放入框中。

#### 居中

display:table; display:table-cell

display:flex ;justify-content:center;align-items:center

tansform:translate\(-50%,-50%\)

#### 盒子模型

##### 标准 W3C 盒子模型

标准 W3C 盒子模型的范围包括 margin、border、padding、content，并且 content 部分不包含其他部分。

##### IE 盒子模型

IE 盒子模型的范围也包括 margin、border、padding、content，和标准 W3C 盒子模型不同的是：IE 盒子模型的 content 部分包含了 border 和 pading。

##### 

box-sizing:border-box

为元素设定的宽度和高度决定了元素的边框盒。

就是说，为元素指定的任何内边距和边框都将在已设定的宽度和高度内进行绘制。

通过从已设定的宽度和高度分别减去边框和内边距才能得到内容的宽度和高度。

#### 

Flex布局

布局的传统解决方案，基于盒子模型，依赖display属性 +position属性 +float属性。它对于那些特殊布局非常不方便，比如，垂直居中就不容易实现。Flex 是 Flexible Box 的缩写，意为"弹性布局"，用来为盒状模型提供最大的灵活性。

Webkit 内核的浏览器，必须加上-webkit前缀。

##### 

以下6个属性设置在容器上。

flex-direction 属性决定主轴的方向 row \| row-reverse \| column \| column-reverse

flex-wrap 属性定义，如果一条轴线排不下，如何换行 nowrap \| wrap \| wrap-reverse

flex-flow 前两者的缩写

justify-content 定义了项目在主轴上的对齐方式 flex-start \| flex-end \| center \| space-between \| space-around

align-items 属性定义项目在交叉轴上如何对齐 flex-start \| flex-end \| center \| baseline \| stretch

align-content 属性定义了多根轴线的对齐方式。如果项目只有一根轴线，该属性不起作用 flex-start \| flex-end \| center \| space-between \| space-around \| stretch

##### 以下6个属性设置在项目上。

order属性定义项目的排列顺序。数值越小，排列越靠前，默认为0

flex-grow属性定义项目的放大比例，默认为0，即如果存在剩余空间，也不放大

flex-shrink属性定义了项目的缩小比例，默认为1，即如果空间不足，该项目将缩小

flex-basis属性定义了在分配多余空间之前，项目占据的主轴空间（main size）

flex前三者的简写

align-self属性允许单个项目有与其他项目不一样的对齐方式可覆盖align-items属性

#### 栅格系统

网格系统的实现原理非常简单，仅仅是通过定义容器大小，平分12份\(也有平分成24份或32份，但12份是最常见的\)，再调整内外边距，最后结合媒体查询，就制作出了强大的响应式网格系统。Bootstrap框架中的网格系统就是将容器平分成12份。

#### grid布局

CSS 网格布局\(Grid Layout\) 是CSS中最强大的布局系统。 这是一个二维系统，这意味着它可以同时处理列和行，不像flexbox那样主要是一维系统。 你可以通过将CSS规则应用于父元素（成为网格容器）和该元素的子元素（网格元素），来使用网格布局。

[  
https://segmentfault.com/a/1190000012889793](/ https://segmentfault.com/a/1190000012889793)

