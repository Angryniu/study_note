# Mock.js 一款模拟数据生成器，在后端接口没有写好时 独立模拟数据 进行开发
 * 根据数据模板生成模拟数据
 * 模拟Ajax请求,生成并返回模拟数据
## 用法
 * 下载安装依赖: npm i mockjs --save
 * 创建mock文件夹/index.js    node环境下 require引入  非node环境下 import引入(main.js入口文件也要记得引入)
## 语法
### 数据模板定义(了解即可):'name|rule':value    name:属性名  rule:生成规则 value:属性值
* 'name|min-max':value        重复生成value 次数大于等于min 小于等于max
* 'name|count':value         生成count次 value
* 'info|min-max':[{}]        随机生成数据
* 'info|count':[{}]          随机生成count个数据
### 数据占位符定义
## api
  @params[string]url
  @params[string]type
  @params[any]template
 * Mock.mock([url],[type],[template])
 * Mock.Random   结合 @cname @id 随机数据使用