### 最左匹配原则的原理是什么

------

最左匹配表现出来是使用联合索引，如果SQL中使用了联合索引中最左边的几个，SQL会走联合索引去进行匹配。例如有(a, b, c)索引 [a] [a, b]  [a, b, c]都会走到索引。但是遇到范围查询，between,like等就会停下来。联合索引还可以与覆盖索引搭配。

原理：联合索引会建一个联合索引的B+树，形如(a,b,c)联合索引的 b+ 树，其中的非叶子节点存储的是第一个关键字的索引 a，而叶子节点存储的是三个关键字的数据。这里可以看出 a 是有序的，而 b，c 都是无序的。但是当在 a 相同的时候，b 是有序的，b 相同的时候，c 又是有序的。以此类推。

联合索引确定了前一个最左值 才能确定下一个值。

ref:https://cloud.tencent.com/developer/article/1774781