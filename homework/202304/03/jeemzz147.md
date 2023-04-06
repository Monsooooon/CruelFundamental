### 进程与线程的切换流程

上下文保存：当操作系统需要切换到另一个进程或线程时，需要先保存当前进程或线程的上下文信息，包括程序计数器、寄存器状态、内存状态等，以便于下次恢复。

资源回收：操作系统需要回收当前进程或线程占用的资源，如内存、CPU时间片等，以便于分配给其他进程或线程使用。

调度决策：操作系统需要根据一定的调度算法，选择下一个要执行的进程或线程，并为其分配资源。

上下文恢复：操作系统需要将上下文信息恢复到下一个进程或线程中，使其能够从上次执行的地方继续执行。

进程/线程切换完成：此时操作系统已经完成了进程/线程的切换，下一个进程或线程开始执行，上一个进程或线程被暂停。