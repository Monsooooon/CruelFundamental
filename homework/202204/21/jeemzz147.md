### 知道UDP是不可靠传输，如果设计一个基于UDP差不多可靠的算法，如何设计？

TCP VS UDP

Tcp 是面向连接提供可靠传输 ； UDP是面向无连接，提供不可靠连接

Tcp 提供流量控制 ； UDP不提供流量控制

Tcp 保证传输数据顺序 ； UDP不保证传输顺序，也就是可能是乱序收包

TCP 面向字节流 ； UDP 面向数据包


#### 设计一个基于udp的可靠连接算法

针对数据完整性 –> 加上一个16或者32位的CRC验证字段

针对乱序 –> 加上一个数据包序列号SEQ

针对丢包 –> 需要确认和重传机制，就是和Tcp类似的Ack机制

针对协议字段 –> protol 字段，标识当前使用协议