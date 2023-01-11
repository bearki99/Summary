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



##  :before和::before的区别

CSS3中新规定， 单冒号用于伪类，双冒号用于伪元素



##  手动写动画的最小时间间隔应该是多少

- 大多数显示器的默认频率是60Hz，采用1/60*1000ms = 16.7ms