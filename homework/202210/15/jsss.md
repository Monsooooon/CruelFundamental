# https的创建连接的过程 为什么使用对称加密 对称加密和非对称加密的优缺点

先使用非对称加密传递对称加密的密钥, 这里使用TLS协议完成. 接着使用对称加密密钥来加密报文.

对称加密: 安全性相比非对称加密不高, 但是计算快.
非对称加密: 更加安全但是计算复杂度更高.
