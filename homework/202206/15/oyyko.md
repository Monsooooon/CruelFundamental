原子操作是如何实现的？

原子操作的底层实现
实现方式：基于缓存加锁与总线加锁。

1.总线加锁

所谓总线锁就是使用处理器提供的一个lock#信号，当一个处理器在总线上输出此信号时，其他处理器的请求会被阻塞住，那么该处理器可以独占共享内存。

但总线锁定把cpu和内存之间的通信锁住了，这使得锁定期间，其他处理器不能操作其他内存地址的数据，所以开销比较大。

2.缓存加锁

第二个机制是通过缓存锁定来保证原子性。在同一时刻，我们只需保证对某个内存地址的操作是原子性即可，但总线锁定把CPU和内存之间的通信锁住了，这使得锁定期间，其他处理器不能操作其他内存地址的数据，所以总线锁定的开销比较大，目前处理器在某些场合下使用缓存锁定代替总线锁定来进行优化。

频繁使用的内存会缓存在处理器的L1、L2和L3高速缓存里，那么原子操作就可以直接在处理器内部缓存中进行，并不需要声明总线锁，在Pentium 6和目前的处理器中可以使用“缓存锁定”的方式来实现复杂的原子性。所谓“缓存锁定”是指内存区域如果被缓存在处理器的缓存行中，并且在Lock操作期间被锁定，那么当它执行锁操作回写到内存时，处理器不在总线上声言LOCK＃信号，而是修改内部的内存地址，并允许它的缓存一致性机制来保证操作的原子性，因为缓存一致性机制会阻止同时修改由两个以上处理器缓存的内存区域数据，当其他处理器回写已被锁定的缓存行的数据时，会使缓存行无效，在如图2-3所示的例子中，当CPU1修改缓存行中的i时使用了缓存锁定，那么CPU2就不能同时缓存i的缓存行。
但是有两种情况下处理器不会使用缓存锁定。
第一种情况是：当操作的数据不能被缓存在处理器内部，或操作的数据跨多个缓存行（cache line）时，则处理器会调用总线锁定。
第二种情况是：有些处理器不支持缓存锁定。对于Intel 486和Pentium处理器，就算锁定的内存区域在处理器的缓存行中也会调用总线锁定。
针对以上两个机制，我们通过Intel处理器提供了很多Lock前缀的指令来实现。例如，位测试和修改指令：BTS、BTR、BTC；交换指令XADD、CMPXCHG，以及其他一些操作数和逻辑指令（如ADD、OR）等，被这些指令操作的内存区域就会加锁，导致其他处理器不能同时访问它。



在x86架构中，提供了指令前缀LOCK。LOCK保证了指令不会受其他处理器或cpu核的影响。在PentiumPro之前，LOCK的实现，是通过锁住bus（总线），从而阻止其他cpu核的内存访问。可想而知，这种实现是非常低效的。从PentiumPro开始，LOCK只会阻塞其他cpu核对相关内存的缓存块的访问。

现在，大多数的x86处理器都支持了CAS[[2\]](https://link.zhihu.com/?target=https%3A//en.wikipedia.org/wiki/Compare-and-swap)的硬件实现，保证了多处理器多核系统下的原子操作的正确性。CAS的实现同样无需锁住总线，只会阻塞其他cpu核对相关内存的缓存块的访问。同样的，在MIPS和ARM架构下，还支持了LL/SC的实现[[3\]](https://link.zhihu.com/?target=https%3A//en.wikipedia.org/wiki/Load-link/store-conditional)。LL/SC不会出现CAS中的ABA问题，而且基于LL/SC可以实现CAS FAA等原子操作。

在继续深入以前，需要了解MESI缓存协议[[4\]](https://link.zhihu.com/?target=https%3A//en.wikipedia.org/wiki/MESI_protocol)。当然，还存在其他的MESI变种，不过这里只会简单解释下MESI。每个cache line存在四种状态，Modified代表该cache line为该cpu核独有，且尚未写回（write back）到内存（对缓存一致性不了解的看这里[[5\]](https://link.zhihu.com/?target=https%3A//en.wikipedia.org/wiki/Cache_coherence)）。Exclusive代表该cache line为该cpu核独有，且与内存一致。Shared代表该cache line为多核共享，且与内存一致。Invalid代表缓存失效。处理器系统中多个处理器之间通过快速通道直接通信，比如intel家的QPI，amd家的Hypertransport。而处理器内多核直接通过共享的缓存比如L3总线进行通信。cpu核之间通信的消息包括读消息，以及读消息的响应消息。使无效消息，以及使无效消息的响应消息。当运行在某个cpu核的线程准备读取某个cache line的内容时，如果状态处于M,E,S，直接读取即可。如果状态处于I，则需要向其他cpu核广播读消息，在接受到其他cpu核的读响应后，更新cache line，并将状态设置为S。而当线程准备写入某个cache line时，如果处于M状态，直接写入。如果处于E状态，写入并将cache line状态改为M。如果处于S，则需要向其他cpu核广播使无效消息，并进入E状态，写入修改，后进入M状态。如果处于I，则需要向其他cpu核广播读消息核使无效消息，在收集到读响应后，更新cache line。在收集到使无效响应后，进入E状态，写入修改，后进入M状态。

从上面的说明可知，LOCK的实现，只需要保持cache line的M和E状态即可，此时就可以阻止其他cpu核对该块内存的修改，而不用去锁住整个总线。