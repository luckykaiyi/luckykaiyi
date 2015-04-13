---
published: true
layout: post
title: "CSS学习笔记"
date: 2015-04-13
---

# CSS 学习笔记 

回顾一下W3School上面CSS部分的教程，把自己觉得重要的知识点记录一下。

## 盒子模型

### 清除默认样式

使用通用选择器对所有元素进行设置： 

``` 
* { margin：0；padding：0；border：0；}
```

### 关于width

根据 W3C 的规范，width属性值=元素内容区的宽度；而IE5.X 和 6 在怪异模式中使用自己的非标准模型，width属性值=内容+内边距+边框的宽度。 

### 关于border

1. 边框样式默认为none,使用边框必须声明样式。  
2. 利用`border-color：transparent`可以创建透明边框，结合：hover伪类设置border-color值可以实现鼠标悬停时出现边框颜色的效果。

### 关于 padding

`p { padding: 10% }` 上右下左内边距都等于父元素的 width 的10%（注：百分数是相对于父元素的宽度设置的，margin同理）
 
### 关于 margin

margin合并问题

1. 两个垂直外边距相遇时将会合并，合并后为两者中的较大者。
（mark：只有普通文档流中块框的垂直外边距才会发生外边距合并。行内框、浮动框或绝对定位之间的外边距不会合并。）

2. 外边距可以与自身发生合并。假设有一个空元素，它有外边距，但是没有边框或填充。在这种情况下，上外边距与下外边距就碰到了一起，它们会发生合并。

## CSS定位

### 块框 & 行内框

1. div、h1 或 p 等元素被称为块级元素，这些元素显示为一块内容，即“块框”。与之相反，span 和 strong 等元素称为“行内元素”，这是因为它们的内容显示在行中，即“行内框”。可以使用 display 属性改变生成的框的类型。
2. 在普通流中，块级框从上到下一个接一个地排列，框之间的垂直距离是由框的垂直外边距计算出来。行内框在一行中水平布置，可以使用水平内边距、边框和外边距调整它们的间距。但是，垂直内边距、边框和外边距不影响行内框的高度。由一行形成的水平框称为行框（Line Box），行框的高度总是足以容纳它包含的所有行内框。不过，设置行高可以增加这个框的高度。

### CSS position 属性

CSS 有三种基本的定位机制：普通流、浮动和绝对定位。

CSS position 属性四种类型：

* static 元素框正常生成。块级元素生成一个矩形框，作为文档流的一部分，行内元素则会创建一个或多个行框，置于其父元素中。

* relative 相对定位会按照元素的原始位置对该元素进行移动。元素仍然保持其未定位前的形状，它原本所占的空间仍保留。
  `h1 {position:relative;left:-20px} `从元素的原始左侧位置减去 20 像素, 即相对于正常位置向左移动。
  `h1 {position:relative;left:20px} ` 从元素的原始左侧位置增加 20 像素, 即相对于正常位置向右移动。   
  (mark：相对定位实际上被看作普通流定位模型的一部分，因为元素的位置相对于它在普通流中的位置。)
  
*  absolute 绝对定位元素框从文档流完全删除，相对于最近的已定位祖先元素，如果不存在已定位的祖先元素，那么相对于最初的包含块。绝对定位使元素的位置与文档流无关，因此不占据空间，可以覆盖其他元素，可通过 z-index 属性来控制元素的堆放次序。

* fixed 类似于absolute定位，但其包含块是视窗本身，最常见的例子就是用于header啦。

### CSS 浮动
浮动的框可以向左或向右移动，直到它的外边缘碰到包含框或另一个浮动框的边框为止。  
由于浮动框不在文档的普通流中，所以文档的普通流中的块框表现得就像浮动框不存在一样。

* 如果把所有三个框都向左移动，那么框 1 向左浮动直到碰到包含框，另外两个框向左浮动直到碰到前一个浮动框，从而实现水平排列效果。

* 如果包含框太窄，无法容纳水平排列的三个浮动元素，那么其它浮动块向下移动，直到有足够的空间。如果浮动元素的高度不同，那么当它们向下移动时可能被其它浮动元素“卡住”。

* 默认情况下，块元素会忽略浮动框，而内联元素会围绕浮动框。

* 清除浮动可以利用clear属性：属性值 left、right、both 或 none，它表示框的哪些边不应该挨着浮动框。


###To be continued...