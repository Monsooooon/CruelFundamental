1. Redis 停止响应写请求：当 Redis 内存用完，Redis 将停止接收新的写请求，这意味着 Redis 将对所有写请求返回错误
2. 使用 LRU 策略来释放一些内存空间
4. 如果 Redis 内存满了，并且内存中的数据没有持久化到硬盘上，那么 Redis 将无法保存这些数据，因此可能会发生数据丢失
