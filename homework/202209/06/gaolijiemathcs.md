## HTTP1.0， HTTP1.1和 HTTP2.0的区别

### HTTP 1.0

#### 1、无状态

- 无状态：服务器不跟踪不记录请求过的状态

#### 2、无连接

- 无连接：浏览器每次请求都需要建立tcp连接

HTTP1.0 规定浏览器和服务器保持短暂的连接，浏览器的每次请求都需要与服务器建立一个TCP连接，服务器处理完成后立即断开TCP连接（无连接），服务器不跟踪每个客户端也不记录过去的请求（无状态）。

#### 缺点

无状态的问题可以借助cookie/session来做身份认证和状态记录解决。

无连接特性将会导致以下性能缺陷：

（1）无法复用连接：每次发送请求都需要建立一次TCP连接，TCP连接释放又是比较费事的。无连接的特性会导致网络利用率较低。

（2）队头阻塞。由于HTTP 1.0 规定下一个请求必须在前一个请求响应到达之后才能发送。假设一个请求一直不到达，那么下一个请求就不发送，就导致阻塞后面的请求。



### HTTP 1.1

#### 1、长连接

- 长连接：HTTP 1.1 增加了一个Connection字段，通过设置Keep-alive 可以保持连接不断开，避免了每次客户端与服务器请求都要重复建立释放TCP连接，提高了网络的利用率。如果客户端想要关闭HTTP连接，可以在请求头中携带Connection：false 来告知服务器关闭请求。

#### 2、支持请求管道化

- 支持请求管道化（pipelining）：只要第一个请求发送出去，不用等待回来，就可以发送第二个请求，减少整体响应时间。



#### 缺点

但是还是有性能瓶颈：

（1）请求/响应头部(Header)未经过压缩就发送，首部信息越多延迟就越大，只能压缩Body部分。

（2）发送冗长的首部，每次互相发送相同的部首会造成的浪费很多。

（3）服务器也是按照请求的顺序响应，如果服务器响应慢，会导致客户端一直请求不到数据，也是队头阻塞。

（4）没有请求优先级控制

（5）请求只能从客户端开始，服务器只能被动响应。



### HTTP 2.0

HTTP 2.0 基于HTTPS，所以HTTP 2.0的安全性是有保障的。

HTTP 2.0 相比HTTP 1.1性能有改进的

#### 1、头部压缩

HTTP 2.0 会压缩头（Header）如果同时发送多个请求，头是一样的，或者是相似的。协议会消除重复的部分。

HPACK算法：在客户端和服务器端同时维护一张头信息表，所有的字段都会存入这个表，生成一个索引号，以后就不发送同样的字段，只发送索引号，来提高速度。

#### 2、二进制格式

HTTP 2.0 不会像HTTP 1.1 中存纯文本形式的报文，而是采用了二进制格式。

头信息和数据体都是二进制，统称为帧(frame)：头信息帧和数据帧。

二进制对人不友好，但是对计算机友好，计算机只懂二进制，收到而报文以后，无需将明文转换为二进制，而是直接解析二进制报文。增加数据传输效率。

#### 3、数据流

HTTP 2.0 数据包不是按顺序发送的，同一个连接里面连续的数据包，可能属于不同的回应。因此，必须要对数据包做标记，指出属于哪个回应。

每个请求或者回应的所有数据包，称为一个数据流（Stream）。

每个数据流都标记一个独一无二的编号，其中规定客户端发出的数据流编号为奇数，服务器发出的数据流编号为偶数。

客户端还**可以指定数据流的优先级。**优先级高的请求，服务器就先相应该请求。

#### 4、多路复用

HTTP 2.0 是可以在**一个连接中并发多个请求或者回应 而不用按照顺序一一对应。**

移除了HTTP 1.1 中的串行请求，不需要排队等待，不会出现队头阻塞。降低了延迟，提高连接利用率。

TCP连接中，服务器接收到客户端A和B的两个请求，如果发现A处理的过程非常耗时，于是回应A请求已经处理好的部分。接着回应B请，完成以后，再回应A请求剩下的部分。

#### 5、服务器推送

HTTP 2.0 在一定程度改善了传统的【请求-应答】工作模式，服务不再是被动的响应，而是可以主动向客户端发送消息。

在浏览器请求HTML可以提前将可能会用到的JS、CSS文件等静态资源主动发送给客户端，减少延时的等待，服务器推送。



### HTTP 3.0

#### 1、将下层的TCP协议改为UDP 解决丢包阻塞问题

HTTP 2.0问题：多个HTTP请求在复用一个TCP连接，下层的TCP协议是不知道有多少个HTTP请求的。

一旦发生丢包现象，就会触发TCP的重传机制，在**一个TCP连接中的所有HTTP请求都必须等待这个丢的包被重传回来。**

- HTTP 1.1 中的管道(pipeline)：传输中如果有一个请求阻塞了，队列请求也被阻塞。
- HTTP 2.0 多路复用一个TCP连接，一旦发生丢包，就会阻塞住所有HTTP请求。

HTTP 3.0 将HTTP下层TCP协议改成了UDP

UDP发送是不管顺序也不管丢包，因此不会出现HTTP 1.1 队头阻塞，HTTP 2.0 一个丢包全部重传。

UDP不可靠传输，基于UDP的QUIC协议可以实现类似TCP协议的可靠性传输。

- QUIC有自己的一套机制可以保证传输的可靠性。当某个流发生丢包，只会阻塞这个流，其他流不会受到影响。
- TL3升级为最新的1.3版本，头部压缩算法也升级为QPack
- HTTPS要建立一个连接需要6次交互，先3次握手，然后TLS/1.3 3次握手 密钥协商，QUIC直接将TCP和TLS 1.3 6次交互合并为3次。减少交换次数。

QUIC一个建立在UDP上的伪TCP+TLS+HTTP 2.0的多路复用协议



ref:https://mp.weixin.qq.com/s/amOya0M00LwpL5kCS96Y6w