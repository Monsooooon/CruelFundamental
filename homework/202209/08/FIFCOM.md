## UDP传输数据的最大容量？为什么？

#### 局域网环境下，建议将UDP数据控制在1472字节以下

以太网(Ethernet)数据帧的长度必须在46-1500字节之间,这是由以太网的物理特性决定的，这个1500字节被称为链路层的MTU(最大传输单元)。 但这并不是指链路层的长度被限制在1500字节，其实这这个MTU指的是链路层的数据区，并不包括链路层的首部和尾部的18个字节。

所以，事实上这个1500字节就是网络层IP数据报的长度限制。因为IP数据报的首部为20字节，所以IP数据报的数据区长度最大为1480字节。而这个1480字节就是用来放TCP传来的TCP报文段或UDP传来的UDP数据报的。

又因为UDP数据报的首部8字节，所以UDP数据报的数据区最大长度为1472字节。这个1472字节就是我们可以使用的字节数

#### Internet编程时，建议将UDP数据控制在548字节以下

ipv4协议规定ip层的最小重组缓冲区大小为576！所以，建议udp包不要超过这个大小，而不是因为internet的标准MTU是576！

