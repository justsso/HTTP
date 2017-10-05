# HTTP

#### HTTP 协议用于客户端和服务器端之间的通信

==客户端==： 请求访问文本或图像等资源的一端

==服务端==： 提供资源响应的一端

#### 通过请求和响应的交换达成通信


```
sequenceDiagram
客户端->>服务端: 发送请求
服务端->>客户端: 响应回复
```

==请求报文==中的内容：

![image](http://www.hixiaoya.com/wp-content/uploads/2017/10/http03.png)


#### HTTP 是不保存状态的协议

每一次的请求都是重新建立tcp连接，完事之后，断开tcp连接。和其他的请求没关系，服务端记不住，不保存之前的状态。

#### 请求 URI 定位资源

URI:统一资源标识符，

#### 告知服务器意图的 HTTP 方法
GET POST最常用

PUT DELETE缺乏安全性，不常用

#### 使用方法下达命令
![image](http://www.hixiaoya.com/wp-content/uploads/2017/10/http04.png)


#### 持久连接节省通信量

- 持久连接

之前客户端和服务端的连接是只要发请求就连接，哪怕是连续不断的发请求，也要断开TCP连接，再建立TCP连接

持久连接的意思是：只要任意一端没有明确提出断开连接，则保持 TCP 连接状态。

![image](http://www.hixiaoya.com/wp-content/uploads/2017/10/http05.png)

- 管线化

![image](http://www.hixiaoya.com/wp-content/uploads/2017/10/http06.png)

客户端不用等待服务端发回响应了，可以一直发请求。

#### 使用Cookie的状态管理
http是无状态的，这有好处也有坏处。好处是：服务端的相应处理快了，它不用考虑太多的事儿。坏处是： 它不记得各个客户端是谁，哪怕两次是同一个客户端发送的请求，它也不知道。

为了解决http无状态带来的问题，cookie出现了。cookie本来是用来http传输的，只是它有存储信息的能力，所以在早期才被开发人员用来做存储。现在h5的技术发展迅速，localStorage和sessionStorage更多的被使用....

==cookie的过程==：

1. 请求报文（没有 Cookie 信息的状态）

```
GET /reader/ HTTP/1.1
Host: hackr.jp
```

*首部字段内没有Cookie的相关信息

2. 响应报文（服务器端生成 Cookie 信息）
```
HTTP/1.1 200 OK
Date: Thu, 12 Jul 2012 07:12:20 GMT
Server: Apache
＜Set-Cookie: sid=1342077140226724; path=/; expires=Wed,
10-Oct-12 07:12:20 GMT＞
Content-Type: text/plain; charset=UTF-8
```
3. 请求报文（自动发送保存着的 Cookie 信息）
```
GET /image/ HTTP/1.1
Host: hackr.jp
Cookie: sid=1342077140226724

```




