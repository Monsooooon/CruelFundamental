理论上32位系统的堆内存可以达到2^32字节，即4GB，但由于计算机不仅需要对内存条寻址，还需要对BIOS，其它硬件缓存寻址，实际对内存寻址不够4GB，大约3.25GB的样子，另外由于内核在每个进程的地址空间中都 必须存在，内核分配的内存也不能移动，通常还会内核分配约1G的内存，实际上堆最大可用约2G内存
