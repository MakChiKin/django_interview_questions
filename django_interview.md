# 目录 <span id="目录"></span>

[欢迎前往GitHub贡献自己的问题和答案](https://github.com/MakChiKin/django_interview_questions)  
[前往有道云浏览（推荐）](http://note.youdao.com/noteshare?id=c16d3e59263823bfc32ea00b95123882)  
[前往CSDN浏览](https://blog.csdn.net/weixin_41622043/article/details/103426652)  

[TOC]
# HTTP模块 
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
### 01.什么是Django框架？
`初级`  `Django`<br><br>
&#8195;&#8195;Django是一个开放源代码的Web应用框架，由Python写成。采用了MTV的框架模式。使用这种架构，程序员可以方便、快捷地创建高品质、易维护、数据库驱动的应用程序。它还包含许多功能强大的第三方插件，使得Django具有较强的可扩展性。

[返回目录](#目录)
<br><br>

### 02.Django对web开发有哪些优势
`初级`  `Django`<br>
- **功能完善、要素齐全**：该有的、可以没有的都有，自带大量常用工具和框架，无须你自定义、组合、增删及修改。
- **完善的文档**：经过十多年的发展和完善，Django有广泛的实践案例和完善的在线文档。开发者遇到问题时可以搜索在线文档寻求解决方案。
- **强大的数据库访问组件**：Django的Model层自带数据库ORM组件，使得开发者无须学习其他数据库访问技术（SQL、pymysql、SQLALchemy等）。
- **灵活的URL映射**：Django使用正则表达式管理URL映射，灵活性高。新版的2.0，进一步提高了URL编写的优雅性。
- **丰富的Template模板语言**：类似jinjia模板语言，不但原生功能丰富，还可以自定义模板标签，并且与其ORM的用法非常相似。
- **自带后台管理系统admin**：只需要通过简单的几行配置和代码就可以实现一个完整的后台数据管理控制平台。
- **完整的错误信息提示**：在开发调试过程中如果出现运行错误或者异常，Django可以提供非常完整的错误信息帮助定位问题。

[返回目录](#目录)
<br><br>
### 03.简述Django的项目的组成模块
`初级`  `Django`<br>
1. **Project**
2. **Apps**
3. **Model**
4. **URL Route**
5. **View**
6. **DTL**
7. **Admin**
8. **Cache System**

<br>

以下详细参考：
- **工程**<br>
> &#8195;&#8195;工程是承载了Django实例的所有设置的Python程序包。大部分情况下，一个Web站点就是一个工程。工程内可以新建及存放该工程固有的应用，或者保存Web站点的设置(数据库设置、Django的选项设置、各应用的设置等)
- **应用**<br>
> &#8195;&#8195;对于Django而言，应用之的是表示单一工程的Web应用的Python程序包。由于其本质就是Python程序包，因此方法PYTHONPATH有效地任何位置都没有问题。这里最好尽量减少应用与工程、应用于应用之间的依赖关系，做到功能独立，以便在其他工程中重复利用。
- **模型**<br>
> &#8195;&#8195;Django提供了O/R映射工具，因此可以用Python代码来描述数据库布局。
　　每个模型都是继承了django.db.models.Model类的Python的类，分别对应数据库中的一个表格。通过建数据库的字段、关系、行为定义为模型类的属性或方法，我们可以使用丰富且灵活的数据库方位API。
- **URL分配器**<br>
> &#8195;&#8195;URL分配器机制使得URL信息不再受框架及扩展名的制约，从而让Web应用的URL设计保持简介。<br>
　　URl在URlconf模块中进行描述，URLconf模块中包含使用正则表达式书写的URL和Python函数的映像。URlconf能够以应用为单位进行分割，因此提高了应用的可重复利用性。另外，我们可以利用给URL设置名称并定义的方式让代码和目标直接通过该名称调用URL，从而将URL设计与代码分离。
- **视图**<br>
> &#8195;&#8195;Django的视图时一类函数，它能够生成指定页面的HttpResponse对象或像Http 404这样的异常情况，返回HTTP请求。典型的视图函数的处理流程通常是从请求参数中获取数据，读取模型，热按后根据获取的数据渲染模板。
- **模板系统**<br>
> &#8195;&#8195;在Django的概念中，模板系统只负责显示，并不是编写逻辑代码的环境。因此Django的模板系统将设计与内容、代码分离开来，是一共功能强、扩展性高、对设计者很友好的模板语言。<br>
　　模板基于文本而不是XML，因此它不但能生成XML和HTML，还能生成E-mail、JavaScript、CSV等任意文本格式。<br>
　　另外，如果使用模板继承功能，子模板只需要将父模板中预留的空位填满即可。我们在编写模板时只需要描述各个模板独有的部分，因此可以省去重复冗余的编码过程。
- **管理界面**<br>
> &#8195;&#8195;大多Web应用在运行过程中，都需要一个专供拥有管理员权限的用户添加、编辑、删除数据的界面，但是实际制作这个界面并不容易。<br>
　　Django只需将已经完工的模型添加到管理站点，就能根据模型定义，动态地生成页面。为我们提供一个功能齐全的管理界面。
- **缓存系统**<br>
> &#8195;&#8195;Django可以使用memcached等缓存后端轻松地缓存数据。比如可以将动态页面的渲染结果缓存下来，等到下次需要时直接读取缓存，从而不必每次都对动态页面进行处理。<br>
　　缓存的后端可以从memcached、数据库、文件系统、本地内存等位置进行选择。缓存对象也支持整个网站、特定的整个视图、部分模板、特定数据等。
　　

[返回目录](#目录)
<br><br>

### 04.简述MVC模式和MVT模式
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

### 05.简述Django请求生命周期
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

[返回目录](#目录)
<br><br>


### 07.什么是WSGI
`初级` `wsgi` `Django` <br><br>
&#8195;&#8195;WSGI(Python Web Server Gateway Interface，即Web服务器网关接口)是Python定义的Web服和Web应用程序或框架之间的一种简单而通用的接口。它是Python为了解决Web服务器端与客户端之间的通信问题而产生的，它基于现存的CGI标准而设计。其定义了Web服务器如何与Python应用程序进行交互，让Python写的Web应用程序可以和Web服务器对接起来。
<br><br>[返回目录](#目录)
<br><br>


### 08.uwsgi、uWSGI和WSGI的区别
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

### 09.Django的request对象是在什么时候创建的？
`中级`  `WSGI` 
```python
class WSGIHandler(base.BaseHandler):
    request = self.request_class(environ)
```
请求走到WSGIHandler类的时候，执行cell方法，将environ封装成了request

[返回目录](#目录)
<br><br>


### 10.什么是中间件并简述其作用
`初级` `中间件`  `Django` <br><br>
&#8195;&#8195;中间件是一个用来处理Django请求和响应的框架级钩子。它是一个轻量、低级别的插件系统，用于在全局范围内改变Django的输入和输出。每个中间件组件都负责做一些特定的功能。<br><br>
[返回目录](#目录)
<br><br>


### 11.列举django中间件的5个方法，以及django中间件的应用场景
`初级` `中间件`  `Django` <br>
- process_request : 请求进来时,权限认证
- process_view : 路由匹配之后,能够得到视图函数
- process_exception : 异常时执行
- process_template_responseprocess : 模板渲染时执行
- process_response : 请求有响应时执行

[返回目录](#目录)
<br><br>

### 12.简述Django对http请求的执行流程
`初级` `Django` <br><br>
&#8195;&#8195;在接受一个Http请求之前的准备,需启动一个支持WSGI网关协议的服务器监听端口等待外界的Http请求，比如Django自带的开发者服务器或者uWSGI服务器。
Django服务器根据WSGI协议指定相应的Handler来处理Http请求。此时服务器已处于监听状态，可以接受外界的Http请求,当一个http请求到达服务器的时候,Django服务器根据WSGI协议从Http请求中提取出必要的参数组成一个字典（environ）并传入Handler中进行处理。在Handler中对已经符合WSGI协议标准规定的http请求进行分析，比如加载Django提供的中间件，路由分配，调用路由匹配的视图等。最后返回一个可以被浏览器解析的符合Http协议的HttpResponse。

[返回目录](#目录)
<br><br>
### 13.Django中session的运行机制是什么
`初级` `Django` <br><br>
&#8195;&#8195;django的session存储可以利用中间件middleware来实现。需要在 `settings.py` 文件中注册APP、设置中间件用于启动。设置存储模式（数据库/缓存/混合存储）和配置数据库缓存用于存储，生成django_session表单用于读写。



[返回目录](#目录)
<br><br>
### 14. 什么是CSRF，请描述其攻击原理，在Django中如何解决
`初级` `Django` <br><br>
&#8195;&#8195;CSRF（cross-site request forgery）简称跨站请求伪造。例如，你访问了信任网站A,然后网站A会用保存你的个人信息并返回给你的浏览器一个cookie，然后呢，在cookie的过期时间之内，你去访问了恶意网站B，它给你返回一些恶意请求代码，要求你去访问网站A，而你的浏览器在收到这个恶意请求之后，在你不知情的情况下，会带上保存在本地浏览器的cookie信息去访问网站A，然后网站A误以为是用户本身的操作，导致来自恶意网站C的攻击代码会被执行：发邮件，发消息，修改你的密码，购物，转账，偷窥你的个人信息，导致私人信息泄漏和账户财产安全受到威胁。<br><br>
&#8195;&#8195;在post请求时，form表单或ajax里添加csrf_token，服务端开启CSRF中间件进行验证。<br><br>
&#8195;&#8195;解决原理是页面添加csrf_token值后，用户通过URL访问（GET请求）该页面时，Django会在响应中自动帮我们生成cookie信息，返回给浏览器，同时在前端代码会生成一个csrf_token值，然后当你POST提交信息时，Django会自动比对cookie里和前端form表单或ajax提交上来的csrf_token值，两者一致，说明是当前浏览器发起的正常请求并处理业务逻辑返回响应，那么第三方网站拿到你的cookie值为什么不能通过验证呢，因为他没你前端的那个随机生成的token值，他总不能跑到你电脑面前查看你的浏览器前端页面自动随机生成的token值吧。<br>
> 注意：你打开浏览器访问某个url（页面），默认是get请求，也就是说，你只要访问了url，对应的视图函数里只要不是if xx == post的逻辑就会执行，所以你打开页面，他会先生成cookie（token）值，返回给浏览器，然后你提交表单，或者发ajax请求时，会将浏览器的cookie信息（token值）发送给服务器进行token比对，这个过程相对于你发起了两次请求，第一次是get，第二次才是post，搞清楚这个，你才能明白csrf_token是怎么比对的。


[返回目录](#目录)
<br><br>
### 15. Django中CSRF的实现机制
`初级` `Django` <br>
1. django第1次响应来自某个客户端的请求时,服务器随机产生1个token值，把这个token保存在session态中;同时,服务器把这个token放到cookie中交给前端页面；
2. 该客户端再次发起请求时，把这个token值加入到请求数据或者头信息中,一起传给服务器；
3. 服务器校验前端请求带过来的token和session里的token是否一致。

[返回目录](#目录)
<br><br>
### 16.什么是跨域请求，其有哪些方式
`初级` `Django` <br>
- **跨域是指一个域下的文档或脚本试图去请求另一个域下的资源**。

方式如下：
1. 资源跳转： a链接、重定向、表单提交
2. 资源嵌入： link/script/img/frame/dom等标签，还有样式中background:url()、@font-face()等文件外链
3. 脚本请求： js发起的ajax请求、dom和js对象的跨域操作等

[返回目录](#目录)
<br><br>
### 17.跨域请求Django是如何处理的
`初级` `Django` <br><br>
使用第三方工具 **django-cors-headers** 即可彻底解决
- 注册app
- 添加中间件
- 配置运行跨域请求方法

[返回目录](#目录)
<br><br>
### 16.什么是信号量
`初级` `Django` <br><br>
&#8195;&#8195;Django包含一个"信号调度程序"，它有助于在框架中的其他位置发生操作时通知分离的应用程序。简而言之，信号允许某些发送者通知一组接收器已经发生了某些动作。当许多代码可能对同一事件感兴趣时，它们特别有用.

[返回目录](#目录)
<br><br>
### 17.web框架的本质是什么
`初级` `Django` <br>
- web框架本质是一个socket服务端，用户的浏览器是一个socket客户端。

[返回目录](#目录)
<br><br>

### 18.谈谈你对restful规范的认识
`初级` `Django` <br><br>
&#8195;&#8195;restful是一种软件架构设计风格，并不是标准，它只是提供了一组设计原则和约束条件，主要用于客户端和服务器交互类的软件。     就像设计模式一样，并不是一定要遵循这些原则，而是基于这个风格设计的软件可以更简洁，更有层次，我们可以根据开发的实际情况，做相应的改变。<br><br>
它里面提到了一些规范，例如
1. restful 提倡面向资源编程,在url接口中尽量要使用名词，不要使用动词
2. 在url接口中推荐使用Https协议，让网络接口更加安全                       
3. 在url中可以体现版本号         
4. url中可以体现是否是API接口           
5. url中可以添加条件去筛选匹配           
6. 可以根据Http不同的method，进行不同的资源操作             
7. 响应式应该设置状态码
8. 有返回值，而且格式为统一的json格式             
9. 返回错误信息           
10. 返回结果中要提供帮助链接，即API最好做到Hypermedia

[返回目录](#目录)
<br><br>

### 19.Django中如何加载初始化数据
`初级` `Django` <br><br>
&#8195;&#8195;Django在创建对象时在掉用save()方法后，ORM框架会把对象的属性转换为写入到数据库中，实现对数据库的初始化；通过操作对象，查询数据库，将查询集返回给视图函数，通过模板语言展现在前端页面。

[返回目录](#目录)
<br><br>
### 20.Django缓存系统类型有哪些
`初级` `Django` <br>
**1. 全站缓存，较少使用**
```python
MIDDLEWARE_CLASSES = (
    ‘django.middleware.cache.UpdateCacheMiddleware’,  # 第一
    'django.middleware.common.CommonMiddleware',
    ‘django.middleware.cache.FetchFromCacheMiddleware’,  # 最后
)
```
**2. 视图缓存，用户视图函数或视图类中**
```python
from django.views.decorators.cache import cache_page
import time

@cache_page(15) #超时时间为15秒
def index(request):
    t=time.time() #获取当前时间
    return render(request,"index.html",locals())
```
**3. 模板缓存，指缓存不经常变换的模板片段**
```html
{% load cache %}
    <h3 style="color: green">不缓存:-----{{ t }}</h3>

{% cache 2 'name' %} # 存的key
    <h3>缓存:-----:{{ t }}</h3>
{% endcache %}
```

[返回目录](#目录)
<br><br>
### 21.请简述Django下的（内建）缓存机制
`初级` `Django` <br><br>
&#8195;&#8195;Django根据设置的缓存方式，浏览器第一次请求时，cache会缓存单个变量或整个网页等内容到硬盘或者内存中，同时设置response头部，当浏览器再次发起请求时，附带f-Modified-Since请求时间到Django，Django发现f-Modified-Since会先去参数之后，会与缓存中的过期时间相比较，如果缓存时间比较新，则会重新请求数据，并缓存起来然后返回response给客户端，如果缓存没有过期，则直接从缓存中提取数据，返回给response给客户端。

[返回目录](#目录)
<br><br>

### 22.什么是ASGI，简述WSGI和ASGI的关系与区别
`初级` `Django` <br><br>
&#8195;&#8195;ASGI是异步网关协议接口，一个介于网络协议服务和Python应用之间的标准接口，能够处理多种通用的协议类型，包括HTTP，HTTP2和WebSocket。<br>
&#8195;&#8195;WSGI是基于HTTP协议模式的，不支持WebSocket，而ASGI的诞生则是为了解决Python常用的WSGI不支持当前Web开发中的一些新的协议标准。同时，ASGI对于WSGI原有的模式的支持和WebSocket的扩展，即ASGI是WSGI的扩展。

[返回目录](#目录)
<br><br>

### 23.Django如何实现websocket
`初级` `Django` <br><br>
&#8195;&#8195;django实现websocket使用channels。==channels通过http协议升级到websocket协议，保证实时通讯。== 也就是说，我们完全可以用channels实现我们的即时通讯。而不是使用长轮询和计时器方式来保证伪实时通讯。==他使用asgi协议而不是wsgi协议，他通过改造django框架，使django既支持http协议又支持websocket协议。==

[返回目录](#目录)
<br><br>

### 25.列举django的核心组件
`初级`  `Django` <br>
- 用于创建模型的对象关系映射；
- 为最终用户设计较好的管理界面；
- URL设计；
- 设计者友好的模板语言；
- 缓存系统。

[返回目录](#目录)
<br><br>

### 26.Django本身提供了runserver，为什么不能用来部署
`初级` `Django` <br>
1. runserver方法是调试 Django 时经常用到的运行方式，它使用Django自带的
WSGI Server 运行，==主要在测试和开发中使用，并且 runserver 开启的方式也是单进程。==
2. uWSGI是一个Web服务器，它实现了WSGI协议、uwsgi、http 等协议。注意uwsgi是一种通信协议，而uWSGI是实现uwsgi协议和WSGI协议的 Web 服务器。==uWSGI具有超快的性能、低内存占用和多app管理等优点，并且搭配着Nginx就是一个生产环境了，能够将用户访问请求与应用 app 隔离开，实现真正的部署 。== 相比来讲，支持的并发量更高，方便管理多进程，发挥多核的优势，提升性能。

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
### 02.urlpatterns中的name与namespace的区别
`初级` `Django` <br><br>
name:给路由起一个别名<br>
namespace:防止多个应用之间的路由重复

[返回目录](#目录)
<br><br>

### 03.Django路由系统中include是干嘛用的？
`初级` `Django` <br><br>
&#8195;&#8195;include用作路由转发，通常，我们会在每个app里，各自创建一个urls.py路由模块，然后从根路由出发，将app所属的url请求，全部转发到相应的urls.py模块中。

[返回目录](#目录)
<br><br>


### 04.Django2.x中的path与django1.x里面的URL有什么区别
`初级` `Django` <br><br>
&#8195;&#8195;path与url是两个不同的模块,效果都是响应返回页面, path调用的是python第三方模块或框架,而url则是自定义的模块。url默认支持正则表达式，而path不支持，正则表达式需要使用另外一个函数re_path。

```python
# django 2.x
django.urls path
# django 1.x
django.conf.urls url
```
[答案来源](https://www.lockv.com/python/django2-x%E4%B8%ADpath%E4%B8%8Edjango1-x%E4%B8%ADurl%E7%9A%84%E5%8C%BA%E5%88%AB%E5%8F%8A%E7%94%A8%E6%B3%95/)

[返回目录](#目录)
<br><br>

### 05.Django重定向的几种方法，用的什么状态码
`初级` `Django` <br>
- HttpResponse
- Redirect
- redirect 
- reverse
- 状态码：302,301

[返回目录](#目录)
<br><br>


## 模型层
### 01.命令migrate 和makemigrations的差别
`初级`  `Django` <br>
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

### 02.谈一谈你对ORM的理解
`初级`  `ORM` <br><br>
**ORM**是“对象-关系-映射”的简称。

&#8195;&#8195;ORM是MVC或者MVC框架中包括一个重要的部分，它实现了数据模型与数据库的解耦，即数据模型的设计不需要依赖于特定的数据库，通过简单的配置就可以轻松更换数据库，这极大的减轻了开发人员的工作量，不需要面对因数据库变更而导致的无效劳动。

### 14.如何使用Django ORM批量创建数据
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

### 15.列举django ORM中操作QuerySet对象的方法(至少5个)
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

### 16.ORM如何取消级联
`初级` `Django` <br><br>

[返回目录](#目录)
<br><br>
### 17.查询集的2大特性？什么是惰性执行
`初级` `Django` <br><br>

[返回目录](#目录)
<br><br>
### 18.查询集返回的列表过滤器有哪些
`初级` `Django` <br><br>

[返回目录](#目录)
<br><br>
### 19.selected_related与prefetch_related有什么区别
`初级` `Django` <br><br>

[返回目录](#目录)
<br><br>
### 20.values()与values_list()有什么区别
`初级` `Django` <br><br>

[返回目录](#目录)
<br><br>
### 21.QueryDict和dict区别
`初级` `Django` <br><br>

[返回目录](#目录)
<br><br>
### 22.Django中查询Q和F的区别
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

### .基于函数的视图和基于类的视图之间的区别？你更喜欢哪一个？为什么？


## 模板层
### 如何继承B模板中的A模板？(模板继承)。
`初级` `Django` <br><br>

[返回目录](#目录)
<br><br>



## 高阶
### 01.如何在Django中处理负载管理？
### 02.如何提高Django应用程序的性能？
### 03.Django如何实现高并发?
### 04.Django中当用户登录到A服务器进入登陆状态，下次被nginx代理到B服务器会出现什么影响
`初级` `Django` <br><br>
&#8195;&#8195;如果用户在A应用服务器登陆的session数据没有共享到B应用服务器，那么之前的登录状态就没有了。<br><br>
[返回目录](#目录)
<br><br>
### Tornado和Django区别

[返回目录](#目录)
<br><br>


# 数据库模块
## MySQL
### .NoSQL和SQL数据库之间有什么不同？请举例回答(提示：mysql和mongo db)。
### .如何确定需要哪些字段需要设置索引？
### .什么情况下需要设定字段属性为unique = True？
### .如何排查某个SQL语句的索引命中情况？
### .如何排查查询过慢的SQL语句？
### .mysql怎么处理高并发

[返回目录](#目录) 
<br><br>

# Redis模块
## 你了解的Redis的特点是什么？为什么会使用它？
## 支持的数据类型
## 如何合理的规划key？
## redis持久化，如果redis现需要重启，rdb模式下怎么在重启前保存数据
## 比如我需要把所有的文章和分类数据写入Redis，在Django中直接读取Redis拿到### 分类和文章的数据，问怎么规划数据存储，如何处理分页？
## 是否支持事务？举个例子。
## 有哪些数据淘汰策略？
## 当你发现有些Redis查询响应时间太长，如何排查？可能是什么引起的？
## 你用到的或者了解的Redis的部署结构是什么？
## 是否了解Redis的持久化策略，不同的策略有什么不同？
## 说说你了解的Redis主从同步的策略。

# 部署模块
## 01.什么是Nginx
`初级` `Nginx` <br><br>
&#8195;&#8195;Nginx是一个高性能代理服务，接收客户端发送过来的HTTP请求和websocket请求，响应静态文件请求和转发动态请求。
<br><br>[返回目录](#目录)
<br><br>
## 负载均衡什么意思
## 如何部署Django项目
## 为什么正式部署时不要开启DEBUG = True配置

# 常用算法模块
## Python中字典类型的实现算法
## 你了解的高级语言中的垃圾回收机制有哪些？Python中用的是什么？
## 介绍下你知道的缓存相关的算法
## 介绍下你知道的负载均衡相关的算法
## 介绍下数据库索引相关算法

[返回目录](#目录) 
<br><br>



# 其他模块 
## .介绍你项目的架构设计
[返回目录](#目录) 
<br><br>
## .Tornado的核是什么
`初级` `Django` <br><br>

# 云服务模块 
## .你使用过哪些云服务技术？
[返回目录](#目录)
<br><br>

