# 集群脑裂数据丢失
## 产生原因
当主节点与其他节点断开连接，但是仍然和客户端保持连接。依然可以执行客户端发送过来的命令。此时哨兵会从其他节点中选出新的主节点。当旧的主节点恢复连接后就会被降级为从节点并且进行主从复制。那么那段时间客户端修改的数据就会丢失。
## 解决办法
设置两个参数：
1. 设置一个N，如果主节点连接数小于N，那么主节点就拒绝写数据。
2. 设置一个T，如果主从复制同步延迟大于T，那么主节点就会拒绝写数据。

这种解决办法只能尽量减少数据的丢失。