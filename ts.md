# TypeScript
* 描述: TypeScript 是JavaScript的一个超集。
* TypeScript是一种面向对象的编程语言
  - 面向对象主要有两个概念:对象和类
   对象是类的实例  
   类是一个模板，描述一类对象的行为和状态
   方法是类的操作的实现步骤
* 设计目标: 开发大型应用，可以编译成纯js
* 语言特性:TypeScript给JavaScript添加特性的语言扩展
  - 类型批注和编译时类型检查
  - 类型推断
  - 类型擦除
  - 接口
  - 枚举
  - Mixin
  - 泛型编程
  - 名字空间
  - 元组
  - Await

* npm i --global typescript 安装全局ts
  - 使用 tsc命令来执行TypeScript相关代码
  - tsc [ts文件名]  编译为js文件  需要在同级目录下配置tsconfig.json文件 为了防止编译后的ts文件不报错
  - tsc --help     显示帮助信息
  - tsc --module   载入扩展模块
  - tsc --target   设置ECMA版本
  - tsc --declaration 额外生成一个.d.ts扩展名的文件 
  - tsc --removeComments  删除文件的注释
  - tsc [ts文件1] [ts文件2] --out [合并文件名]
  - tsc --sourcemap 生成一个.map文件     sourcemap 是一个存储源代码与编译代码对应位置映射的信息文件
  - tsc --watch  在监视模式下运行编译器。监视输出文件，在改变它们时重新编译

## 基础类型
 * 任意类型 any
 * 数字类型 number
 * 字符串类型 string
 * 布尔类型 boolean
 * 数组类型 number[]    Array<number>
 * 元组类型  A 