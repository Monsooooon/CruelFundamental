## 用了TCP协议，数据一定不会丢失吗

TCP只保证传输层的消息可靠性，但不保证应用层的消息可靠性。对于下层的数据丢失，TCP可以不久，而上层则不行