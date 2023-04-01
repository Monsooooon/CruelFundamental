TCP和UDP可以使用同一个端口号。在计算机网络中，端口号用于标识特定的网络服务或进程，TCP和UDP都需要使用端口号来建立连接或发送数据。每个端口号在特定的协议中只能被分配一次，但是不同的协议之间可以共享同一个端口号。

当TCP和UDP使用同一个端口号时，通常是由服务器程序决定如何解释接收到的数据包。例如，Web服务器通常会同时监听TCP的80端口和UDP的80端口，然后根据接收到的数据包的类型来区分用户请求的是Web页面还是视频流等内容。

需要注意的是，虽然TCP和UDP可以共享同一个端口号，但它们的工作方式和传输协议是完全不同的，因此，在使用同一个端口号时需要确保能够正确地处理不同协议的数据包