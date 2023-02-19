### TCP是怎么保证有序传输的

------

tcp主要是通过数据包头的序列号来保证数据的有序，即给到用户的数据一定是按照序列号顺序来的，对于缺失的数据会要求重传来补齐，并且不会跳序列号给到用户。



### 知不知道 time_wait状态，这个状态出现在什么地方，有什么用

------

time_wait出现在tcp连接中，主动关闭端发送完针对对端关闭请求的ack之后所进入的状态，这个状态的作用就是防止丢失对端未收到主动关闭端的ack包而发起的重传请求，一定程度上确保对端也能正常关闭。