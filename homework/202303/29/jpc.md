# 四次挥手中收到乱序的FIN包会怎么处理
如果收到乱序的FIN报文，也就是FIN报文先到，关闭方并不会立马进入TIME_WAIT状态，而是首先将FIN报文放入到乱序队列中去。再收到包之后再去乱序队列中去查看是否有FIN包，是否能和当前报文顺序接上，如果能这时才进入TIME_WAIT状态
