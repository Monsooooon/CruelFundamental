B+树
- 矮胖，有效减少访问节点次数从而提高性能
- 只有叶子节点才存数据，非叶子节点是存储的指针；所有叶子节点构成一个有序链表；
- 使用双向链表串连所有叶子节点，区间查询效率更高
- 内部节点并没有指向关键字具体信息的指针，因此其内部节点相对 B 树更小
