#  CSS



##  CSS盒子模型

标准盒子模型	content = width

怪异盒子模型	content = width + padding + border

如何设置不同的盒子模型

box-sizing:

1. content-box 标准盒子模型
2. border-box 怪异盒子模型
3. inherit 继承父元素box-sizing属性的值 



##  CSS优先级

!important > 内联样式 > id选择器 > 类/伪类/属性选择器 > 元素/伪元素选择器 > 其他

- 优先级在同权重下以样式定义最近者为准

  

##  CSS3动画

- transition transform animation



## position的值

- absolute 生成绝对定位的元素，相对于距离最近的有定位的父元素
- fixed 生成绝对定位的元素，相对于浏览器窗口进行定位
- relative 生成相对定位的元素，相对于自己进行定位
- static 默认值，没有定位
- inherit 从父元素继承position的值



##  display: inline-block什么时候不会显示间隙

- 溢出空格
- 使用margin负值
- 使用font-size: 0
- word-spacing
- letter-spacing



##  可以改变页面布局的属性

- position display float width height margin padding top left right bottom



##  :before和::before的区别

CSS3中新规定， 单冒号用于伪类，双冒号用于伪元素



##  手动写动画的最小时间间隔应该是多少

- 大多数显示器的默认频率是60Hz，采用1/60*1000ms = 16.7ms



##  圣杯布局 双飞翼布局

圣杯布局 注意 圣杯布局会预先为左右两边的内容留出来padding

**圣杯布局就是将基本布局之后使用向左浮动，middle栏留出两边位置，然后使用相对定位将左右两栏通过`margin`定位到相应位置。**

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      .container {
        padding-left: 150px;
        padding-right: 190px;
        height: 300px;
      }
      .main {
        background-color: brown;
        width: 100%;
        height: 100%;
      }
      .left {
        background-color: aquamarine;
        position: relative;
        margin-left: -100%;
        right: 150px;
        width: 150px;
        height: 150px;
      }
      .right {
        background-color: blue;
        position: relative;
        width: 190px;
        height: 190px;
        margin-left: -190px; //把元素从第二行挪到第一行
        left: 190px;
      }
      .main,
      .left,
      .right {
        float: left;
      }
    </style>
  </head>
  <body>
    <div class="container">
      <div class="main"></div>
      <div class="left"></div>
      <div class="right"></div>
    </div>
  </body>
</html>

```

双飞翼布局

不需要进行relative之后的left

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      .content {
        height: 200px;
      }
      .middle {
        float: left;
        width: 100%;
        height: 200px;
        background-color: burlywood;
      }
      .middle-inner {
        margin: 0 200px;
      }
      .left {
        background-color: aqua;
        margin-left: -100%;
      }
      .right {
        background-color: aquamarine;
        margin-left: -200px;
      }

      .left,
      .right {
        width: 200px;
        height: 200px;
        float: left;
      }
    </style>
  </head>
  <body>
    <div class="content">
      <div class="middle">
        <div class="middle-inner"></div>
      </div>
      <div class="left"></div>
      <div class="right"></div>
    </div>
  </body>
</html>
```



##  margin重叠

- CSS中，相邻的两个盒子的外边距可以结合成一个单独的外边距，这种合并外边距的方式被称为折叠，因此所结合成的外边距称为折叠外边距。

**折叠结果遵循下列计算规则**：

- 两个相邻的外边距都是正数时，折叠结果是它们两者之间较大的值。
- 两个相邻的外边距都是负数时，折叠结果是两者绝对值的较大值。
- 两个外边距一正一负时，折叠结果是两者的相加的和。



##  rgba()和opacity的透明效果区别

- rgba 只能作用于元素的颜色/背景色，设置rgba的元素的子元素不会继承透明的效果
- oapacity直接作用于元素，会被继承



##  如何垂直居中

1. position: absolute;

   left: 50%;

   top: 50%;

   transform:translate(-50%, -50%)

2. position: absolute;

   left: 50%;

   top:50%;

   margin-top: -100px;

   margin-left: -100px;

   height: 200px;

   width: 200px;

3. position: absolute;

   margin: auto;

   left: 0;

   right: 0;

   top: 0;

   bottom: 0;

4. 如何垂直居中一个img？

   display: table-cell;

   text-align: center;

   vertical-align: middle;

##  px和em的区别

px是固定的，指定是多少就是多少

em是相对单位，相对于自己的字体大小，如果没有指定自己的字体大小，会继承自父级元素的字体大小

##  css Content属性

用于伪元素::before,::after里，用于生成插入内容，通常用于清除浮动

```css
/**一种常见利用伪类清除浮动的代码**/
.clearfix:after {
    content:".";       //这里利用到了content属性
    display:block;
    height:0;
    visibility:hidden;
    clear:both; 
 }
.clearfix {
    *zoom:1;
}
```

##  水平居中

- 元素为行内元素，设置父元素text-align: center
- 元素宽度固定，设置左右margin: 0 auto
- 绝对定位+移动：absolute transform
- flex布局：justify-content属性为center
- display设置为table-cell

##  垂直居中

- display: table-cell vertical-align: middle
- flex align-items:center
- 绝对定位 bottom: 0 top: 0 margin: auto
- 绝对定位 top:50% margin-top为高度一半
- 文本垂直居中，line-height设置为height值

##  CSS实现硬件加速

transform opacity filter

##  回流，重绘

- 回流：渲染树中元素的布局发生改变，也会引起重绘
- 重绘：渲染树中的元素外观发生改变，但是不影响布局
- offsetLeft、scrollTop、getComputedStyle也会引起回流
- 回流必定会引起重绘

如何避免回流、重绘：

- 尽量避免使用css表达式
- 批量修改元素的样式
- 缓存Layout属性值
- 需要对元素进行复杂的操作时，可以先隐藏，操作完成后再显示

##  左边宽度固定 右边自适应

1. 浮动+右边只设置高度

``` html
<div class='outer'>
    <div class='left'></div>
    <div class='right'></div>
</div>
```

```css
.outer {
    width: 100%;
    height: 500px;
}
.left {
    width: 200px;
    height: 200px;
    float: left;
}
.right {
    height: 200px;
}
```

2. 右边的元素绝对定位 top: 0 left: 200px right: 0

```css
.outer {
    width: 100%;
    height: 500px;
    background-color: yellow;
    position: relative;
}
.left {
    width: 200px;
    height: 200px;
    background-color: red;
}
.right {
    height: 200px;
    background-color: blue;
    position: absolute;
    left: 200px;
    top:0;          
    right: 0;
}
```



3. 右边的元素margin，左边的float
4. 右边的元素margin，左边的float
5. flex布局

##  如何实现小于12px的字体

transform: scale(0.7); **注意，这个属性只能缩放可以定义宽高的元素**

display: inline-block

##  css有哪些继承属性

- font
  - word-break
  - font-size
  - font-family
  - text-align
  - word-spacing
  - text-shadow

- line-height
- color
- visibility
- cursor

##  CSS选择器介绍

1. ID选择器# myid
2. 元素选择器 span
3. 类选择器 .my
4. 相邻选择器 h1+p
5. 后代选择器 li a
6. 子选择器 ul>li
7. 通配符选择器 *
8. 属性选择器 a[rel='external']
9. 伪类选择器 a:hover

浏览器在解析选择器的时候从右到左

##  伪类 伪元素

伪元素 在内容元素的前后插入额外的元素/样式，但是这些元素实际上不在文档中生成

- 只会在外部显示可见，不会在文档的源代码中找到

##  创建一个三角形

```css
#demo {
    width: 0;
    height: 0;
    border: 20px solid transparent;
    border-top: 20px solid red;
}
```

##  品字布局

1. 上面的div宽为100%
2. 下面弄两个div 宽度分别为50%
3. 用display:inline-block

##  li和li之间有看不到的空白间隔

因为中间有换行的字符，空格也属于字符，把字符大小设置为0就没有空格了

##  列举几种隐藏元素的方法

visibility: hidden;

display: none;

opacity: 0;

transform: scale(0);

height: 0;

##  元素竖向百分比的设定是相对于容器的高度吗

不 是相对于容器的高度

##  a标签上四个伪类的执行顺序

link > visited > hover > active

lvha

##  网页图片文件如何点击下载

添加download属性

##  line-height 理解

实际上是上一行基线到下一行基线的距离

- 如果一个标签没有定义height属性，那么最终表现的高度是由line-height决定的
- 将line-height设置为和height一样大小的值可以实现单行文字的垂直居中

##  设置浮动后元素display值的变化

会变成block

##  一个高度自适应的div，里面有两个div，一个高度100px，希望另一个填满剩下的高度

- 方案1：
  - `.sub { height: calc(100%-100px); }`
- 方案2：
  - `.container { position:relative; }`
  - `.sub { position: absolute; top: 100px; bottom: 0; }`
- 方案3：
  - `.container { display:flex; flex-direction:column; }`
  - `.sub { flex:1; }`
