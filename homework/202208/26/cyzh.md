## 2022/08/26

### 什么是lamport logical clock?

逻辑时钟是计算机之间相对的时间，由于物理时间又误差，所以无法用物理时间来准确确定事件事件的顺序。Lamport提出逻辑时钟就是为了解决分布式系统中的时序问题，即如何定义A事件发生早于B事件。

- 只有两个事件之间发生过信息传递，才可以得到两个事件之间的因果关系
- 事件之间的时间具有偏序关系