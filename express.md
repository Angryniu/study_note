# express
* params参数和query参数,params参数用name编写传参,query参数用path编写传参
* req.query() 可以接收params和query参数
* req.body()  可接受data
## 获取数据的方法
### get请求(获取url上面的参数)
* req.query
### post请求(获取请求体的参数)
* 首先安装npm install body-parser --save-dev
* const bodyParser = require('body-parser')	

   app.use(bodyParser.urlencoded({
    extended: false
}))
  app.use(bodyParser.json())
* 然后使用 req.body