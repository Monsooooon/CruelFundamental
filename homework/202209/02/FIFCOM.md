## 什么是管道？

管道（Pipeline）是一系列将标准输入输出链接起来的进程，其中每一个进程的输出被直接作为下一个进程的输入。

#### 使用管道通信，比进程1写入文件temp，进程2再从temp读取，有什么优点？

1. 临时文件存储在磁盘上，而管道存储在内存中，速度更快
2. 匿名管道(`|`)仅允许父子进程访问数据，比起文件更安全
3. 管道允许进程并行运行，即进程B可在接收到A的数据的同时处理数据。文件则需要等待进程A执行完毕