## 分布式系统一致性的需求和解决方案

### 一致性的分类和标准

#### 强一致 
只要是用户获得的值，永远都是最新且有效的。

#### 弱一致性
当数据被更改之后，系统不把保证一致性的重要性排在前面，用户获得的值可能是最新的也可能不是。

#### 最终一致性
最终一致性可以当作是弱一致性的加强版，可能用户获得的值不是最新的，但经过一段有限的时间后，系统不同分区的值会同步成最新。

### 解决方案

#### 二阶段提交协议

分布式系统有一个协调组件来维护信息同步，如果某一个分区进行了数据更新，这个分区会: 1. 通知协调组件自己的操作成功与否。2. 协调组件会协调其余分区做出正确的操作。这就是两阶段提交了。