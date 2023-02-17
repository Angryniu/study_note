# Sass
* 一款强化CSS的辅助工具,在css语法基础上增加了变量、嵌套、混合、导入等高级功能。
* vscode编译sass插件下载   下载sass
## Sass变量
*  数据类型: 字符串、数字、颜色、布尔值、列表、null
*  变量格式为: $variable:值        ps:variable 变量
*  作用域:只能在当前的层级上有效果，块级作用域，外部无法访问
*  !global: 关键词来设置变量是全局的，当处于块级作用域的变量值 后加上!global   则定义为全局变量 外部也可以访问
*  全局变量一般定义在同一个文件: 如 _global.scss
* &:hover{}    & 会被解析为父级选择器
## Sass嵌套规则与属性
* 嵌套规则
  -  nav {
       ul{

       }
       li{

       }

  }
    ---- 转换为  nav ul{};   nav li{};
* 嵌套属性
  - font: {
      family:Helvetica;
      size: 18px;
      weight: bold;
  }
    --- 转换为  font-family:Helvetica  font-size:18px
    **** 注意一定要加: 然后属性一定要写到选择器内部
## @import与Partials    import引入 具有模块化思想 方便维护
* @import指令可以引入 变量定义的文件、颜色相关的文件、字体相关的文件等
* 格式 @import filename;   文件不需要加后缀，编译时自动加
### Partials
* 如果不希望将一个Sass代码文件编译到一个css文件中，可以在文件名的开头添加一个下划线，Sass不会将其编译到css文件中
* 格式 _filename
* 不能将_filename 与 filename 文件名相同，下划线不同的文件 放在同一文件下，会自动忽略_file
## @mixin与@include    mixin混入 类型函数封装好样式，include引入即可使用
* @mixin指令允许我们定义一个可以在整个样式表中重复使用的样式
* @include指令可以将混入(mixin)引入到文档中

* 定义一个混入  _ 等同于 -
  - @mixin import_text {
      color:red;
      font-size:25px;
      font-weight: bold;
      font-border: 1px solid blue;
  }
  - selector{
      @include mixinName
  }
* 混入可以内嵌混入
* 混入可以传递变量
 - @mixin color_mixin($color){
     color:$color;
 }
 - 调用混入传递参数 @include color_mixin(red)
 - 参数可以配默认值 @mixin color_mixin($color:red)
 - 可变参数 不确定混入使用多少个参数 使用...来设置可变参数    @mixin box-shadow($shadows...)
       @include box-shadow(0px 4px 5px #666, 2px 6px 10px #999)
## @extend与继承      extend减少代码重复
* 样式之间只有少量区别，@extend就很有用
## Sass函数
### String函数
* 处理字符串并获取相关信息
* 字符串的其实索引值从1开始，不是0
 - quote(string)   给字符串添加引号   quote(runoob) --->输出  "runoob"
 - str-index(string,substring) 返回substring子字符串第一次在string中出现的位置，如果没有匹配到则返回null
 - str-insert(string,insert,index) 在字符串string中index位置插入insert
 ...............
### Number[数字]函数 
### List[列表]函数
### Map(映射)函数
### 选择器函数
### Introspection函数
### 颜色相关函数