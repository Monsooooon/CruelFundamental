### **OSI**七层模型

为了增强通⽤性和兼容性，计算机⽹络都被设计成层次机构，每⼀层都遵守⼀定的规则。因此有了OSI这样⼀个抽象的⽹络通信参考模型，按照这个标准使计算机⽹络系统可以互相连接

- 物理层

  通过⽹线、光缆等这种物理⽅式将电脑连接起来。传递的数据是⽐特流，0101010100。

- 数据链路层

  ⾸先，把⽐特流封装成数据帧的格式，对0、1进⾏分组。电脑连接起来之后，数据都经过⽹卡来传输，⽽⽹卡上定义了全世界唯⼀的MAC地址。然后再通过⼴播的形式向局域⽹内所有电脑发送数据，再根据数据中MAC地址和⾃身对⽐判断是否是发给⾃⼰的

- ⽹络层

  ⼴播的形式太低效，为了区分哪些MAC地址属于同⼀个⼦⽹，⽹络层定义了IP和⼦⽹掩码，通过对IP和⼦⽹掩码进⾏与运算就知道是否是同⼀个⼦⽹，再通过路由器和交换机进⾏传输。IP协议属于⽹络层的协议。

- 传输层

  有了⽹络层的MAC+IP地址之后，为了确定数据包是从哪个进程发送过来的，就需要端⼝号，通过端⼝来建⽴通信，⽐如TCP和UDP属于这⼀层的协议

- 会话层

  负责建⽴和断开连接

- 表示层

  为了使得数据能够被其他的计算机理解，再次将数据转换成另外⼀种格式，⽐如⽂字、视频、图⽚等。

- 应⽤层

  最⾼层，⾯对⽤户，提供计算机⽹络与最终呈现给⽤户的界⾯

### TCP/IP四层结构

-  数据链路层

  也有称作⽹络访问层、⽹络接⼝层。他包含了OSI模型的物理层和数据链路层，把电脑连接起来。

- ⽹络层

  也叫做IP层，处理IP数据包的传输、路由，建⽴主机间的通信

- 传输层

  为两台主机设备提供端到端的通信

- 应⽤层

  包含OSI的会话层、表示层和应⽤层，提供了⼀些常⽤的协议规范，⽐如FTP、SMPT、HTTP等。

## 区别

TCP/IP 协议中的应用层处理 OSI 模型中的第五层、第六层和第七层的功能。

TCP/IP 协议中的传输层并不能总是保证在传输层可靠地传输数据包，而 OSI 模型可以做到。TCP/IP 协议还提供一项名为 UDP（用户数据报协议）的选择。UDP 不能保证可靠的数据包传输。






