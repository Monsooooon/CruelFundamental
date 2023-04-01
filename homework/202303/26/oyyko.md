如果没有这个accept方法，TCP连接还能建立起来吗？

就算不执行accept()方法，三次握手照常进行，并顺利建立连接。

全连接队列（ACCEPT队列），在服务端收到第三次握手后，会将半连接队列的sock取出，放到全连接队列中。队列里的sock都处于 ESTABLISHED状态。这里面的连接，就等着服务端执行accept()后被取出了。

建立连接的过程中根本不需要accept() 参与， 执行accept()只是为了从全连接队列里取出一条连接。