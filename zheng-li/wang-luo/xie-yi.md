物理层：通过媒介传输比特，确定机械及电气规范（比特bit）中继器、集线器

数据链路层：将比特组装层帧和点到点的传递（帧frame）交换机 网卡 网桥

网络层：负责数据包从源到宿的传递和网际互联（包packet） IP协议

传输层：提供端到端的可靠报文传递和错误恢复（段segment） TCP/UDP协议

会话层：建立、管理和终止会话

表示层：对数据进行翻译、加密和压缩

应用层：允许访问OSI环境的手段 HTTP/HTTPS/FTP

## TCP/IP协议族

链路层：ARP,RARP

网络层：ICMP，IP，IGMP

传输层：TCP，UDP

应用层：HTTP，FTP，DNS等

## ARP协议

### 定义

**地址解析协议（Rddress Resolution Rrotocol）是根据IP地址获取物理地址的TCP/IP协议**

### 过程

第一步：A在本机ARP缓存中查找B的的匹配的MAC地址。

第二步：如果没找到，A则广播带上自己的IP地址和MAC地址发送ARP请求帧到本地网络的所有主机，其他主机收到广播，如果发现和自己的地址不匹配则丢弃。

第三步：主机B确定ARP请求中的IP地址与自己的IP地址匹配，则将主机A的IP地址和MAC地址映射添加到本地ARP缓存中。

第四步：主机B将包含其MAC地址的ARP回复消息直接发送回主机A。

第五步：当主机A收到从主机B发来的ARP回复消息时，会用主机B的IP和MAC地址映射更新ARP缓存。本机缓存是有生存期的，生存期结束后，将再次重复上面的过程。主机B的MAC地址一旦确定，主机A就能向主机B发送IP通信了。

## ICMP

ICMP是（Internet Control Message Protocol）Internet控制[报文](https://baike.baidu.com/item/报文)协议。它是[TCP/IP协议族](https://baike.baidu.com/item/TCP%2FIP协议族)的一个子协议，用于在IP[主机](https://baike.baidu.com/item/主机)、[路由](https://baike.baidu.com/item/路由)器之间传递控制消息。控制消息是指[网络通](https://baike.baidu.com/item/网络通)不通、[主机](https://baike.baidu.com/item/主机)是否可达、[路由](https://baike.baidu.com/item/路由)是否可用等网络本身的消息。这些控制消息虽然并不传输用户数据，但是对于用户数据的传递起着重要的作用。通过IP协议发送

#### PING命令

发：

1.生成固定格式的ICMP数据包

2.将包和目标IP地址一起传送给IP协议

3.IP协议将该地址作为目标地址构建IP数据包，并将通过ARP协议查找到的本地映射表上的对应的MAC地址一起传送给数据链路层

4.数据链路层构建数据帧，并将本机MAC地址设为源地址，该地址为目标MAC地址，并附加控制信息传送出去

收：

## HTTP

超文本传输协议

特点：**无连接**（每次连接只能处理一个请求，处理完后断开）、**无状态**（对事务处理无记忆能力）

**步骤：**

1.浏览器解析URL，本地DNS缓存或者请求DNS服务器

2.根据IP地址和默认端口80建立TCP连接

3.浏览器发出HTTP请求，在TCP第三次握手的时候发送给服务器

4.服务器做出响应，将数据或者资源返回给客户端

5.释放TCP连接

6.浏览器处理资源或者数据

消息结构：

请求：请求行、请求头、空行、请求体

返回：状态行、返回头、空行、返回体

[https://www.cnblogs.com/master-song/p/8820244.html](https://www.cnblogs.com/master-song/p/8820244.html)

## TCP

TCP为了保证不发生丢包，就给每个包一个序号，同时序号也保证了传送到接收端实体的包的按序接收。然后接收端实体对已成功收到的包发回一个相应的确认（ACK）；如果发送端实体在合理的往返时延（[RTT](https://baike.baidu.com/item/RTT)）内未收到确认，那么对应的数据包就被假设为已丢失将会被进行重传。TCP用一个校验和函数来检验数据是否有错误；在发送和接收时都要计算校验和。

[https://blog.csdn.net/qq\_34328833/article/details/60468358](https://blog.csdn.net/qq_34328833/article/details/60468358)

## IP

[https://blog.csdn.net/super\_yc/article/details/72290931](https://blog.csdn.net/super_yc/article/details/72290931)

## 状态码

101 协议升级  用于websocket和HTTP2\(单链接多次请求，二进制，压缩头部，服务器推送\)

404 没有找到

502  网关错误

301 重定向

200 成功

401 未授权

403 拒绝访问

304 协商缓存

## HTTP2

[https://www.zhihu.com/question/34074946](https://www.zhihu.com/question/34074946)

## websocket

[http://www.ruanyifeng.com/blog/2017/05/websocket.html](http://www.ruanyifeng.com/blog/2017/05/websocket.html)

#### 缓存

##### 强制缓存：

expires 设置一个特定的时间  &lt;meta http-equiv="expires" content=""&gt;

cathe-control 设置一个具体的时间长度  优先 &lt;meta http-equiv="cathe-control" content="no-cathe"&gt;

##### 协商缓存：

etag:基于内容是否修改来判断  返回一个字符串 对比客户端字符串

last-modified：资源上次修改的时间 返回时间

