## 2022/08/15

### 哈希索引和聚簇索引有什么区别？

#### 哈希索引

- 如果多个hash值相同，则采用链表存储

#### 聚簇索引

- 数据是分类放在一起的

- 查询显示一定范围数据的时候，由于数据都是紧密相连
- 数据库目前只有innodb数据引擎支持聚簇索引，而Myisam并不支持聚簇索引
- 每个表一般都是主键进行排序
