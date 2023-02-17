## 弹性布局
### 父元素属性
1. display:flex  // 声明显示方式
2. flex-direction: row row-reverse 行  column column-reverse 列 // 声明主轴方向
3. justify-content: flex-start  flex-end center space-between spance-around  //声明主轴的排列方式
4. align-items:flex-start flex-end center baseline stretch(默认拉伸)
5. flex-flow: direction wrap 的缩写
6. flex-wrap: no-wrap(默认) wrap(换行)   // 超出设定宽度自动换行
7. align-content: flex-start  flex-end center space-between spance-around (多行情况下使用)

### 子元素属性
1. order:数值(可为负 从小到达排序)  // 子项目排序
2. flex:数值  // 所占比例
3. align-self:flex-start flex-end center baseline stretch  //给子项目单独设置 侧轴对齐方式

## 媒体查询
1. @media 查询的对象(all  screen 打印机)  and/not/only(min-width:600px 要求){
    变化的属性
}
2. min-width 大于这个值就会发生改变   max-width 小于这个值发生变化



## rem
1. rem单位 相对于 html的字体大小设置
2. eg  html:{font-size:100px}    div{width:1rem}   // width = 100px

## less
1. 变量 @color:pink  然后需要的直接调用
2. 嵌套 内层选择器前面没有&符号,则被解析为父选择器的后代
        如果有&符号,就被解析为父元素自身或父元素的伪类
    eg:
        a{
           &:hover{
               color:red;
           }
        }
3. 运算 对于两个不同的单位的值之间的运算,运算结果的值取第一个值的单位
        如果两个值之间只有一个值有单位,则运算结果就取该单位
        / 除法运算要使用小括号包裹
4. 混合 将一组属性从一个规则集 包含到另一个规则集的方法
    eg:  .myborder{
            border-top:1px solid red
    }
      div{
          width:200px
          height:100px
          .myborder()  // 就将 myborder的属性调进来使用
      }
5. 转义 @min768:(min-width:768px)
    .element{
        @media @min768{
            font-size:1.2rem
        }
    }
6. 函数
7. 命名空间和访问符   包装到函数里边  通过 函数名().选择器 调用
8. 映射
9. 作用域

## rem适配方案
1. 页面元素的rem值 = 页面元素值(100px) / ( 屏幕宽度/ 划分的份数)
2. font-size的大小 就是 屏幕宽度/ 划分的份数的值


## calc函数
1. width:calc(100% - 80px)   + - * /
2. 100%是父盒子的宽度



## 响应式开发

## css3多列
1. column-count:数值  //列数
2. column-gap:数值px  //间隙
3. column-rule:1px solid red  // 分割线
4. column-span:数值   // 跨度
5. column-width:数值  // 列的宽度
6. columns: count width //简写属性

## transform   2d转换
1. translate(x,y)   translateX()  translateY()
2. scale(x,y)  放大倍数 scaleX()  scaleY()
3. rotate(数值deg) 旋转角度
4. skew(x,y)  倾斜  skewX()  skewY()

## 3d转换
1. translate3d(x,y,z) translateZ()     连写时x y z 值不能省略 没有就写0
2. scale3d(x,y,z)  scaleZ()
3. rotate3d(x,y,z,angle)  rotateZ()

## transform 转换属性
1. transform-origin: center center  或者百分比   z的长度
2. transform-style: flat 2d或者 preserve 3d   控制子元素是否开启3d模式 
3. perspective:数值(视距) 透视效果  写在被观察元素的父盒子上面  d:视距   z:物体到屏幕的距离
4. backface-visibility:visible/hidden 可见或者不可见

## transition 过渡
1. transition-property:css的属性
2. transition-druation:持续时间
3. transition-timing-function:时间曲线 linear(匀速) ease(慢-快-慢) ease-in(慢速开始) ease-out(快速开始) ease-in-out(慢速开始和结束)   cubic-bezier(n,n,n,n)  0-1
4. transition-delay:何时开始

## animation 动画
1. @keyframes 规定动画
2. animation-name 规定动画名称
3. animation-duration 完成时间
4. animation-timing-function 速度曲线
5. animation-delay 何时开始
6. animation-iteration-count:数值/infinite(无限的) 播放次数
7. animation-direction:reverse(反向) 是否反向播放
8. animation-play-state 规定是否暂停
9. animation-fill-mode 不播放时的样式


## 网格布局
1. display:grid  // 设定网格显示
2. grid-gap:数值 数值 // 间隙 grid-row-gap  grid-column-gap 的简写
3. grid-template-areas:'元素名称'  // 规定如何显示行和列
4. grid-template-columns:默认值 auto // 指定列大小,设置列的数量
5. grid-template-rows:默认值 auto  // 指定行的大小,设置行的数量
   justify-content:space-evenly(多的 其余一样)
   aligh-content:space-evenly

6. grid-area:从第几行 第几列开始  跨越几行 跨越几列 网格元素名称   注意:在设置过这个属性后,即使设置只设置名字,其余默认值为   auto 会影响别的属性使用
7. grid-row:grid-row-start 和 grid-row-end  // 第几行开始 跨越几行  eg:grid-row: 2 / span 2 从第2行开始 跨越2行
8. grid-column:grid-column-start 和 grid-column-end // 从第几列开始 跨越几列

## filter
1. blur(数值) // 高斯模糊  不可以用百分比
2. brightness(%) // 调亮调暗  百分之0全黑 百分之百 全亮
3. contrast:(%)  // 对比度  百分之0全黑 百分之百 全亮
4. drop-shadow:(x y length color)  // 跟 box-shadow相似 通过filter设定提高浏览加载速度
5. grayscale(%)  // 转换为灰度图像
6. hun-rotate(angle角度)   // 色值旋转
7. invert(%)  // 反转输入颜色
8. opacity(%)  // 透明度  跟 opacity相似 通过 filter设定 提高浏览器加载速度
9. saturate(%)  // 饱和度
10. sepia(%) // 转换为深褐色
11. url(%)  //接受一个滤镜
 
## 选择器
1. 通配符选择器 *{} 选择所有元素
2. 类选择器   .class{}  选择所有这个类名的元素
3. id选择器    #id{}  选择具有这个id的元素
4. 标签选择器   element{} 选择这个所有标签
5. 后代选择器   符号是空格
6. 子代选择器   符号是 >     最近一级元素
7. 并集选择器   符号是 ,    
8. 兄弟选择器(+)   符号是 +   后面的第一个兄弟
9. 兄弟选择器(~)   符号是     后面所有兄弟

### 属性选择器
1. [attribute]  选择所有带有这个属性的选择器
2. [attribute=value]  选择所有带这个属性=值的选择器
3. [attribute ~= value]  选择所有带有这个 单词的 元素
4. [attribute ^= value]   选择具有这个属性且以 value开头的元素
5. [attribute $= value]  选择具有这个属性 且以 value 结尾
6. [attribute *=value]  选择具有这个属性且含有value

### 结构伪类选择器
1. first-child  选择同标签下 第一个元素   不排序
2. last-child 选择同标签下 最后一个元素
3. nth-child(第几个)  选择同标签下 第几个元素 even 偶数 odd奇数 n全选 n+5从第5个开始 -n+5 前5个
4. first-of-type 指定类型的第一个
5. last-of-type 指定类型的最后一个
6. nth-of-type(n) 指定类型的第n个

### 伪元素选择器
1. ::before 在父元素前面插入
2. ::after 在父元素后面插入

## bootstrap