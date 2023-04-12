# 什么是临界区，如何解决冲突
每个进程中访问临界资源的那段程序称为临界区，一次仅允许一个进程使用的资源称为临界资源。

解决冲突的办法：

* 如果有若干进程要求进入空闲的临界区，一次仅允许一个进程进入，如已有进程进入自己的临界区，则其它所有试图进入临界区的进程必须等待；
* 进入临界区的进程要在有限时间内退出。
* 如果进程不能进入自己的临界区，则应让出CPU，避免进程出现“忙等”现象。