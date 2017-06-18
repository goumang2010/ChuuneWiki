---
title: CSS
excerpt: CSS
categories: 
- FE
---



# 教程


## 编写
http://www.w3school.com.cn/example/csse_examples.asp

## 选择器
http://www.w3school.com.cn/cssref/css_selectors.asp

* em是相对长度单位。相对于当前对象内文本的字体尺寸。如当前对行内文本的字体尺寸未被人为设置，则相对于浏览器的默认字体尺寸。


# 布局


# 特殊概念

## BFC
http://web.jobbole.com/84808/
http://www.imooc.com/article/9723

1. 在BFC下，内部的Box会在垂直方向，一个接一个地放置。
2. Box垂直方向的距离由margin决定。属于同一个BFC的两个相邻Box的margin会发生重叠
3. 在BFC中，每一个盒子的左外边缘（margin-left）会触碰到容器的左边缘(border-left)（对于从右到左的格式来说，则触碰到右边缘），即使存在浮动也是如此。
4. BFC的区域不会与其外的float box重叠。
5. 计算BFC的高度时，浮动元素也参与计算。
6. 内部元素的布局不会影响外部元素。

### 触发条件

- 浮动元素，float 除 none 以外的值
- 绝对定位元素，position的值不为relative和static（absolute，fixed）
- display为以下其中之一的值inline-block, table-cell, table-caption, flex，inline-flex
- overflow 除了 visible 以外的值（hidden，auto，scroll）

### 应用
- 清除浮动（防止塌陷）：https://codepen.io/goumang2010/pen/wegYPp
- 自适应两栏布局： https://codepen.io/goumang2010/pen/mwRQmL
- 解决与子元素边距折叠。


## 边距折叠

https://www.w3.org/TR/CSS2/box.html#collapsing-margins

### 折叠条件
- 常规文档流，（非float和绝对定位）的块级盒子,并且处于同一个BFC当中。
- 没有线盒，没有空隙，没有padding和border将他们分隔开
- 都属于垂直方向上相邻的外边距，可以是下面任意一种情况：
    - 元素的margin-top与其第一个常规文档流的子元素的margin-top
    - 元素的margin-bottom与其下一个常规文档流的兄弟元素的margin-top
    - height为auto的元素的margin-bottom与其最后一个常规文档流的子元素的margin-bottom
    - 高度为0并且最小高度也为0，不包含常规文档流的子元素，并且自身没有建立新的BFC的元

### 折叠结果
1. 两个相邻的外边距都是正数时，折叠结果是它们两者之间较大的值。 
2. 两个相邻的外边距都是负数时，折叠结果是两者绝对值的较大值。 
3. 两个外边距一正一负时，折叠结果是两者的相加的和。

### 结论
https://codepen.io/goumang2010/pen/jwyQjb

- 创建了新的BFC的元素与它的子元素的外边距不会折叠
- 浮动元素不与任何元素的外边距产生折叠（包括其父元素和子元素）
- 绝对定位元素不与任何元素的外边距产生折叠（要求常规文档流）
- inline-block元素不与任何元素的外边距产生折叠（要求块级盒子）
- 一个常规文档流元素的margin-bottom与它下一个常规文档流的兄弟元素的margin-top会产生折叠，除非它们之间存在间隙（clearance）。
- 一个常规文档流元素的margin-top 与其第一个常规文档流的子元素的margin-top产生折叠，条件为父元素不包含 padding 和 border ，子元素不包含 clearance。
- 一个 'height' 为 'auto' 并且 'min-height' 为 '0'的常规文档流元素的 margin-bottom 会与其最后一个常规文档流子元素的 margin-bottom 折叠，条件为父元素不包含 padding 和 border ，子元素的 margin-bottom 不与包含 clearance 的 margin-top 折叠。
- 一个不包含border-top、border-bottom、padding-top、padding-bottom的常规文档流元素，并且其 'height' 为 0 或 'auto'， 'min-height' 为 '0'，其里面也不包含行盒(line box)，其自身的 margin-top 和 margin-bottom 会折叠。

## clearance

https://codepen.io/goumang2010/pen/owBJza

闭合浮动元素的clearance = 浮动元素上下边距高度 + 浮动元素height +浮动元素的上下边框高度+浮动元素的上下内边距高度。