## 状态码

101 协议升级  用于websocket和HTTP2\(单链接多次请求，二进制，压缩头部，服务器推送\)

404 没有找到

502  网关错误

301 重定向

200 成功

401 未授权

403 拒绝访问

304 协商缓存

#### 缓存

##### 强制缓存：

expires 设置一个特定的时间  &lt;meta http-equiv="expires" content=""&gt;

cathe-control 设置一个具体的时间长度  优先 &lt;meta http-equiv="cathe-control" content="no-cathe"&gt;

##### 协商缓存：

etag:基于内容是否修改来判断  返回一个字符串 对比客户端字符串

last-modified：资源上次修改的时间 返回时间

