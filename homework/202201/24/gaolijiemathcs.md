# 数据库的隔离级别和各个隔离级别下解决的问题

隔离级别是用于规定每个事务中做的修改，哪些级别在事务之间是可见的，哪些是不可见的。较低的隔离可以有更高的并发，系统开销更低。



- READ UNCOMMITTED（未提交读RU）：允许脏读，可能读取到其他会话中未提交的事务
  - 内容：未提交读级别，事务中的修改，即使没有提交，对其他事务也可见。
  - 分析：本级别会导致很多问题，但性能上不会比其他级别好，优点少，一般很少使用。
  - 存在的问题：存在脏读问题，事务可以读取未提交的数据。
- READ COMMITTED（已提交读RC）：只能读取到已提交的数据。Oracle等数据库默认级别。
  - 内容：大多数据库默认级别READ COMMITED(MySQL不是)。READ COMMITTED满足隔离性定义，一个事务开始的时候，只能看见已经提交的事务的修改。
  - 分析：（1）提交读级别，事务从开始到提交之前，对数据做的修改，对于其他事务是不可见的。（2）RC级别，数据读取不加锁，但是数据写入、删除、修改需要加锁。
  - 存在的问题：存在不可重复读问题(non-repeatable read)，两次执行同样的查询，可能会得到不一样的结果。事务B修改id=1数据内容提交之后，事务A在事务B提交前和提交后查询的结果不一样，就是不可重复读（重新读取产生的结果不一样）。
- REPEATABLE READ（可重复读RR）：同一个事务中的查询，都与事务开始前的查询保持一致。消除了不可重复读问题，但是存在幻读问题。
  - 内容：REPEATABLE READ保证在同一个事务中多次读取同样的记录结果保持一致，解决了脏读问题。
  - 分析：（1）可重复读仍无法解决幻读问题(Phantom Read)：幻读，指当某个事务在读取范围内的记录中，另外一个事务又在该范围内插入新的记录，当之前的事务再次读取该范围记录，会有多出的幻行(Phantom Row)。（2）InnDB和XtraDB存储引擎通过多版本并发控制(MVCC)解决幻行问题。（3）为MySQL默认的事务隔离级别。（4）当进行读的时候，可重读，意思就是在一个事务的多实例并发读取数据，可以看到同样的数据行。
  - 解决的问题：（1）解决不可重复读问题，支持可重读，当事务B修改id=1的字段内容，事务A在事务B提交前后各自读取一次，读到的数据完全相同。（2）原理：锁机制，RR中sql第一次读到数据，会将数据加行锁，其他事务无法修改数据，实现可重复读。但这只针对update和delete，因为行锁只会将设计到的字段行进行加锁操作，因此无法对insert的数据提交有影响。
  - 未解决的问题：幻读问题。行锁无法避免对insert的数据提交，因此出现当事务B执行insert操作时候，事务A在事务B之前读取了数据，事务B还是可以insert提交，这个时候事务A再读取，还是会多一条事务B操作insert增加的数据。幻读的解决需要通过可串行读SERIALIZABLE。
- SERIALIZABLE（可串行读）：完全串行化的读，解决幻读问题，但是每次读都要加表级别锁，读写阻塞。
  - SERIALIZABLE可串行化，最高隔离级别。通过强制事务串行执行，避免幻读问题。
  - 分析：（1）SERIALIZABLE会在读取的每一行数据都加锁，可能导致大量的超时和锁争用问题。（2）只有非常需要数据一致性和可以接受没有并发才能用这个级别。
  - 解决的问题：解决了幻读，读用读锁，写用写锁，读锁和写锁互斥，避免了幻读、不可重复读、脏读问题，但是会极大的降低数据库并发能力。



对于不可重复读和幻读，MySQL等数据库，出于性能的考虑，都使用了以乐观锁为基础的MVCC(多版本并发控制来避免)。