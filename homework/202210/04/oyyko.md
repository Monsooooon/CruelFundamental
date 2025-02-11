## HDLC简介

HDLC（High-level Data Link Control，高级数据链路控制）是一种面向比特的链路层协议，其最大特点是对任何一种比特流，均可以实现透明的传输。

​       HDLC协议只支持点到点链路，不支持点到多点。

​       HDLC不支持IP地址协商，不支持认证。协议内部通过Keepalive报文来检测链路状态。

​       HDLC协议只能封装在同步链路上，如果是同异步串口的话，只有当同异步串口工作在同步模式下才可以应用HDLC协议。目前应用的接口为：工作在同步模式下的Serial接口和POS接口等。

## HDLC的帧类型和帧格式

HDLC有信息帧（I帧）、监控帧（S帧）和无编号帧（U帧）3种不同类型的帧。

​       信息帧用于传送有效信息或数据，通常简称为I帧。

​       监控帧用于差错控制和流量控制，通常称为S帧。

​       无编号帧用于提供对链路的建立、拆除以及多种控制功能，简称U帧。

HDLC帧由标志、地址、控制、信息和帧校验序列等字段组成。

​       标志字段为0111110，标志一个HDLC帧的开始和结束，所有的帧必须以F开头，并以F结束；在邻近两帧之间的F，即作为前面帧的结束，又作为后续帧的开头；

​       地址字段是8比特，用于标识接收或发送HDLC帧的地址；

​       控制字段是8比特，用来实现HDLC协议的各种控制信息，并标识是否是数据；

​       信息字段可以是任意的二进制比特串，长度未作限定，其上限由FCS字段或通讯节点的缓冲容量来决定，目前国际上用得较多的是1000-2000比特，而下限可以是0，即无信息字段。但是监控帧中不可有信息字段。

​       帧检验序列字段可以使用16位CRC，对两个标志字段之间的整个帧的内容进行校验。



HDLC协议使用统一的帧格式，运用方便；采用零比特插入法，易于硬件实现，且支持任意的位流传输，实现信息的透明传输；[全双工通信](https://baike.baidu.com/item/全双工通信/8752822?fromModule=lemma_inlink)，[吞吐率](https://baike.baidu.com/item/吞吐率/1555673?fromModule=lemma_inlink)高，在未收到应答帧的情况下，可连续发送信息帧，提高数据链路传输的效率；采用CRC帧校验序列，可防止漏帧，提高信息传输的可靠性。 [4] 

主要有四个特点：

1·对于任何一种比特流都可透明传输。

2·较高的数据链路传输效率。

3·所有的帧都有[帧校验序列](https://baike.baidu.com/item/帧校验序列/6818718?fromModule=lemma_inlink)（[FCS](https://baike.baidu.com/item/FCS/22504028?fromModule=lemma_inlink)），传输可靠性高。

4·用统一的帧格式来实现传输。

 