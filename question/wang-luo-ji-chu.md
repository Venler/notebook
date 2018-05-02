## ARP协议

地址解析协议（Rddress Resolution Rrotocol）是根据**IP地址获取物理地址**的TCP/IP协议

1 A在本机ARP缓存中查找B的的匹配的MAC地址

2 如果没找到，A则广播带上自己的IP地址和MAC地址发送ARP请求帧到本地网络的所有主机，其他主机收到广播，如果发现和自己的地址不匹配则丢弃



