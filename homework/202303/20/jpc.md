# TCP和UDP可以使用同一个端口吗？

TCP/UDP 各自的端口号相互独立，互不影响。

TCP 和 UDP 传输协议，在内核中是由两个完全独立的软件模块实现的。

当主机收到数据包后，可以在 IP 包头的协议号字段知道该数据包是 TCP/UDP，所以可以根据这个信息确定送给哪个模块（TCP/UDP）处理，送给 TCP/UDP 模块的报文根据端口号确定送给哪个应用程序处理。

