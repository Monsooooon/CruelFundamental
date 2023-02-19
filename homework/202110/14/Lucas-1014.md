# MVCC 原理
- https://mp.weixin.qq.com/s/xBTT9BD3l6lWSB6oRSF3sA

## 相关知识
- ACID
- Atomicity 原子性，要么没有，要么所有
- Consistency 一致性，事务前后数据一致
- Isolation 隔离性，两个事务互不干扰
- Durability 持久性，数据不能丢失

## 事务
- 脏读，读未提交
- 不可重复读，多次查询结果不一致
- 幻读，两次查询的结果集不一样

## 隔离级别
- 读未提交，最低，有脏读，重复读，幻读的问题
- 读已提交，解决脏读问题
- 可重复度，读数据时，不能修改，解决重复读，但是仍然可以插入？
- 串行化，最高，所有事务串行执行，避免所有并发问题，性能较差
- 加锁来实现隔离，MVCC 多版本控制，解决加锁后的性能问题

## 多版本控制
- 实现了读已提交，可重复读的隔离级别
- InnoDB 每行记录可能有三列
- trx_id, 操作该行数据的事务ID
- roll_pointer，指向回滚段的 undo 日志
- row_id, 如果没有主键和非NULL唯一键，单调递增的行ID