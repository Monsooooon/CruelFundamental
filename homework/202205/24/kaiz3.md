进程间的通信方式:

1.管道(pipe)： 是一种半双工的通信方式，数据只能单向流动，而且只能在具有亲缘关系的进程间使用。进程的亲缘关系通常是指父子进程关系。没有名字并且大小受限，传输的是无格式的流，所以两进程通信时必须约定好数据通信的格式。管道它就像一个特殊的文件，但这个文件只存在于内存中，在创建管道时，系统为管道分配了一个页面作为数据缓冲区，进程对这个数据缓冲区进行读写，以此来完成通信。其中一个进程只能读一个只能写，所以叫半双工通信，为什么一个只能读一个只能写呢?因为写进程是在缓冲区的末尾写入，读进程是在缓冲区的头部读取，他们各自的数据结构不同，所以功能不同。

2.有名管道(named pipe)： 有名管道也是半双工的通信方式，但是它允许无亲缘关系进程间的通信。它提供了一个路径名与之关联，有了自己的传输格式。有名管道和管道的不同之处还有一点是,有名管道是个设备文件，存储在文件系统中(名字存在于文件系统中，内容存放在内存中)，没有亲缘关系的进程也可以访问，但是它要按照先进先出的原则读取数据,不支持lseek之类的文件定位操作。

3.信号(signal)： 信号是在软件层次上对中断机制的一种模拟，用于通知接收进程某个事件已经发生。在原理上，一个进程收到一个信号与处理器收到一个中断请求可以说是一样的。信号是异步的，一个进程不必通过任何操作来等待信号的到达，事实上，进程也不知道信号到底什么时候到达。信号是进程间通信机制中唯一的异步通信机制，可以看作是异步通知，通知接收信号的进程有哪些事情发生了。信号机制经过POSIX实时扩展后，功能更加强大，除了基本通知功能外，还可以传递附加信息。信号事件的发生有两个来源：硬件来源(比如我们按下了键盘或者其它硬件故障)；软件来源。信号分为可靠信号和不可靠信号，实时信号和非实时信号。进程有三种方式响应信号1.忽略信号2.捕捉信号3.执行缺省操作。

4. 消息队列(message queue)： 是存放在内核中的消息链表，每个消息队列由消息队列标识符标识。消息队列克服了信号传递信息少、管道只能承载无格式字节流以及缓冲区大小受限等缺点。与管道不同的是，消息队列存放在内核中，只有在内核重启(系统重启)时才能删除一个消息队列，同样消息队列的大小也是受限制的。

5.信号量(semophore)： 是一个计数器，常用来处理进程或线程同步的问题，用来控制多个进程对共享资源的访问。它常作为一种锁机制，防止某进程正在访问共享资源时，其他进程也访问该资源。特别是对临界资源的访问同步问题。临界资源：为某一时刻只能由一个进程或线程操作的资源，当信号量的值大于或等于0时，表示可以供并发进程访问的临界资源数，当小于0时，表示正在等待使用临界资源的进程数。更重要的是，信号量的值仅能由PV操作来改变。

6.共享内存(shared memory)： 就是分配一块能被其他进程访问的内存。共享内存可以说是最有用的进程间通信方式，也是最快的IPC形式。它往往与其他通信机制(如信号量)配合使用。首先说下在使用共享内存区前，必须通过系统函数将其附加到进程的地址空间或说为映射到进程空间。两个不同进程A、B共享内存的意思是，同一块物理内存被映射到进程A、B各自的进程地址空间。进程A可以即时看到进程B对共享内存中数据的更新，反之亦然。由于多个进程共享同一块内存区域，必然需要某种同步机制，互斥锁和信号量都可以。采用共享内存通信的一个显而易见的好处是效率高，因为进程可以直接读写内存，而不需要任何数据的拷贝。对于像管道和消息队列等通信方式，则需要在内核和用户空间进行四次的数据拷贝，而共享内存则只拷贝两次数据[1]：一次从输入文件到共享内存区，另一次从共享内存区到输出文件。实际上，进程之间在共享内存时，并不总是读写少量数据后就解除映射，有新的通信时，再重新建立共享内存区域。而是保持共享区域，直到通信完毕为止，这样，数据内容一直保存在共享内存中，并没有写回文件。共享内存中的内容往往是在解除映射时才写回文件的。因此，采用共享内存的通信方式效率是非常高的。

7. 套接字(socket)