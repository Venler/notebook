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

ICMP是（Internet Control Message Protocol）Internet控制[报文](https://baike.baidu.com/item/报文)协议。它是[TCP/IP协议族](https://baike.baidu.com/item/TCP%2FIP协议族)的一个子协议，用于在IP[主机](https://baike.baidu.com/item/主机)、[路由](https://baike.baidu.com/item/路由)器之间传递控制消息。控制消息是指[网络通](https://baike.baidu.com/item/网络通)不通、[主机](https://baike.baidu.com/item/主机)是否可达、[路由](https://baike.baidu.com/item/路由)是否可用等网络本身的消息。这些控制消息虽然并不传输用户数据，但是对于用户数据的传递起着重要的作用。

