# SQL vs NoSQL
- https://acecodeinterview.com/sql_vs_nosql/

## SQL 优点
- 接近实际，易于理解
- 高一致性
- 实体之间可以联合查询

## SQL 缺点
- 读写慢，不支持高并发
- 表结构改动成本大
- 水平扩展难， TODO

## NoSQL 优点
- 横向扩展
- 数据复制和分区
- 高可用性
- 反规范化，提高查询效率
- 丰富的存储格式
- 设计简单

## NoSQL 缺点
- 一致性差
- 不支持JOIN

## Question
- 能不能请教一个问题，关系型数据库，数据库水平分片，怎么实现JOIN啊，谢谢了
- table1 id (1-1,000,000) 在服务器A上
- table1 id (1,000,001-2,000,000) 在服务器B上
- table2 id (1-1,000,000) 在服务器C上
- table2 id (1,000,001-2,000,000) 在服务器D上