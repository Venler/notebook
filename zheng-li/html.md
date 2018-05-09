## HTML5

#### 标签：

&lt;header&gt;、&lt;footer&gt;、&lt;nav&gt;、&lt;acticle&gt;、&lt;section&gt;、&lt;vedio&gt;、&lt;audio&gt;、&lt;canvas&gt;

#### 特性：

localstorage 最多5M左右 永久存储

sessionstorage 最多5M左右 页面窗口关闭就没有了 \(cookie存储4K左右\)

地理位置 navigator.geolocation.getcurrentpositon

应用程序缓存：manifest [http://www.jb51.net/html5/438218.html](http://www.jb51.net/html5/438218.html)

简单来说manifest能让你的应用在无网的情况下也能访问。

&lt;htmlmanifest="demo.appcache"&gt;

CACHE MANIFEST -在此标题下列出的文件将在首次下载后进行缓存

NETWORK -在此标题下列出的文件需要与服务器的连接，且不会被缓存

FALLBACK -在此标题下列出的文件规定当页面无法访问时的回退页面（比如 404 页面）

#### 

svg与canvas对比

svg：绘制矢量图形，不受分辨率影响，内嵌于HTML中，可当做普通DOM进行操作，可添加事件处理，适合做地图

canvas：使用JS来绘制图形，逐像素进行渲染，适合游戏领域

#### 

PWA

[https://blog.csdn.net/qq\_19238139/article/details/77531191](https://blog.csdn.net/qq_19238139/article/details/77531191)

