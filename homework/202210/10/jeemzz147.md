### go 协程如何实现

1个协程绑定 1 个线程，这种最容易实现。协程的调度都由 CPU 完成了，缺点是 协程的创建、删除和切换的代价都由 CPU 完成，对CPU消耗很大，略显昂贵。
N个协程绑定1个线程，优点就是协程在用户态线程即完成切换，不会陷入到内核态，这种切换非常的轻量快速。但也有很大的缺点，某个程序用不了硬件的多核加速能力；一旦某协程阻塞，造成线程阻塞，本进程的其他协程都无法执行了，根本就没有并发的能力了。
因此，Go选择了 M 个协程绑定 N 个线程，是 N:1 和 1:1 类型的结合，克服了以上 2 种模型的缺点。协程跟线程是有区别的，线程由 CPU 调度是抢占式的，协程由用户态调度是协作式的，一个协程让出 CPU 后，才执行下一个协程。

