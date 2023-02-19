### ping 能访问到一个端口是否支持tcp连接吗，udp呢？

并不是每次打包都是从应用层往下每一层都打包一个包头。ping虽然是应用层协议，但是不会从应用层给传输层打上TCP或UDP包装，再给IP封装。ping用的是网络层的ICMP协议，直接打上IP包头。

因此不经过传输层，不需要支持tcp/udp连接。因此ICMP没有传输层的端口号，也没有具体的端口。