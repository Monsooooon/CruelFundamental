用LT的话附带的代码写起来会比较简单,不容易有bug,ET模式的代价就是增加了网络层的逻辑处理复杂度，必须保证时刻知道fd当前的状态(为什么呢TODO)ET的要求是需要一直读写，直到返回EAGAIN，否则会遗漏事件,
对于EPOLLOUT事件适合用ET,也就是fd可写事件(缓存满的时候要再等这个事件),如果用LT会需要开关各一次此事件(否则只要fd可写,每次epoll_wait,可写事件会立刻触发),所以EPOLLOUT事件更适合ET模式所以,
像nginx这样作为高性能服务器的,网络上传下载量大,很可能缓冲区被频繁写满,也就是会经常需要等待EPOLLOUT事件,于是就适合用ET;而Redis使用的是水平触发.而LT可以保证代码简单
