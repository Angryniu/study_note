# AJAX(Asynchronous JavaScript and XML)  异步的JavaScript 和 XML
* 用于创建快速动态网页的技术
* 不重新加载整个页面，可以与服务器交换数据并更新部分网页内容
* 传统网页(不使用ajax)需要更新内容，必须重新加载整个网页

## 工作原理
* 浏览器发生某个事件，比如 onclick
* 创建XMLHttpRequest 实例化对象
* 发送HttpRequest
* 服务器处理HttpRequest，创建响应数据并返回浏览器
* 使用js处理被返回的数据
* 更新页面

## 联合运用
* XMLHttpRequest对象(异步的服务器交换数据)
* JavaScript/DOM(信息显示/交互)
* css(给数据定义样式)
* XML(作为数据转换的格式)

## 使用
* const xhr = new XMLHttpRequest()   创建实例化对象
* xhr.open(method,url)    规定请求方法与地址
* xhr.send()              发送请求
* xhr.onreadystatechange = function(){}   检测到状态码发生改变 
 ps:onreadystatechange 事件，储存函数,每当readyState属性改变时，就会调用该函数
* xhr.response     接受服务器的返回(响应)数据
* xhr.readyState == 4     readyState 存有XMLHttpRequest的状态，0请求未初始化 1服务器建立连接 2请求已接受 3请求处理中 4请求完成
* xhr.status >= 200 && < 300    状态在这个区间就说明找到页面

## GET 与 POST相比
* GET请求比POST更简单更快
### 使用POST请求的情况
* 不愿使用缓存文件(更新服务器上的文件或数据库)
* 向服务器发送大量数据(POST没有数据量限制)
* 发送包含未知字符的用户输入时,POST比GET 更稳定也更可靠

## ajax的属性与方法
### 属性
* responseType 响应类型 xhr.responseType = 'json'  默认值为type
* responseURL 返回序列化URL
* responseText 返回服务器返回纯文本的值
* responseXML  返回 HTML/XML
* response   返回响应的值   是一个对象
* readyState  返回值0 请求初始化 1与服务器建立连接 2接受请求 3处理请求 4请求完成
* status   200 ok   HTTP响应状态码 信息响应(100-199) 成功响应(200-299) 重定向消息(300-399) 客户端错误(400-499) 服务端错误(500-599)
* statusText 返回OK 或者 Not Found
* timeout   设置超时时间
* upload   返回一个上传对象  里面包括很多监听事件
* withCredentials  
### 方法
* abort()    终止该请求
* open(method,url) 初始化请求
* send()   用于发送http请求
* setRequestHeader()  设置HTTP请求头部的方法,必须在open() send() 两个方法之间调用
* getALLResponseHeaders()   返回所有响应头
* getResponseHeader()       响应头文本的字符串
### 事件
* abort  终止触发
* error  遇到错误
* load   请求完成触发
* loadstart 程序开始加载触发
* loadend  程序结束开始触发
* progress  请求接收到数据被周期性触发
* onreadystatechange 只要readyState改变就触发
* timeout 进度由约定时间终止就触发
  
# Promise
* 异步编程的一种解决方案
## promise状态
* 实例对象中的一个属性 [PromiseState]
* pending(进行中)、fulfilled(已成功)、rejected(已失败)
## promise对象的值
* 实例对象中的一个属性[PromiseReuslt]
* 保存着对象[成功/失败]的结果
* resolve
* reject
## promise的api-构造函数 then  catch(对失败结果的处理)
## Promise.resolve(value)   成功的数据/promise对象  返回一个成功/失败的promise对象
## Promise.reject(reason)   失败的原因    返回一个失败的promise对象
## Promise.all([promise1,promise2....])    包含n个promise的数组  返回一个新的promise，只有所有的promise都成功才成功
## Promise.race([promise1,promise2....]) 包含n个promise的数组  返回一个新的promise 第一个完成的promise结果状态就是最终状态
## Promise的then返回结果状态，是由then()指定的回调函数执行的结果决定， 如果回调函数没有返回值，那么promise的then返回结果就是undefined
## Promise的异常穿透
## 中断Promise链   返回一个  pending状态的promise
## async函数的返回值是promise对象  promise对象的结果由async函数执行的返回值决定


# Axios
* 返回结果是一个promise对象
## axios发送请求的方式
* axios({传入配置项})   返回结果是一个promise对象
* axios.request({传入配置项})
* axios.post('url',data)
* axios.get('url')
## axios默认配置
* axios.defaults.method = 'GET'   // 设置默认请求类型为GET
* axios.defaults.baseURL = 'http://127.0.0.1:3000' // 设置基础URL
* axios.defaults.params = {id:100}
* axios.defaults.timeout = 3000   // 超时时间
## axios创建实例对象
* 相当于new
* let duanzi = axios.create({
    baseUrl:""
    timeout:
    })       通过create方法创建实例对象
   duanzi  与 axios功能接近一样
   duanzi({
       url:''
   }).then(value=>{console.log(value)})
## axios拦截器
* 请求拦截器  axios.interceptors.resquest.use(function(response){},function(error){})
* 响应拦截器  axios.interceptors.response.use(function(response){},function(error){})
## axios取消