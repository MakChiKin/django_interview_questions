# 目录 <span id="目录"></span>
[TOC]
# HTTP模块 
共16个常见面试题 <br>`HTTP` `HTTPS` `TCP` `UDP` `COOKIE` `SESSION` `PYTHON` 
## 01.HTTP是什么
`初级` `HTTP`
1. HTTP协议是Hyper Text Transfer Protocol（超文本传输协议）的缩写,是用于从万维网（WWW:World Wide Web ）服务器传输超文本到本地浏览器的传送协议。
2. HTTP协议是一个基于TCP/IP通信协议来传递数据（HTML 文件, 图片文件, 查询结果等）。
3. HTTP协议是一个属于应用层的面向对象的协议。
4. HTTP协议工作于客户端和服务端架构上。浏览器作为HTTP客户端通过URL向HTTP服务器发送请求，服务器根据接收到的请求后，向客户端发送响应信息，

* 基于TCP/IP

    双方建立通信的顺序,以及Web页面显示需要 处理的步骤,等等。像这样把与互联网相关联的协议集合起来总称为       TCP/IP。而HTTP协议是基于TCP/IP协议之上的应用层协议。

* 基于请求－响应模式

    HTTP协议规定,请求从客户端发出,最后服务器响应该请求并返回

* 无状态保存

    HTTP是一种无状态协议。HTTP协议不对请求和响应之间的通信状态进行保存，不做持久化处理。这是为了更快地处理大量事务,确保协议的可伸缩性,而特意把HTTP协议设计成 如此简单的。
    
    可是,随着Web的不断发展,因无状态而导致业务处理变得棘手的情况增多了。比如,用户登录到一家购物网站,即使他跳转到该站的 其他页面后,也需要能继续保持登录状态。
    
    针对这个实例,网站为了能够掌握是谁送出的请求,需要保存用户的状态。HTTP/1.1虽然是无状态协议,但为了实现期望的保持状态功能, 于是引入了Cookie技术。有了Cookie再用HTTP协议通信,就可以管 理状态了。<br>
    
[返回目录](#目录) 
<br><br>


## 02.HTTP请求报文与响应报文格式
`初级` `HTTP`
- **请求报文包含三部分：**
1. 请求行(包含请求方法、URL、HTTP版本信息)
2. 请求首部字段
3. 请求内容实体

<br>

- **响应报文包含三部分：**
1. 状态行(包含HTTP版本、状态码、状态码的原因短语)
2. 响应首部字段
3. 响应内容实体

[返回目录](#目录)
<br><br>


## 03.HTTP常见首部字段有哪些
`初级` `HTTP`
1. 通用首部字段（请求报文与响应报文都会使用的首部字段）

字段|字段描述
---|---
Date|创建报文时间
Connection|连接的管理
Cache-Control|缓存的控制
Transfer-Encoding|报文主体的传输编码方式

2. 请求首部字段（请求报文会使用的首部字段）

字段|字段描述
---|---
Host|请求资源所在服务器
Accept|可处理的媒体类型
Accept-Charset|可接收的字符集
Accept-Encoding|可接受的内容编码
Accept-Language|可接受的自然语言

3. 响应首部字段（响应报文会使用的首部字段）

字段|字段描述
---|---
Accept-Ranges|可接受的字节范围
Location|令客户端重新定向到的URI
Server|HTTP服务器的安装信息

4. 实体首部字段（请求报文与响应报文的实体部分使用的首部字段）

字段|字段描述
---|---
Allow|资源可支持的HTTP方法
Content-Type|实体主类的类型
Content-Encoding|实体主体适用的编码方式
Content-Language|实体主体的自然语言
Content-Length|实体主体的的字节数
Content-Range|实体主体的位置范围，一般用于发出部分请求时使用

[返回目录](#目录)
<br><br>


## 04.HTTP与HTTPS的区别
`初级` `HTTP` `HTTPS`
- HTTP协议传输的数据都是明文、未加密的。因此使用HTTP协议传输隐私信息非常不安全。
- HTTPS协议是由HTTP+SSL构建的网络协议，可进行加密传输、身份认证，要比HTTP协议安全。

不同点|HTTP | HTTPS
---|---|---
安全证书 |不需要|需要到ca申请证书（免费/付费可选）|
是否加密|不加密，信息是明文传输|具有安全性的ssl加密传输协议|
验证数据|不验证数据，可能遭到伪装<br>无法验证报文完整性，可能被篡改|验证数据且对数据完整性保护|
连接方式|无状态连接|HTTPS协议是由SSL+HTTP协议构建的<br>可进行加密传输、身份认证的网络协议，比HTTP协议安全。
默认端口|80|443
安全性|不安全|安全|

[返回目录](#目录)
<br><br>


## 05.列举HTTP请求中常见的请求方式
`初级` `HTTP` 
方法名称|定义
:-:|:--
GET|向特定的路径资源发出请求
POST|向指定路径资源提交数据进行处理请求（一般用于提交表单或者上传文件）
PUT|从客户端向服务器传送数据更新指定的资源
PATCH|从客户端向服务器传送数据更新部分指定的资源
DELETE|请求服务器删除指定的资源
HEAD|向服务器索要与GET一样的请求，但是不返回返回体。<br>这个方法可以在不必传输整个响应内容的情况下，获取包含在响应消息头中的元信息
OPTIONS|查询相应URL支持的HTTP方法
TRACE|返回服务器收到的请求，主要用于测试或诊断
CONNECT|HTTP/1.1协议中预留给能够将连接改为管道方式的代理服务

[返回目录](#目录)
<br><br>


## 06.GET方法与POST方法的区别
`初级` `HTTP`
不同点|GET|POST|
---|---|---
本质|产生1个TCP数据包，只跑1次<br>浏览器会把HTTP header和data一并发送出去，服务器响应200（返回数据）|产生2个TCP数据包，来回各1次（共2次）<br>浏览器先发送header，服务器响应100 continue，浏览器再发送data，服务器响应200 ok（返回数据）
请求形式|参数通过URL传递|把数据放在Request的body中
安全性|因为URL是可见的，可能会泄露私密信息，<br>如账号密码等，所以不安全|数据在request中，用户不可见，较get安全性较高
传输数据量|传输的数据量小，因为受URL长度最多是1024字节，但效率较高；|可以传输大量数据，所以上传文件时只能用Post方式；
支持编码|只能进行url编码|支持多种编码
字符格式|只能支持ASCII字符，向服务器传的中文字符可能会乱码。|支持标准字符集，可以正确传递中文字符。
浏览器处理|请求会被浏览器主动cache，请求参数会被完整保留在浏览器历史记录里|浏览器不会主动cache，参数不会被保留，除非手动设置
业务应用|常用在从服务器上获取数据|常用在向服务器发送数据
<br>

&#8195;&#8195;==**GET只需要跑一趟就把信息送到了，而POST得跑两趟。第一趟，先去和服务器打个招呼“嗨，我等下要送一消息来，你们打开门迎接我”，然后再回头把数据送过去。**==<br>
&#8195;&#8195;因为POST需要两步，时间上消耗的要多一点。所以看起来GET比POST更有效,但事实上不是，在网络环境好的情况下，发一次包的时间和发两次包的时间差别基本可以无视。而在网络环境差的情况下，两次包的TCP在验证数据包完整性上，有非常大的优点。而且并非所有浏览器都会在POST中发送两次包，Firefox浏览器就只发送一次。

[返回目录](#目录)
<br><br>


## 07.常见的HTTP相应状态码
`初级` `HTTP`

状态码|描述
---|---
1xx|指示信息--表示请求已接收，继续处理
2xx|成功--表示请求已被成功接收、理解、接受
3xx|重定向--要完成请求必须进行更进一步的操作
4xx|客户端错误--请求有语法错误或请求无法实现
5xx|服务器端错误--服务器未能实现合法的请求

状态码|描述
---|---
200|请求被正常处理
204|请求被受理但没有资源可以返回
206|客户端只是请求资源的一部分，服务器只对请求的部分资源执行GET方法，<br>相应报文中通过Content-Range指定范围的资源。
301|永久性重定向
302|临时重定向
303|与302状态码有相似功能，只是它希望客户端在请求一个URI的时候，<br>能通过GET方法重定向到另一个URI上
304|发送附带条件的请求时，条件不满足时返回，与重定向无关
307|临时重定向，与302类似，只是强制要求使用POST方法
400|请求报文语法有误，服务器无法识别
401|请求需要认证
403|请求的对应资源禁止被访问
404|服务器无法找到对应资源
500|服务器内部错误
503|服务器正忙

[返回目录](#目录)
<br><br>


## 08.如何对HTTP进行优化
`中级` `HTTP`

**1. TCP复用**<br>
&#8195;&#8195;TCP连接复用是将多个客户端的HTTP请求复用到一个服务器端的TCP连接上，HTTP复用是指一个客户端的多个HTTP请求通过一个TCP连接进行处理<br><br>
**2. 内容缓存**
&#8195;&#8195; <br>&#8195;&#8195;将经常用到的内容进行缓存到浏览器中，那么客户端就可以直接在内存中获取响应的数据<br><br>
**3. 压缩**<br>&#8195;&#8195;将文本数据进行压缩，减少带宽<br><br>
**4. SSL加速**<br>&#8195;&#8195;使用SSL协议对HTTP协议进行加密，在通道内加密并加速<br><br>

[返回目录](#目录)
<br><br>


## 09.TCP与UDP的区别
`初级` `TCP` `UDP`

**UDP协议和TCP协议都是传输层协议。**

&#8195;&#8195;TCP（Transmission ControlProtocol，传输控制协议）提供的是面向连接，可靠的字节流服务。客户和服务器交换数据前，必须现在双方之间建立一个TCP连接，之后才能传输数据。并提供超时重发、丢弃重复数据，检验数据，流量控制等功能，保证数据能完整地从一端传到另一端。<br>
&#8195;&#8195;==简单说就是必须要建立连接后才能传输数据，确保传输完整性，类比现实当中的打电话。==

&#8195;&#8195;UDP（User Data Protocol，用户数据报协议）是一个简单的面向数据报的运输层协议。它不提供可靠性，只是把应用程序传给IP层的数据报发送出去，但是不能保证它们能到达目的地。由于UDP在传输数据报前不用再客户和服务器之间建立一个连接，且没有超时重发等机制，所以传输速度很快。<br>
&#8195;&#8195;==简单说就是单向把程序中的信息发送了，但也不知道对方收到没有，类比现实当中的寄信。==

类型 | 不同点描述
:-:|:--
TCP | 面向连接，可靠的，速度慢，效率低。
UDP | 无连接、不可靠、速度快、效率高。

[返回目录](#目录)
<br><br>


## 10.请介绍TCP的3次握手和4次挥手流程
`初级` `TCP`

SYN:请求字段<br>
ACK:应答字段

<img src="https://img-blog.csdnimg.cn/2019120511481038.gif" width="500" height="300" alt="cookie" align=center>

==建立双工通信，确保双方都能收到对方的信息，所以需要3次握手==<br>
第1次握手：建立连接时，客户端发送syn包（syn=x）到服务器，并进入同步已发送状态，等待服务器确认；SYN：同步序列编号。<br>
> 例如：客户端SYN=1; 客户端向服务器发送建立通信请求把客户端SYN=1的包发到服务器<br>
客户端：我发了！

第2次握手：服务器收到syn包，必须确认客户的SYN（ack=x+1），同时自己也发送一个SYN包（syn=y），即SYN+ACK包，此时服务器进入同步已接受状态；<br>
> 例如：服务端ACK=客户端SYN+1=2,服务端SYN=10；意思是服务端已经收到客户端请求，并在客户端SYN请求值上加1作为ACK值返回给客户端，告知客户端自己已收到，同时发送服务端自己的SYN值给客户端。（注意此处会同时返回SYN和ACK包给客户端）<br>服务器：你发来吧，我收到你的SYN了！


第3次握手：客户端收到服务器的SYN+ACK包，向服务器发送确认包ACK(ack=y+1），此包发送完毕，客户端和服务器进入ESTABLISHED（TCP连接成功）状态，完成三次握手。<br>
> 例如：客户端AC包=服务端SYN+1=11；客户端在收到服务器的SYN包，并在服务器SYN请求值上加1作为ACK返回给服务端，告知客服端已收到服务端的SYN包，完成第三次握手。<br>客户端：我收到你的SYN了！

数据传输.....

<img src="https://img-blog.csdnimg.cn/20191205115043452.gif" width="500" height="300" alt="cookie" align=center>

&#8195;&#8195;==全双工关闭需要客户端和服务器发送和接受都关闭，但是关闭连接时，当Server端收到FIN报文时，很可能并不会立即关闭SOCKET，只能先回复一个ACK报文，所以需要4次挥手==<br>
第1次挥手：客户端进程发出连接释放报文，并且停止发送数据。此时，客户端进入FIN-WAIT-1（终止等待1）状态。
> 客户端：我不发了！停止发送，等待你的确认

第2次挥手：<br>
服务器收到连接释放报文，发出确认报文。服务端就进入了CLOSE-WAIT（关闭等待）状态。TCP服务器通知高层的应用进程，客户端向服务器的方向就释放了，这时候处于半关闭状态，即客户端已经没有数据要发送了，但是服务器若发送数据，客户端依然要接受。这个状态还要持续一段时间，也就是整个CLOSE-WAIT状态持续的时间。
> 服务器：我知道了！进入等待程序关闭状态

客户端收到服务器的确认请求后，此时，客户端就进入FIN-WAIT-2（终止等待2）状态，等待服务器发送连接释放报文（在这之前还需要接受服务器发送的最后的数据）。
> 客户端：好，我知道你已经收到了！继续等待你的关闭确认

第3次挥手：服务器将最后的数据发送完毕后，就向客户端发送连接释放报文，FIN=1，ack=u+1，由于在半关闭状态，服务器很可能又发送了一些数据，假定此时的序列号为seq=w，此时，服务器就进入了LAST-ACK（最后确认）状态，等待客户端的确认。
> 服务器：我不发了！关闭发送，等待你的确认

第4次挥手：<br>客户端收到服务器的连接释放报文后，必须发出确认，ACK=1，ack=w+1，而自己的序列号是seq=u+1，此时，客户端就进入了TIME-WAIT（时间等待）状态。注意此时TCP连接还没有释放，必须经过2MSL（最长报文段寿命）的时间后，当客户端撤销相应的TCB后，才进入CLOSED状态。
> 客户端：我已经收到你的确认了，关闭接收

服务器只要收到了客户端发出的确认，立即进入CLOSED状态。同样，撤销TCB后，就结束了这次的TCP连接。可以看到，服务器结束TCP连接的时间要比客户端早一些。
> 服务器：我已经收到你的确认了，关闭发送


[返回目录](#目录)
<br><br>

## 11.为什么TCP连接的时候是3次握手，关闭的时候却是4次握手？
`初级` `TCP`<br><br>
&#8195;&#8195;因为当Server端收到Client端的SYN连接请求报文后，可以直接发送SYN+ACK报文。其中ACK报文是用来应答的，SYN报文是用来同步的。==但是关闭连接时，当Server端收到FIN报文时，很可能并不会立即关闭SOCKET，所以只能先回复一个ACK报文，告诉Client端，"你发的FIN报文我收到了"。== 只有等到我Server端所有的报文都发送完了，我才能发送FIN报文，因此不能一起发送。故需要四步握手。

[返回目录](#目录)
<br><br>


## 12.HTTP和websocket的区别
`中级` `HTTP` `WEBSOCKET`<br><br>
<img src="https://img-blog.csdnimg.cn/20191205123219258.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MTYyMjA0Mw==,size_16,color_FFFFFF,t_70" width="750" height="400" alt="cookie" align=center>

- ==**最大的区别就是HTTP只能由客户端推送信息给被动的服务端，而websocket既可以让客户端发送消息给服务端，也可以让服务端主动推送消息到客户端，实现双工通信**==
- **http协议是用在应用层的协议，他是基于tcp协议的，http协议建立链接也必须要有三次握手才能发送信息。**

>  &#8195;&#8195;http链接分为短链接，长链接，短链接是每次请求都要三次握手才能发送自己的信息。即每一个request对应一个response。长链接是在一定的期限内保持链接。保持TCP连接不断开。客户端与服务器通信，必须要由客户端发起然后服务器返回结果。客户端是主动的，服务器是被动的。 
- **WebSocket是为解决客户端与服务端实时通信。浏览器和服务器只需要做1个握手的动作，在建立连接之后，双方可以在任意时刻，相互推送信息。同时，服务器与客户端之间交换的头信息很小。**

>  &#8195;&#8195;建立了WebSocket之后服务器不必在浏览器发送request请求之后才能发送信息到浏览器。这时的服务器已有主动权想什么时候发就可以发送信息到服务器。而且信息当中不必在带有head的部分信息了与http的长链接通信来说，这种方式，不仅能降低服务器的压力。而且信息当中也减少了部分多余的信息。

[返回目录](#目录)
<br><br>


## 13.HTTP的长连接与websocket的持久连接的区别
`高级` `HTTP` `WEBSOCKET`
- **HTTP1.1的连接默认使用长连接**（persistent connection）

  &#8195;&#8195;HTTP 1.1默认进行持久连接。在1次 TCP 连接中可以完成多个 HTTP 请求，但是对每个请求仍然要单独发 header，Keep-Alive不会永久保持连接，它有一个保持时间，可以在不同的服务器软件（如Nginx）中设定这个时间。这种长连接是一种“伪链接”


- **WebSocket的持久连接**

  &#8195;&#8195;WebSocket 是一个持久化的协议，只需建立1次Request/Response消息对，之后都是TCP连接，==避免了需要多次建立Request/Response消息对而产生的冗余头部信息。==

[返回目录](#目录)
<br><br>


## 14.什么是cookie？其特点和应用场景有哪些？其如何获取、设置？
`中级` `COOKIE` `PYTHON`<br><br>
<img src="https://img-blog.csdnimg.cn/20190531164116532.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MTYyMjA0Mw==,size_16,color_FFFFFF,t_70" width="500" height="300" alt="cookie" align=center>

- **cookie是一种会话跟踪技术，由服务器生成，然后通过响应发送给客户端的一个键值对。**
- 特点：
> 1. cookie是一个标准的python字典，以键值对方式进行存储，键值都是字符串
> 2. 通过浏览器访问一个网站时，浏览器会将存储该网站相关的所有cookie信息发送给该网站的服务器，request.COOKIES
> 3. cookie是基于域名安全的
> 4. cookie是有过期时间的，如果不指定，默认关闭浏览器后cookie就会过期
> 5. 单个Cookie保存的数据不能超过4K，很多浏览器都限制一个站点最多保存20个Cookie。

- **应用场景：记住用户名和密码，安全性要求不高**

```python
response.set_cookie("is_login",True)  # 获取
request.COOKIES.get("is_login")  # 设置
```

[返回目录](#目录)
<br><br>


## 15.什么是session？其特点和应用场景有哪些？其如何设置、获取、清空？
`中级`  `SESSION` `PYTHON`<br><br>
<img src="https://img-blog.csdnimg.cn/20190531161316354.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MTYyMjA0Mw==,size_16,color_FFFFFF,t_70" width="500" height="330" alt="cookie" align=center>

- **Session是服务器端技术，它保存在服务器上。客户端浏览器访问服务器的时候，服务器把客户端信息以某种形式记录在服务器上。这就是 Session。客户端浏览器再次访问时只需要从该 Session 中查找该客户的状态就可以了。**
- 特点：
> 1. 它是以已键值对进行存储
> 2. 它依赖cookie，唯一的标识码session ID保存在cookie中
> 3. 它也是有过期时间，如果不指定，默认两周就会过期
> 4. 它是用base64加密

- 应用场景：涉及到安全性要求比较高的数据，银行卡账户、密码

```python
 request.session["is_login"] = True  # 设置
 is_login = request.session.get("is_login")  # 获取
 request.session.flush()  # 清空
```

[返回目录](#目录)
<br><br>


## 16.session和cookie的相同点和区别
`中级` `SESSION` `COOKIE` 
- **相同点**

||cookie/session|
---|---|---
跟踪技术|都是踪浏览器用户身份的绘画方式|
生成地点|都在服务器|
存储形式|都是键值对|
过期时间|都可自定义|

- **不同点**

||cookie|session|
---|---|---
存放地点|浏览器|服务器|
安全性|不安全，他人可通过分析存放在本地的cookie并进行Cookie欺骗|比较安全，因数据在服务器中，且用base64加密
依赖性|无|依赖cookie，唯一的标识码session ID保存在cookie中
过期时间|默认关闭浏览器后就会过期|默认两周就会过期

[返回目录](#目录)
<br><br>

## 17.什么是JWT，有什么特点
`初级` `JWT` `cookie` `session` <br><br>
&#8195;&#8195;JWT 全称 JSON Web Tokens，它定义了一种以JSON 对象形式的安全通信方法。它由头部、负载和签名3部分组成。它具有2个特点：
- 简洁：可以通过URL, POST 参数或者在 HTTP header 发送，因为数据量小，传输速度快
- 自包含：负载中包含了所有用户所需要的信息，避免了多次查询数据库



[返回目录](#目录)
<br><br>

## 18.简述JWT的工作原理
`初级` `JWT` `cookie` `session` <br><br>
<img src="https://imgconvert.csdnimg.cn/aHR0cHM6Ly93dzMuc2luYWltZy5jbi9sYXJnZS8wMDZ0TmM3OWd5MWZidjYzcHpxb2NqMzBwajBoOHQ5bS5qcGc" width="700" height="450" align=center>

1. 客户端通过Web表单将正确的用户名和密码发送到服务端的接口。这一过程一般是POST请求。建议的方式是通过SSL加密的传输（https协议），从而避免敏感信息被嗅探。
2. 服务端核对用户名和密码成功后，将用户的id等其他信息作为JWT Payload（负载），将其与头部分别进行Base64编码拼接后签名，形成一个JWT。形成的JWT就是一个形同lll.zzz.xxx的字符串，并设置有效时间。
3. 服务端将JWT字符串作为登录成功的返回结果返回给客户端。
4. 客户端将返回的JWT以cookie的形式保存在浏览器上，并设置cookie的有效时间（建议客户端cookie和服务端JWT的有效时间设置为一致），用户登出时客户端需删除cookie。
5. 客户端在每次请求时将JWT放入HTTP Header中的Authorization位。(解决XSS和XSRF问题)
6. 服务端对收到的JWT进行解密和校验，如检查签名是否正确、Token是否过期、Token的接收方是否是自己等。
7. 验证通过后服务端使用JWT中包含的用户信息进行其他逻辑操作，返回相应结果，否则返回401。


[返回目录](#目录)
<br><br>

## 19.传统Session方式存储ID和JWT的区别
`初级` `JWT` `cookie` `session` <br><br>
&#8195;&#8195;Session是保存在服务端的，而JWT是保存在客户端的。<br>&#8195;&#8195;Session方式存储用户id的最大弊病在于Session是存储在服务器端的，所以==需要占用大量服务器内存，对于较大型应用而言可能还要保存许多的状态。== 一般而言，大型应用还需要借助一些KV数据库和缓存机制来实现Session的存储。<br>&#8195;&#8195;==JWT方式将用户状态分散到了客户端中，可以减少服务器查询数据库的次数和减轻服务端的内存压力。== 除了用户id之外，还可以存储其他的和用户相关的信息，例如该用户是否是管理员、用户所在的分组等。虽说JWT方式让服务器有一些计算压力（例如加密、编码和解码），但是这些压力相比磁盘存储而言可能就不算什么了。具体是否采用，需要在不同场景下用数据说话。

 
[返回目录](#目录)
<br><br>

# Django模块
## 框架层
### 01.简述MVC模式和MVT模式
`初级`  `MVC` `MVT`<br><br>
<img src="https://img-blog.csdnimg.cn/20190516085453110.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MTYyMjA0Mw==,size_16,color_FFFFFF,t_70" width="500" height="330" align=center>

&#8195;&#8195;**MVC**就是把Web应用分为模型(M)，控制器(C)和视图(V)三层,他们之间以一种插件式的、松耦合的方式连接在一起，模型负责业务对象与数据库的映射(ORM)，视图负责与用户的交互(页面)，控制器接受用户的输入调用模型和视图完成用户的请求。

<img src="https://img-blog.csdnimg.cn/20190516091151355.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MTYyMjA0Mw==,size_16,color_FFFFFF,t_70" width="500" height="330" align=center>

**MTV** <br>
&#8195;&#8195;Django的MTV模式本质上和MVC是一样的，也是为了各组件间保持松耦合关系，只是定义上有些许不同，Django的MTV分别是值：

M 代表模型（Model）： 负责业务对象和数据库的关系映射(ORM)。<br>
T 代表模板 (Template)：负责如何把页面展示给用户(html)。<br>
V 代表视图（View）： 负责业务逻辑，并在适当时候调用Model和Template。<br>

除了以上三层之外，还需要一个URL分发器，它的作用是将一个个URL的页面请求分发给不同的View处理，View再调用相应的Model和Template，MTV的响应模式。

[返回目录](#目录)
<br><br>

### 02.谈一谈你对ORM的理解
`初级`  `ORM` <br><br>
**ORM**是“对象-关系-映射”的简称。

&#8195;&#8195;ORM是MVC或者MVC框架中包括一个重要的部分，它实现了数据模型与数据库的解耦，即数据模型的设计不需要依赖于特定的数据库，通过简单的配置就可以轻松更换数据库，这极大的减轻了开发人员的工作量，不需要面对因数据库变更而导致的无效劳动。

[返回目录](#目录)
<br><br>

### 03.简述Django请求生命周期
`初级`  `Django`  `生命周期` <br><br>
<img src="https://img-blog.csdnimg.cn/20191205152153636.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MTYyMjA0Mw==,size_16,color_FFFFFF,t_70" width="480" height="700" align=center>

1. uWSGI服务器通过wsgi协议,将HttpRequest交给web框架 （Flask、Django）     
2. 首先到达request中间件，对请求对象进行校验或添加数据，例如：csrf、request.session，如果验证不通过直接跳转到response中间件
3. 通过URL配置文件找到urls.py文件
4. 根据浏览器发送的URL，通过视图中间件去匹配不同的视图函数或视图类，如果没有找到相对应的视图函数，就直接跳转到response中间件
5. 在视图函数或视图类中进行业务逻辑处理，处理完返回到response中间件
6. 模型类通过ORM获取数据库数据，并返回序列化json或渲染好的Template到response中间件
7. 所有最后离开的响应都会到达response中间件，对响应的数据进行处理，返回HttpResponse给wsgi
8. wsgi经过uWSGI服务器,将响应的内容发送给浏览器。

<br><br>[返回目录](#目录)
<br><br>


### 04.什么是Nginx
`初级` `Nginx` <br><br>
&#8195;&#8195;Nginx是一个高性能代理服务，接收客户端发送过来的HTTP请求和websocket请求，响应静态文件请求和转发动态请求。
<br><br>[返回目录](#目录)
<br><br>


### 05.什么是WSGI
`初级` `wsgi` `Django` <br><br>
&#8195;&#8195;WSGI是Python定义的Web服和Web应用程序或框架之间的一种简单而通用的接口。它定义了Web服务器如何与Python应用程序进行交互，让Python写的Web应用程序可以和Web服务器对接起来。
<br><br>[返回目录](#目录)
<br><br>


### 06.uwsgi、uWSGI和WSGI的区别
`中级`  `uwsgi` `uWSGI` `WSGI` <br><br>
```
graph LR
Nginx-- uwsgi ---uWSGI
uWSGI-- WSGI ---Django
```

- uwsgi：是uWSGI服务器实现的独有协议，用于Nginx服务与uWSGI服务的通信规范
- uWSGI：是一个Web服务器，它实现了WSGI/uwsgi/HTTP等协议，用于接收Nginx转发的动态请求，处理后发个python应用程序
- WSGI：用在python web框架（Django/Flask）编写的应用程序与web服务器之间的规范

[返回目录](#目录)
<br><br>

### 07.Django的request对象是在什么时候创建的？
`中级`  `WSGI` 
```python
class WSGIHandler(base.BaseHandler):
    request = self.request_class(environ)
```
请求走到WSGIHandler类的时候，执行cell方法，将environ封装成了request

[返回目录](#目录)
<br><br>


### 08.什么是中间件并简述其作用
`初级` `中间件`  `Django` <br><br>
&#8195;&#8195;中间件是一个用来处理Django请求和响应的框架级钩子。它是一个轻量、低级别的插件系统，用于在全局范围内改变Django的输入和输出。每个中间件组件都负责做一些特定的功能。<br><br>
[返回目录](#目录)
<br><br>


### 09.列举django中间件的5个方法，以及django中间件的应用场景
`初级` `中间件`  `Django` <br>
- process_request : 请求进来时,权限认证
- process_view : 路由匹配之后,能够得到视图函数
- process_exception : 异常时执行
- process_template_responseprocess : 模板渲染时执行
- process_response : 请求有响应时执行

[返回目录](#目录)
<br><br>

### 10.简述Django对http请求的执行流程
`初级` `Django` <br><br>

[返回目录](#目录)
<br><br>
### 11.Django中如何读取和保存session，整个session的运行机制是什么
`初级` `Django` <br><br>

[返回目录](#目录)
<br><br>
### 12. 什么是CSRF，及防范方式
`初级` `Django` <br><br>

[返回目录](#目录)
<br><br>
### 13. Django中CSRF的实现机制
`初级` `Django` <br><br>

[返回目录](#目录)
<br><br>
### 14.解决跨域的常用方式有哪些
`初级` `Django` <br><br>

[返回目录](#目录)
<br><br>
### 15.跨域请求Django是如何处理的
`初级` `Django` <br><br>

[返回目录](#目录)
<br><br>
### 16.信号的作用是什么？
`初级` `Django` <br><br>

[返回目录](#目录)
<br><br>
### 17.web框架的本质是什么
`初级` `Django` <br><br>

[返回目录](#目录)
<br><br>
### 18.创建Django工程、Django app、以及运行的命令
`初级` `Django` <br><br>

[返回目录](#目录)
<br><br>
### 19.Django App的目录结构
`初级` `Django` <br><br>

[返回目录](#目录)
<br><br>
### 20.Django 获取用户前端请求数据的几种方式
`初级` `Django` <br><br>

[返回目录](#目录)
<br><br>
### 21.在Django中，服务端给客户端响应信息有几种方式？分别是什么
`初级` `Django` <br><br>

[返回目录](#目录)
<br><br>
### 22.谈谈你对restful规范的认识
`初级` `Django` <br><br>

[返回目录](#目录)
<br><br>
### 23.Django本身提供了runserver，为什么不能用来部署
`初级` `Django` <br><br>

[返回目录](#目录)
<br><br>
### 24.Django中如何加载初始化数据
`初级` `Django` <br><br>

[返回目录](#目录)
<br><br>
### 25.缓存系统类型有哪些
`初级` `Django` <br><br>

[返回目录](#目录)
<br><br>
### 26.简述Django下的（内建）缓存机制
`初级` `Django` <br><br>

[返回目录](#目录)
<br><br>
### 27.Django中当用户登录到A服务器进入登陆状态，下次被nginx代理到B服务器会出现什么影响
`初级` `Django` <br><br>

[返回目录](#目录)
<br><br>
### 28.Django如何实现websocket
`初级` `Django` <br><br>

[返回目录](#目录)
<br><br>
### 29.Django如何实现高并发
`初级` `Django` <br><br>

[返回目录](#目录)
<br><br>
### .30列举django的内置组件
`初级`  `Django` <br>
- Admin是对model中对应的数据表进行增删改查提供的组件
- model组件：负责操作数据库
- form组件：<br>1. 生成html代码<br>2. 数据有效性校验<br>3. 校验信息返回并展示
- ModelForm组件即用于数据库操作,也可用于用户请求的验证

[返回目录](#目录)
<br><br>

### 31.Tornado的核是什么
`初级` `Django` <br><br>

[返回目录](#目录)
<br><br>



## 路由层
### 01.路由优先匹配原则是什么
 `初级` `路由`  `Django` <br><br>
**在url匹配列表中==位置优先匹配==**
- 如第1条和第2条同时满足匹配规则，则优先匹配第1条。
- 如第1条为正则模糊匹配，第2条为精确匹配，也是优先匹配第1条

[返回目录](#目录)
<br><br>

### 02.如何获取django urlpatterns里面注册的所有url
`初级` `Django` <br><br>

[返回目录](#目录)
<br><br>
### 03.Django路由系统中include是干嘛用的？
`初级` `Django` <br><br>

[返回目录](#目录)
<br><br>
### 04.Django2.0中的path与django1.xx里面的url有什么区别
`初级` `Django` <br><br>

[返回目录](#目录)
<br><br>
### 05.urlpatterns中的name与namespace有什么作用？你是如何使用的
`初级` `Django` <br><br>

[返回目录](#目录)
<br><br>
### 06.Django重定向你是如何实现的？用的什么状态码
`初级` `Django` <br><br>

[返回目录](#目录)
<br><br>


## 模型层
### 01.命令migrate 和makemigrations的差别
`初级`  `Django` <br><br>
- makemigrations:生成迁移文件
- migrate:执行迁移

[返回目录](#目录)
<br><br>


### 02.Django的Model的继承有几种形式，分别是什么
`初级` `Django` <br><br>

[返回目录](#目录)
<br><br>
### 03.class Meta中的元信息字段有哪些
`初级` `Django` <br><br>

[返回目录](#目录)
<br><br>
### 04.如何给一个字段设置一个主键
`初级` `Django` <br><br>

[返回目录](#目录)
<br><br>
### 05.如何设置一个带有枚举值的字典
`初级` `Django` <br><br>

[返回目录](#目录)
<br><br>
### 06.DateTimeField类型中的auto_now与auto_now_add有什么区别
`初级` `Django` <br><br>

[返回目录](#目录)
<br><br>
### 07.多对多关联的表，如何插入数据？如何删除数据？如何更新数据
`初级` `Django` <br><br>

[返回目录](#目录)
<br><br>
### 08.Django的M2M关系，如何手动生成第三张表
`初级` `Django` <br><br>

[返回目录](#目录)
<br><br>
### 09.Django的Model中的ForeignKey字段中的on_delete参数有什么作用
`初级` `Django` <br><br>

[返回目录](#目录)
<br><br>
### 10.Django中想验证表单提交是否格式正确需要用到Form中的哪个函数
`初级` `Django` <br><br>

[返回目录](#目录)
<br><br>
### 11.当删除一个外键的时候，如何把与其关联的对应关系删除
`初级` `Django` <br><br>

[返回目录](#目录)
<br><br>
### 12.图书管理系统的表结构是怎么设计的
`初级` `Django` <br><br>

[返回目录](#目录)
<br><br>

### 13.django中怎么写原生SQL
`初级` `Django`  `SQL`

1. 使用extra
```python
# 查询人民邮电出版社出版并且价格大于50元的书籍
Book.objects.filter(publisher__name='人民邮电出版社').extra(where=['price>50']) 
```

2. 使用raw
```python
books=Book.objects.raw('select * from hello_book')  

for book in books:  
   print book
```

3. 使用游标
```python
from django.db import connection  
cursor = connection.cursor() 
cursor.execute("insert into hello_author(name) values ('特朗普')"）
cursor.execute("update hello_author set name='普京' WHERE name='特朗普'")  
cursor.execute("delete from hello_author where name='普京'")  
cursor.execute("select * from hello_author")  
cursor.fetchone()  
cursor.fetchall() 
```

[返回目录](#目录)
<br><br>


### 14.如何使用django orm批量创建数据
`中级` `Django`  `ORM`
 
可以使用`django.db.models.query.QuerySet.bulk_create()`批量创建对象，减少SQL查询次数。<br>
例子如下：

```Python
# 创建一个空列表
querysetlist=[]

# 把创建的对象添加入列表中
for i in resultlist:
    querysetlist.append(Account(name=i))   
    
# 批量创建
Account.objects.bulk_create(querysetlist)
```

[返回目录](#目录)
<br><br>

### .列举django ORM中操作QuerySet对象的方法(至少5个)
`初级` `Django`  `ORM`
方法|作用
---|---
all()|查询所有结果
filter()|过滤查询对象。获取不到返回None。
get()|返回与所给筛选条件相匹配的对象，返回结果有且只有1个。如果符合筛选条件的对象超过1个或者没有都会抛出错误。
exclude()|排除满足条件的对象
order_by()|对查询结果排序
reverse()|对查询结果反向排序
count()|返回数据库中匹配查询(QuerySet)的对象数量。
first()|返回第一条记录
last()|返回最后一条记录
exists()|如果QuerySet包含数据，就返回True，否则返回False
values()|返回包含对象具体值的字典的QuerySet
values_list()|与values()类似，只是返回的是元组而不是字典。
distinct()|对查询集去重

[返回目录](#目录)
<br><br>

### 15.ORM如何取消级联
`初级` `Django` <br><br>

[返回目录](#目录)
<br><br>
### 16.查询集的2大特性？什么是惰性执行
`初级` `Django` <br><br>

[返回目录](#目录)
<br><br>
### 17.查询集返回的列表过滤器有哪些
`初级` `Django` <br><br>

[返回目录](#目录)
<br><br>
### 18.selected_related与prefetch_related有什么区别
`初级` `Django` <br><br>

[返回目录](#目录)
<br><br>
### 19.values()与values_list()有什么区别
`初级` `Django` <br><br>

[返回目录](#目录)
<br><br>
### 20.QueryDict和dict区别
`初级` `Django` <br><br>

[返回目录](#目录)
<br><br>
### 21.Django中查询Q和F的区别
`初级` `Django` `ORM`
- Q查询：对数据的多个字段联合查询（常和且或非"&|~"进行联合使用）
- F查询：对数据的不同字段进行比较（常用于比较和更新，对数据进行加减操作）

[返回目录](#目录)
<br><br>






## 视图层
### 01.简述什么是FBV和CBV
`初级`  `Django` <br><br>
FBV（function base views）使用视图函数处理请求<br>
CBV（class base views）使用视图类处理请求<br><br>
[返回目录](#目录)
<br><br>


### 02.如何给CBV的程序添加装饰器
`初级`  `Django` <br>
```
from django.utils.decorators import method_decorator


@method_decorator(check_login)
def post(self, request):
    '''给方法加'''
    ...
    
@method_decorator(check_login)
def dispatch(self, request, *args, **kwargs):
    '''给dispatch加'''
    ...
    
@method_decorator(check_login, name="get")
@method_decorator(check_login, name="post")
class HomeView(View):
    '''给类加'''
    ...
```
导入 method_decorator 装饰器
1. 给方法加
2. 给dispatch加
3. 给类加

[返回目录](#目录)
<br><br>

### 03.常用视图响应的方式有哪些
`初级`  `Django` <br>
- 常用视图响应的方式有4种方式**redirect**、**Response**、**HttpResponse**和**JsonResponse**
```python
return Response({content=响应体, content_type=响应体数据类型, status=状态码)
return HttpResponse(content=响应体, content_type=响应体数据类型, status=状态码) 
return JsonResponse({‘city’: ‘beijing’, ‘subject’: ‘python’},status=response.status_code)
return redirect(‘/index.html’)
```

[返回目录](#目录)
<br><br>

### 04.在视图函数中，常用的验证装饰器有哪些？
`初级` `Django` <br><br>

[返回目录](#目录)
<br><br>
### 05.如何给一个视图函数加上缓存？
`初级` `Django` <br><br>

[返回目录](#目录)
<br><br>


## 模板层
### 01.Django的模板中自定义filter和simple_tag的区别
`初级` `Django` <br><br>

[返回目录](#目录)
<br><br>
### 02.描述下自定义simple_tag
`初级` `Django` <br><br>

[返回目录](#目录)
<br><br>










<span id = "jump"></span>
# 架构模块 
## .介绍你项目的架构设计
[返回目录](#目录)
<br><br>



