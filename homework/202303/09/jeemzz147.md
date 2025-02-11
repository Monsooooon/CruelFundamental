### QUIC的流量控制和拥塞控制

流量控制

QUIC 并没有引入TCP那样的滑动窗口的概念，而是采用一种“限额(limit-base)”流控方案，接收方在一个特定的流上或者整个连接上，给出一个自己能够处理的最大字节数。发送方发送的数据不能超过这两个（流和连接）“限额”。若是达到“限额”，就需要阻塞等待发送方增加限额的命令。
所以QUIC中有两个级别的数据流控制：

基于流的流控，它通过限制可以在单个流上可发送的数据量来防止单个流消耗整个连接的接收缓区。

基于连接的流控，它通过限制所有流上通过STREAM帧发送的流数据的总字节数来防止发送方超出接收方的连接缓冲区容量。

发送方不得（MUST NOT）发送超过任一限制的数据。
