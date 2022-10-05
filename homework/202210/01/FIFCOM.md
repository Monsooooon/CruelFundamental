# 处理器的三级调度？

分为高级调度、中级调度和低级调度

#### 作业调度

高级调度又称为宏观调度、作业调度或者长程调度。

其主要任务是按照一定的原则从外存上处于后备状态的作业中选择一个或者多个，给它们分配内存、输入/输出设备等必要资源，并建立相应的进程，以使该作业具有获得竞争处理器的权利。

作业调度的运行频率较低，通常为几分钟一次。

#### 交换调度

中级调度又称为中程调度或者交换调度，引入**中级调度是为了提高内存利用率和系统吞吐量**。

其主要任务是按照给定的原则和策略，将处于外存对换区中的具备运行条件的进程调入内存，并将其状态修改为就绪状态，挂在就绪队列上等待；或者将处于内存中的暂时不能运行的进程交换到外存对换区，此时的进程状态称为挂起状态。

#### 进程调度

低级调度又称为微观调度、进程调度或者短程调度，其主要任务是按照某种策略和方法从就绪队列中选取一个进程，将处理器分配给它。

**进程调度的运行频率很高，一般隔几十毫秒要运行一次。**