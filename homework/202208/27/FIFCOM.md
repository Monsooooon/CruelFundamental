## 什么是CAP原理，什么是FLP不可能定理？

#### CAP Theorem

CAP原理指对于一个分布式系统来说，不可能同时满足这三点：

1. 一致性 Consistency: 所有节点的数据相同
2. 可用性 Availability: 不保证获取到的数据最新，但每次请求获取到的响应都非错
3. 分区容错性 Partition tolerance: 即便网络分区故障导致子系统之间通信错误，数据处理系统也能继续处理数据。(**系统中的网络可能发生分区故障（成为多个子网，甚至出现节点上线和下线），即节点之间的通信无法保障。而网络故障不应该影响到系统正常服务。**)

#### FLP Theorem

FLP不可能定理指：在网络有延迟但不丢失(网络可靠)的异步网络中，如果至少有一个节点可能出现故障，则没有任何共识算法能够解决一致性问题

> [CS6213 - FLP Theorem](https://ilyasergey.net/CS6213/week-03-bft.html#flp-theorem)