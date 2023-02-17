# Jquery 是javascript库
* 基础语法 $(selector).action()
   * $ 定义JQuery
   * 选择器selector 选择html元素
   * action() 执行对元素的操作
* 开始加载jquery代码(防止html元素未就绪之前就加载jquery代码)
   * 第一种  $(document).ready(function(){ jquery代码  })
   * 第二种  $(function(){ jquery代码   })
## 选择器
* 元素选择器  $('el')  el: div p h1等
* id选择器    $('#id') #id: #only等
* class选择器 $('.class') .class: .main等
* p.main    选取class为main 的p元素
* p:first   选取第一个p元素
* ul li:first  选取第一个ul元素下的第一个li元素
* ul li:first-child  选取每个ul元素下的 第一个li元素
* [href]         选取带有href属性的元素
* a[target='_black']  选取所有target = _black的元素
* :button   选取type = 'button'的input元素 或者 button元素
* tr:even  选取偶数tr元素
* tr:odd    选取奇数tr元素

## 事件
* 鼠标事件: click dblclick mouseenter mouseleave hover
* 键盘事件: keypress keydown keyup
* 表单事件: submit change focus blur
* 窗口事件: load resize scroll unload

## 效果
* 隐藏显示  
   - hide([speed,speedType,callback]) 
   - show([speed,speedType,callback])
   - toggle([speed,speedType,callback]) 来回切换显示与隐藏
* 淡入淡出
   - fadeIn([speed,callback])  淡入已隐藏的元素
   - fadeOut([speed,callback]) 淡出已显示的元素
   - fadetogle([speed,callback]) 切换淡出或淡入
   - fadeTo([speed,opactiy必填,callback])     允许渐变为给定的不透明度
* 滑动
   - slideDown([speed,callback]) 向下滑动
   - slideUp([speed,callback])  向上滑动
   - slideToggle([speed,callback]) 向上或者向下滑动
* 动画
   - animate({params},[speed,callback]) params是css值 比如 left:100px
   - stop(stopAll,goToEnd)   停止动画
## HTML
* 捕获 设置
   - text([newValue:String或function(i,old){return返回新修改值}])     设置或返回所选元素的文本内容
   - html([newValue:String或function(i,old){return返回新修改值}])     设置或返回所选元素的内容(包括html标签)
   - val([newValue:String或function(i,old){return返回新修改值}])      设置或返回表单字段的值
   - attr(属性名,[newValue:String或function(i,old){return返回新修改值}])      获取自定义属性值
   - prop(属性名,[newValue:String或function(i,old){return返回新修改值}])      获取自身固定属性值
* 添加元素
   - append('文本|html')  元素内部后方追加
   - prepend('文本|html')  元素内部前方追加
   - after('文本|html')   元素外部后方追加
   - before('文本|html')   元素外部前方方追加
* 删除元素
   - remove([selector可选])   删除被选元素及其子元素 当选择过滤，删除指定的元素
   - empty()    删除该元素的子元素
* css类
   - addClass('类名')  添加类名
   - removeClass('类名') 移除类名
   - toggleClass('类名')  切换添加或移除类名
   - class('css属性名','属性值') 或者({'css属性名':'属性值','css属性名':'属性值'})

* 尺寸
  * border-box 设置后 它的实际宽度 等于 宽度 - 内外边距 - 边框
  * content-box 设置后 它的实际宽度就等于宽度
   - width()  不包括(内外边距、边框)
   - heigth()  不包括(内外边距、边框)
   - innerWidth() 返回宽度 包括内边距
   - innerHeight() 返回高度 包括内边距
   - outerWidth() 返回宽度 包括内边距和边框
   - outerHeight() 返回高度 包括内边距和边框
## 遍历
* 祖先
   - parent()  选取出当前元素的直接父元素一个
   - parents([可指定所有父元素中的一个父元素]) 选取当前元素的所有父元素 直到html
   - parentsUntil()  选取给点两个元素之间的父元素
* 后代
   - children([可指定直接特定子元素]) 返回当前元素的所有直接子元素
   - find([[可指定后代特定子元素]])  返回所有子元素 '*'所有
      必须填一个
* 同胞
   - siblings()  所有同胞元素
   - next()   下一个同胞元素
* 过滤
   - first()  $('div p').first() div后的第一个p元素
   - last()
   - eq(索引号)
   - filter('指定')
   - not('指定')



   