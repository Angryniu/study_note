# html基本文档
<! DOCTYPE html> // 声明html5
```
<html lang='zh-CN'>
 <head>
  <meta charset='UTF-8'>
  <title></title>
 </head>
 <body></body>
</html>
```

# 基本标签
```html
<!-- 标题标签 -->
<h1>~<h6>
<!-- 段落标签 段落之间有缝隙 -->
<p>
<!-- 换行标签 -->
<br/>
<hr>
```
[案例链接](https://github.com/Angryniu/study_note/blob/main/%E4%BD%93%E8%82%B2%E6%96%B0%E9%97%BB.html)

# 文本格式化
```html
<!-- 加粗 -->
<strong>加粗</strong>
<b>加粗</b>

<!-- 斜体 -->
<em>斜体</em>
<i>斜体</i>

<!-- 删除线 -->
<del>删除</del>
<s>删除</s>

<!-- 下划线 -->
<ins>下划线</ins>
<u>下划线</u>
```


# 链接
```
 <a href=""></a>
 <a href="#id">跳到提示部分</a>
 <a id="id">提示部分</a>
 ```


# 图片
```
 <img src="url">
 ```

# 区块元素
```
 <div>   块级元素   可以设置长宽、内外边距可以设置，宽度默认为父亲的宽度，不在同一行显示
 <span>  行内元素   不可以设置长宽、内外边距，宽度为自身字体大小，在同一行显示
 <img>   行内块元素  可以设置长宽、内外边距，宽度为自身默认大小，在同一行显示，有间隙
 ```
 
# 列表
```
* 无序列表   <ul><li></li></ul>
* 有序列表   <ol><li></li></ol>
* 自定义列表   <dl><dt></dt><dd></dd></dl>
```

# 表格
```
* <table>
<tr>
   <th></th>
      </tr>
<tr>
   <td></td>
      </tr>
</table>
```

# 框架
```
* <iframe src="">
```

# 表单
```
* <form>
    <input type="text">
    <select>
      <option></option>
     </select>
    <textarea></textarea>
   </form>
```

# 实体
* &lt = <
* &gt = >





# HTML5 Canvas(画布)
* <canvas width="" height="">  通过javascript操作绘图

# HTML5 SVG(可缩放矢量图形)
# HTML5 MathML(数学标记语言)
# HTML5 拖放
# HTML5 地理定位
# HTML5 Video(视频)
# HTML5 Audio(音频)
# HTML5 input(新增类型)
# HTML5 表单元素
# HTML5 表单属性
# HTML5 语义元素
* <header> <nav>.....
# HTML5 web储存
* localStorage 长久保存数据
* sessionStorage 临时保存
# HTML5 web sql数据库
# HTML5 应用程序缓存
# HTML5 web workers
# HTML5 服务器发送事件
# HTML5 WebSocket