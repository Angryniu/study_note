## http协议
1. HTTP(hypertext transport protocol) 协议[超文本传输协议], 协议详细规定了浏览器和万维网服务器之间互相通信的规则约定

## 请求报文
1. 行:   请求类型(GET/POST)/URL/HTTP1.1
2. 头:   HOST:atguigu.com
         Cookie: name=guigu
         Content-type: application/x-www-form-urlencoded
         User-Agent: chrome 83
3. 空行
4. 体:  username=admin&password=admin

## 响应报文
1. 行: HTTP/1.1 200 OK
2. 头: Content-Type: text/html:charset=utf-8
       Content-length:2048
       Content-encoding:gzip
3. 空行:
4. 体: html结构