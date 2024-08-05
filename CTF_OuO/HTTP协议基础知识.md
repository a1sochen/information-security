# HTTP协议基础知识

reference：[click_here](https://blog.csdn.net/qq_52748334/article/details/136549949)

## 一、HTTP协议请求（header）

### 1.HTTP请求的格式

- 请求行：本次请求的基本信息。

  格式：请求方式 请求路径 协议版本

  示例：GET /emp/1 HTTP/1.1

  

- 请求头：本次请求的附加信息

  格式：一行一个键值对，一个键值对是一个请求头，一次请求可以有多个请求头

  示例：Host: localhost:8080

  

- 请求体：本次请求的正文内容。

  格式：没有固定格式，可以是json，也可以是表单，也可以是二进制数据

  其中：
  	json格式示例：{"name":"tom", "age": 20}
  	表单格式示例：name=tom&age=20

> POST 和 PUT方式 才有请求体，GET和DELETE方式没有请求体

### 2.HTTP请求头相关参数

- Host：指定请求的服务器的域名和端口号，用于服务器区分请求的域名。
- Connection：指定连接方式，如“keep-alive”表示持久连接，或“close”表示关闭连接。
- Accept：指定客户端能够接受的媒体类型，如“text/html”、“application/json”等。
- Accept-Encoding：指定客户端能够接受的压缩格式，如“gzip”、“deflate”等。
- Accept-Language：指定客户端偏好的语言，如“zh-CN”、“en-US”等。
- User-Agent：指定客户端的浏览器或应用程序信息，如“Mozilla/5.0”等。
- Referer：指定请求来源的URL，用于服务器分析请求来源。
- X-Forwarded-For：表示 HTTP 请求端真实 IP
- Authorization：用于身份验证，如“Basic”或“Bearer”等。
- Cookie：用于存储客户端的会话信息，如登录状态等。
- Content-Type：指定请求体的媒体类型，如“application/x-www-form-urlencoded”、“multipart/form-data”等。
- Content-Length：指定请求体的长度，用于服务器确定请求体的结束位置。
- If-Modified-Since：用于缓存控制，表示客户端只接受在指定时间之后修改过的资源。
- Range：用于请求资源的一部分，如“bytes=0-1023”表示请求资源的前1024个字节。

