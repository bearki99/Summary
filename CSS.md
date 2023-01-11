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

