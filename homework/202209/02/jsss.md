# 什么是管道？使用管道通信，进程1写入文件temp，进程2再从temp读取，有什么优点？

管道是进程间通信的方式之一, 分为命名管道和匿名管道. 其提供了单向通信机制.

进程1写入文件temp，进程2再从temp读取. 使用管道文件来进行进程间通信, 内核维护一块缓冲区来进行通信.
