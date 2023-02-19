管道通信（PIPE）

管道通信方式的中间介质是文件，通常称这种文件为管道文件。两个进程利用管道文件进行通信时，一个

进程为写进程，另一个进程为读进程。写进程通过写端（发送端）往管道文件中写入信息；读进程通过读

端（接收端）从管道文件中读取信息。两个进程协调不断地进行写、读，便会构成双方通过管道传递信息

的流水线。

利用系统调用PIPE（）创建一个无名管道文件，通常称为无名管道或PIPE；利用系统调用MKNOD（）创建

一个有名管道文件，通常称为有名管道或FIFO。

PIPE是一种非永久性的管道通信机构，当它访问的进程全部终止时，它也将随之被撤消；它也不能用于不

同族系的进程之间的通信。而FIFO是一种永久的管道通信机构，它可以弥补PIPE的不足。

管道文件被创建后，便可对它进行读写操作，通过系统调用WRITE（）和READ（）来实现。通信完毕后，

可将管道文件关闭，用CLOSE（）来实现。

消息通信（MESSAGE）

消息通信方式以消息缓冲区为中间介质，通信双方的发送和接收操作均以消息为单位。在存储器中，消息

缓冲区被组织成队列，通常称之为消息队列。

创建消息队列用系统调用MSGGET（）来实现，这一步工作也被称为消息队列的初始化。在进行通信时，消

息队列的发送和接收分别用系统调用MSGSND（）和MSGRCV（）来实现。在需要改变队列的使用权限及其它

一些特性时，用MSGCTL（）来实现。