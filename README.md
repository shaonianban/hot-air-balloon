# hot-air-balloon
学习记录 - 纯CSS制作一只热气球

<figure> 标签规定独立的流内容（图像、图表、照片、代码等等）
figure 元素的内容应该与主内容相关，但如果被删除，则不应对文档流产生影响。

使用figure标签，类名为balloon
其中有两个div,第一个类名为envelop，包含两个span
第二个类名为basket，包含四个span

样式：
body
margin:0
height:100vh
display:flex
align-item:center
justify-content:center
background:liner-gradient(
  deepskyblue,
  skyblue,
  lightblue 20%
)
- linear-gradient() 函数用于创建一个线性渐变的 "图像"。
 
balloon
width:12em
height:19em
font-size:16px
outline:1px dashed black
display:flex
flex-direction:column
align-items:center

- outline （轮廓）是绘制于元素周围的一条线，位于边框边缘的外围，可起到突出元素的作用
- flex-direction: column 主轴与块轴方向作为默认的书写模式。即纵向从上往下排列（顶对齐）

envelope
width:inherit
height:16em
outline:1px dashed red
position:relative
overflow:hidden

envelope span
position:absolute
width:inherit
height:12em
color:orange
border-radius"50%
background-color:currentColor

- currentColor 只要是需要使用颜色的地方都可以用关键字CurrentColor替换，使其保持和当前元素color属性的值一致，可以减少写css的重复率

envelope span::before
content:''
position:absolute
width:0
height:0
border-width:10em 5.5em 0 5.5em
border-style:solid
border-color:green transparent transparent transparent
left:calc(50%-5.5em)
top:8.45em

- 此样式关联到怎么实现一个三角形

envelope span:nth-child(2)
filter: brightness(0.85) contrast(1.4)
transform: scaleX(0.4)

-filter为滤镜属性
brightness亮度
contrast对比度
blur模糊
drop-shadow阴影
opacity透明度　
saturate饱和度
grayscale灰度
- transform:scaleX(0.4)把宽度缩小为0.4

basket
position:relative
width:2em
height:3em
outline:1px dashed red;

basket::before
content:''
position:absolute
width:inherit
height:1.6em
background-color:peru
bottom:0
border-radius:0 0 0.5em 0.5em

basket::after
content:''
position:absolute
width:105%
height:0.3em
background-color:saddlebrown
top:1.3em
left:calc((100%-105%)/2)
border-radiu:0.3em

basket span
position:absolute
width:0.1em
height:1.5em
background:burlywood
left: calc((var (--n) -1) * 0.6em )
transform-origin:bottom
transform:rotate(calc(var(--r) * 7deg))

- transform-origin允许您改变被转换元素的位置
- transform:旋转多少度 deg

basket span:nth-child(1)( --n:1; --r:-2)
basket span:nth-child(2)( --n:2; --r:-1)
basket span:nth-child(3)( --n:3; --r:1)
basket span:nth-child(4)( --n:4; --r:2)

动画板块
animation:drift 2s infinite alternate
@keyframes drift{
  to{
    transform:translateY(-5%)
  } 
}
