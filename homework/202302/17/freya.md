redis的数据类型首先是五种基础的类型

- string：最常用来缓存数据，也可用来做计数器，或结合原子指令来做分布式锁
- list：存列表等数据，因为可以左右进出，也可以起到消息队列的功能
- set：存集合，有去重功能，因此可以多个集合做交并操作，例如发现共同好友等，也可以记录点赞关系
- zset：有序集合，可作排行榜
- hash：存储一个key的多个信息，例如用户(ID,name,phone)。

此外redis还有一些较新的数据类型
- HyperLogLog：可以大致计算有多少不重复的数据（有误差）
- GEO：存储地理信息
- bitmap：可以做布隆过滤器，判断数据不在集合中（能确定不在，但无法确定在）