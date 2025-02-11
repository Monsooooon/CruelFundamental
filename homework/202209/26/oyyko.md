**触发器原理：
**      触发器与存储过程非常相似，触发器也是SQL语句集，两者唯一的区别是触发器不能用EXECUTE语句调用，而是在用户执行Transact-SQL语句时自动触发（激活）执行。触发器是在一个修改了指定表中的数据时执行的存储过程。通常通过创建触发器来强制实现不同表中的逻辑相关数据的引用完整性和一致性。由于用户不能绕过触发器，所以可以用它来强制实施复杂的业务规则，以确保数据的完整性。触发器不同于存储过程，触发器主要是通过事件执行触发而被执行的，而存储过程可以通过存储过程名称名字而直接调用。当对某一表进行诸如UPDATE、INSERT、DELETE这些操作时，SQLSERVER就会自动执行触发器所定义的SQL语句，从而确保对数据的处理必须符合这些SQL语句所定义的规则。
触发器的作用：
触发器的主要作用是其能够实现由主键和外键所不能保证的复杂的参照完整性和数据的一致性。它能够对数据库中的相关表进行级联修改，强制比CHECK约束更复杂的数据完整性，并自定义操作消息，维护非规范化数据以及比较数据修改前后的状态。与CHECK约束不同，触发器可以引用其它表中的列。在下列情况下使用触发器实现复杂的引用完整性；强制数据间的完整性。创建多行触发器，当插入，更新、删除多行数据时，必须编写一个处理多行数据的触发器。执行级联更新或级联删除这样的动作。级联修改数据库中所有相关表。撤销或者回滚违反引用完整性的操作，防止非法修改数据。
**触发器与存储过程的区别：**
     触发器与存储过程的主要区别在于触发器的运行方式。存储过程必须有用户、应用程序或者触发器来显示的调用并执行，而触发器是当特定时间出现的时候，自动执行或者激活的，与连接用数据库中的用户、或者应用程序无关。当一行被插入、更新或者删除时触发器才执行，同时还取决于触发器是怎样创建的，当UPDATE发生时使用一个更新触发器，当INSERT发生时使用一个插入触发器，当DELETE发生时使用一个删除触发器



Mysql的触发器相当于内部处理的一些过程，不带入和带出任何的参数。
其内部使用的参数就是新旧两条记录old和new的字段。
用于完成数据表之间的触发操作，来保证数据库的一致性、完整性。
Mysql的存储过程是类似于其它编程语言中的函数的功能。
存储过程内部可以使用顺序循环和转移三种基本程序结构，而且整个存储过程可以接受和返回参数。