## 什么是操作系统的宏内核和微内核？ 

内核是操作系统非常重要的组成部分，同时也是操作系统的核心。内核管理着系统资源，内核向上连接着应用程序，向下连接着硬件，它是应用程序和硬件的桥梁。

内核可以进一步的划分，分为宏内核和微内核。

宏内核和微内核最大的区别就是，宏内核的用户服务和内核服务都保存在相同的地址空间中，它们都由内核进行统一管理，而微内核的用户服务和内核服务会保存在不同的地址空间中

从内核大小上面来讲，微内核的尺寸更小，只包含用户进程相关的服务，而单核的尺寸要比微内核大的多，这点比较好理解，因为宏内核融入了太多服务和驱动。

从执行效率上来说，微内核的执行效率相对较慢，因为涉及到跨模块调用，而宏内核执行效率高，因为函数之间会直接调用。

在微内核模块化之后，它很容易扩展，因为内核空间与用户空间相互隔离，在用户态下（运行在用户空间中的应用程序）应用程序崩溃后一般不会影响到内核中的数据。宏内核的可拓展性较差。

## 微内核为什么更安全但是运行更慢？

微内核优势在于模块间解耦造成的逻辑清晰，易于维护。但模块间IPC通信造成了大量的性能下降