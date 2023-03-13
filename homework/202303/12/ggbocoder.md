在关闭连接时，四次挥手需要确保双方都已经停止发送数据，并且确认对方已经停止发送数据，才能安全地关闭连接。如果只使用三次挥手，可能会出现数据丢失或重复发送的情况。以下是使用三次挥手时可能出现的情况：

发送方向接收方发送 FIN 报文段，表示发送方已经停止发送数据，并要求接收方发送确认报文段。

接收方收到 FIN 报文段后，向发送方发送 ACK 报文段，表示已经收到了关闭连接的请求，并停止发送数据。

发送方收到 ACK 报文段后，认为对方已经停止发送数据，因此直接关闭连接。但是，由于网络延迟等原因，接收方可能还有一些未发送的数据需要传输。这样就可能会导致数据的丢失或者重复发送。

因此，为了确保数据的可靠传输，需要使用四次挥手来关闭连接。四次挥手可以确保双方都已经停止发送数据，并且确认对方已经停止发送数据，从而安全地关闭连接。