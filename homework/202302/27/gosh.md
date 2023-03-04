Redis 管道有什么用？

Redis 客户端与服务器之间使用TCP协议进行通信
在某些高并发场景下，网络开销成了Redis速度的瓶颈，所以需要使用管道技术来实现突破

管道技术
客户端可以一次发送多条命令，不用逐条等待命令的返回值，而是到最后一起读取返回结果，这样只需要一次网络开销，速度明显提升。

Redis中，如果客户端使用管道发送了多条命令，那么服务器就会将多条命令放入一个队列中，会消耗一定的内存
管道中命令的数量不是越大越好，太大容易爆内存

除了减少网络延迟开销，管道也会提升Redis服务器每秒操作总数。

read() 和 write() 系统调用会花费很多时间，因为需要操作系统从用户态切换到内核态，中间涉及到上下文切换
使用管道，多个命令只会进行一次read() 和 write()系统调用。