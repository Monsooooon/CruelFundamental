讲讲拥塞控制

拥塞控制与网络的拥堵情况相关联 流量控制与接收方的缓存状态相关联

网络堵塞时，A重新发送数据包，导致网络更加堵塞

A一次性连续发送多少个数据：拥塞窗口

一次发送1，2，3，4... / 1，2，4，8个数据

slow start threshold: (ssthresh) 分割两种增长方法，来找到瓶颈值（MAX）

达到瓶颈值后，把ssthresh调小，调为MAX的一半