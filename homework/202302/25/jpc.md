# 常见的缓存更新策略
* 旁路缓存策略
    * 写策略：更新数据库中的数据，删除缓存中的数据。
    * 读策略：如果读取的数据命中了缓存，则直接返回数据。如果读取的数据没有命中缓存，则从数据库中读取数据，然后将数据写入到缓存，并且返回给用户。
* 读穿写穿策略
    * 读穿：客户端请求数据，如果缓存中存在就直接返回，如果不存在就由缓存组件去数据库请求数据，并且写入缓存，然后再返回给客户端。
    * 写穿：如果缓存中数据已经存在，则更新缓存中的数据，并且由缓存同步更新到数据库中。如果缓存中数据不存在，直接更新数据库，然后返回。
* 写回策略
    * 更新数据的时候，只更新缓存，并且将这个数据标记为脏的，对于数据库的更新会通过批量异步的方式更新。
