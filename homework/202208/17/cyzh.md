## 2022/08/17

### innodb引擎索引实现结构，为什么B+树而不是B树？

- B+树空间利用效率更高，可以减少I/O
- B+树增删下更快
- B+树的查询效率更加稳定