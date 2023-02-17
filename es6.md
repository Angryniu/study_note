
# es6
## let 与 const
* 不存在变量提升
* let 变量名 只能声明一次
* const声明常量，声明时必须赋值
* 块级作用域
## 解构赋值(Array、Object)
## 模板字符串(`${变量名}`)
## 简化对象写法
## 箭头函数
* this 是静态的，始终指向函数声明时所在作用域下的this值
* 箭头函数不能作为构造实例化对象
* 不能使用arguments变量
* 省略小括号，当形参只有一个的时候
* 省略花括号，当代码体只有一条语句的时候，return必须省略
##  函数参数赋默认值
* 实参小于形参  返回NaN
* 形参小于实参  正常执行
## rest参数
* ...rest 得到的是数组,参数必须要放到参数最后
## Symbol
* 表示独一无二的值,最大的用法是用来定义对象的唯一属性名
* 不能与其它数据进行运算
### 两种创建方式
* Symbol(标识字符串)
* Symbol.for(标识字符串)
* 第一种同时创建2个Symbol === false  第二种 true
## 迭代器
* iterator是一种接口，为各种不同的数据结构提供统一的访问机制.任何数据结构只要部署iterator接口，就可以完成遍历操作
* for....of..  遍历Array得到的是变量名
* for....in..  遍历Array得到的是下标0 1 2 3
* 包含迭代器的数据类型:Array、Arguments、Set、Map、String、TypedArray、NodeList
* 工作原理
1.创建一个指针对象(创建一个对象，里面包含next()方法),指向当前数据结构的起始位置
2.第一次调用对象的next方法,指针自动指向数据结构的第一个成员
3.接下来不断调用next方法,指针一直往后移动,直到指向最后一个成员
4.每调用next方法返回一个包含value 和 done属性的对象
## 生成器函数
* function * 函数名()
* 可以使用迭代器遍历
* 函数内部使用yield(函数分隔符)语句
* 函数名.next(实参)  函数执行一次
## 集合Set
* 类似于数组，成员值唯一。集合实现了iterator接口，可使用[扩展运算符](数组有相同元素会去除)和[for...of]进行遍历
* size 返回集合的元素个数
* add 增加一个新元素，返回当前集合
* delete 删除元素  返回boolean值
* has 检测集合中是否包含某个元素，返回boolean值
## 集合Map
* 类似于对象,键值对的集合.键不限于字符串,也可以是对象.实现了iterator接口,可使用[拓展运算符]和[for...of]进行遍历
* size 返回Map的元素个数
* set 增加一个新元素，返回当前Map
* get 返回键名对象的键值
* has 检测Map中是否包含某个元素，返回boolean值
* clear 清空集合，返回undefined
* 用法:let m = new Map()  m.set(键值名,键值)
## class类
* 公共属性写入 constructor
* 公共方法直接写入对象内，只能使用简化写法
### constructor(){}
* constructor方法可以传入形参数,对象内添加属性this.属性名 = 属性值
### static 关键词 设置静态属性方法
* static 属性名=属性值  方法名(){}  私有属性
### extends(延伸)
* class 子类 extends 父类  继承
### super 用在子类constructor内部必须有,在this之前
* 调用父类传参  super(参数1,参数2)
### get 获取变量 可以检测到
### set 修改变量值 可以检测到
## 对象方法扩展(Object.is/assign/set(get)Prototypeof)
### Object.is(数1,数2)  返回值(true/false)
* 判断 NaN 与 NaN 是true
### Object.assign 对象的合并
* 用于配置合并非常合适
### Object.set(get)Prototypeof() 设置/得到原型对象
## 模块化语法(export暴露、 import引入)
### export 暴露
* 分别暴露  export 在每一个要暴露的变量前添加
* 统一暴露  export{变量名1,变量名2} 
* 默认暴露  export default{键值名:键值}
### import 引入
* 通用导入 import * as 别名 from "src"
* 使用分别暴露,用解构赋值 import{变量名1,变量名2} from "src" 当变量名冲突时用  变量名 as 别名
  针对默认暴露,用解构赋值import{default as 别名} from "src"
* 简便形式，针对默认暴露
  import 别名 from 'src'
## ES7新特性
* Array.includes(数组变量)  是否包含 返回true/false
* 2 ** 10   2的10次方

