# What are the different levels of abstraction in the DBMS?

数据库的三级模式

- 外模式: 外模式又称子模式或用户模式，对应于用户级。它是某个或某几个用户所看到的数据库的数据视图，是与某一应用有关的数据的逻辑表示。外模式是从模式导出的一个子集，包含模式中允许特定用户使用的那部分数据
- 模式: 概念模式又称模式或逻辑模式，对应于概念级。它是由数据库设计者综合所有用户的数据，按照统一的观点构造的全局逻辑结构，是对数据库中全部数据的逻辑结构和特征的总体描述，是所有用户的公共数据视图(全局视图)。它是由数据库管理系统提供的数据模式描述语言(Data Description Language，DDL)来描述、定义的。概念模式反映了数据库系统的整体观。
- 内模式: 内模式又称存储模式，对应于物理级。它是数据库中全体数据的内部表示或底层描述，是数据库最低一级的逻辑描述，它描述了数据在存储介质上的存储方式和物理结构，对应着实际存储在外存储介质上的数据库。

## 参考

[Link](https://baike.baidu.com/item/%E6%95%B0%E6%8D%AE%E5%BA%93%E4%B8%89%E7%BA%A7%E6%A8%A1%E5%BC%8F/8143441?fr=aladdin)