# 为什么虚拟地址空间切换比较耗时
由于每个进程都有自己的虚拟地址空间，那么显然每个进程都有自己的页表，那么当进程切换后页表也要进行切换，页表切换后 TLB 就失效了，Cache 失效导致命中率降低，那么虚拟地址转换为物理地址就会变慢，表现出来的就是程序运行会变慢，而线程切换则不会导致 TLB 失效，因为线程无需切换地址空间，因此线程切换要比较进程切换块。
