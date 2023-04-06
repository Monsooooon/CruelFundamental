虚拟地址空间切换会比较耗时，是因为它涉及到操作系统的内核态和用户态的切换。在一个进程执行的过程中，当需要切换到另一个进程时，操作系统会将当前进程的上下文信息（比如程序计数器、寄存器值、栈指针等）保存起来，并且加载新进程的上下文信息。

这个过程需要在内核态和用户态之间进行切换。在内核态下，操作系统可以直接访问硬件资源和进程的地址空间；而在用户态下，进程只能访问自己的虚拟地址空间，不能直接访问硬件资源。因此，每次虚拟地址空间切换都需要进行内核态和用户态的切换，这个切换的过程需要耗费一定的时间。

另外，在虚拟地址空间切换过程中，操作系统还需要完成一些额外的工作，如页表的切换、TLB（翻译后援：转换后备缓存）清空等，这些都会增加切换的时间。

因此，虚拟地址空间切换会比较耗时，特别是在频繁切换进程或线程的情况下，会严重影响系统的性能。