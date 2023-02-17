# axios
* 基于promise的一个网络请求库,可用在浏览器和nodejs之中

## axios API
### axios({})    返回promise对象
### axios.request({}) 返回promise对象
### axios.get(url[,config])  传参直接?键名=健值&&键名=健值
### axios.delete(url[,config])  
### axios.option(url[,config])  
### axios.post(url,data[,config])   data请求头数据内容
### axios.put(url,data[,config])   data请求头数据内容
### axios.patch(url,data[,config])   data请求头数据内容
### axios.create({})  创建实例对象并发送请求  搭配实例对象.get/post 方法使用

## axios请求响应结果的结构
* config 配置项
* data 数据
* headers 响应头信息
* ajax实例化对象
* status 状态码
* 状态文本 ok

## axios配置对象详细说明config
* url:路径
* method:get/post...
* baseURL:基础结构 http://127.0.0.1:8000  搭配url一起使用
* transformRequest:[function(data,headers){return data}]   处理请求数据,返回数据
* transformResponse:[function(data,headers){return data}]   处理响应结果,返回数据
* headers:{}     设置请求头信息
* params:{}     设置url参数
* data:{}      设置请求体数据
* timeout:1000  设置超时时间
等等等还有好多好多

## axios的默认配置
* axios.defaults.method = 'GET'  设置默认请求类型
* axios.defaults.baseURL = 'http://127.0.0.1:8000'  设置基础URL
* axios.defaults.timeout = 1000  设置超时时间
等等等

## axios拦截器
