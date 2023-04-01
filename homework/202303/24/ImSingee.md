严格意义上不可以，因为 TLS 是在 TCP 之下的，需要建立好 TCP 连接后才能进行 TLS 握手。
但是，为了降低 TLS 的开销，一个聪明的手段是利用 TCP 的握手信息传递数据：TLS 1.3 引入了 0-RTT 模式就是将 TLS 的握手信息融入了 TCP 中，在 TCP 握手成功之时 TLS 也握手成功了
0-RTT 仅限于非首次连接，因为 0-RTT 依赖于 TCP 的 TCP Fast Open 和先前的密钥协商实现，这两个都要求之前已经建立过连接了。