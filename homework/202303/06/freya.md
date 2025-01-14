## HTTP/1.0，HTTP/1.1，HTTP/2，HTTP/3的区别

- 1.1相比于1.0，引入了长连接，TCP连接默认不关闭，可以复用；
支持管道（pipeline）网络传输，只要第一个请求发出去了，不必等其回来，就可以发第二个请求出去，可以减少整体的响应时间

- 2相比1.1，会压缩header（多个请求的头相同，会消除重复部分）；相比1.1的纯文本报文，2全面采用了二进制；2的连接可以并发多个请求（多路复用）

- 3将TCP更换为UDP，在UDP协议上开发QUIC协议


### QUIC 协议的特点：
- ⽆队头阻塞，QUIC 连接上的多个 Stream 之间并没有依赖，都是独⽴的，也不会有底层协议限制，某个流发
⽣丢包了，只会影响该流，其他流不受影响；

- 建⽴连接速度快，因为 QUIC 内部包含 TLS1.3，因此仅需 1 个 RTT 就可以「同时」完成建⽴连接与 TLS 密
钥协商，甚⾄在第⼆次连接的时候，应⽤数据包可以和 QUIC 握⼿信息（连接信息 + TLS 信息）⼀起发送，
达到 0-RTT 的效果。

- 连接迁移，QUIC 协议没有⽤四元组的⽅式来“绑定”连接，⽽是通过「连接 ID 」来标记通信的两个端点，客
户端和服务器可以各⾃选择⼀组 ID 来标记⾃⼰，因此即使移动设备的⽹络变化后，导致 IP 地址变化了，只
要仍保有上下⽂信息（⽐如连接 ID、TLS 密钥等），就可以“⽆缝”地复⽤原连接，消除᯿连的成本；