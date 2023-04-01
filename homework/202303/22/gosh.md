在TIME_WAIT状态的TCP连接收到SYN会发生什么？

要看SYN的序列号和时间戳是否合法

合法SYN：客户端SYN序列号比服务端期望下一个收到的序列号大 and SYN时间戳比服务端最后收到的报文的时间戳大
非法SYN：客户端SYN序列号比服务端期望下一个收到的序列号小 or SYN时间戳比服务端最后收到的报文的时间戳小

收到合法SYN：重用此四元组连接，跳过2MSL而转变为SYN_RECV状态，接着就能进行建立连接过程。
收到非法SYN：再回复一个第四次挥手的ACK报文，客户端收到后，发现不是自己期望收到的ACK num，就回RST给服务端。