### epoll的两种触发模式？

* 水平触发： 有文件描述符就绪时，通知读写，如果仍然有就绪没有读写，接着触发通知
* 边沿触发： 有文件描述符就绪时，通知读写，如果仍然有就绪没有读写，不触发通知，仅仅在就绪状态改变时通知