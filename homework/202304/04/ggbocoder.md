上下文切换开销：进程切换或线程切换时，需要保存当前的上下文信息，包括CPU寄存器、程序计数器、堆栈指针等。这些信息需要保存到内存中，待恢复时再重新加载到CPU中。这个过程就需要进行上下文切换，它会占用一定的时间和系统资源。

内存管理开销：进程和线程之间切换时，需要切换虚拟地址空间。操作系统需要将旧的虚拟地址空间从MMU（内存管理单元）中移除，将新的虚拟地址空间添加进MMU中。这个过程需要进行页表切换、TLB（快速翻译缓冲区）清空等操作，也会消耗一定的时间。

缓存失效开销：虚拟地址空间切换后，CPU的缓存中可能存在旧地址空间的数据，此时需要进行缓存失效。当下一个进程/线程开始执行时，它需要重新加载数据到CPU缓存中，这也会带来一定的延迟和性能损失。