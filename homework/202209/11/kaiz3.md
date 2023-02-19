SYN
TCP三次握手中，如果A是发起端，则A就对服务器发一个SYN报文。表示建立连接。

ACK
收到数据或请求后发送响应时发送ACK报文。

RST
表示连接重置

FIN
TCP四次挥手时，表示关闭连接
上面四种老朋友了，比较熟悉，看下面比较冷门的两个标志位。

PSH
发送端需要发送一段数据，这个数据需要接收端一收到就进行向上交付。而接收端在收到PSH标志位有效的数据时，迅速将数据交付给应用层。所以PSH又叫急迫比特。

URG
URG成为紧急指针，意为URG位有效的数据包，是一个紧急需要处理的数据包，需要接收端在接收到之后迅速处理。
区别：
首先，PSH与URG的相似之处在于二者所在的数据包都是急需接收端处理的报文。
不同之处在于PSH位有效时，当前的数据还会被发送到接收端的缓冲区，并刷新缓冲区，将当前缓冲区中所有数据都交付给上一层——应用层。
PSH位就是用来通告接收方立即将收到的报文连同TCP接收缓存里的数据递交应用进程处理，一般会出现在发送方封装最后一个应用字段的TCP报文中，针对TCP交互式应用,则只要封装有应用字段的TCP报文，均会将PSH位置1。当然，应用程序的开发者，可以根据需要，在某个应用功能模块或某个应用操作中,将所有封装应用字段的TCP报文PSH位置1，以提高交互双方的处理效率,这在理论上应该也是可行的。
URG位有效的数据包也是在当前报文需要接收端立即处理，但是当前报文不需要经过接收端的缓冲区，直接越过缓冲区，交付往接收端的应用层