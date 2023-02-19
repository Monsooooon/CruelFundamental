# 什么是 TIME_WAIT 状态，为什么需要 TIME_WAIT 状态？时间是多久，为什么？

是TCP断连的4次挥手的第4次挥手到连接彻底关闭时的等待时间。  
需要它的原因是为了防止服务端没收到最后一次挥手，如果超过了这个等待时间，客户端就重发最后一次挥手。  
它的时长是2MSL，也就是一个来回的时间，如果超过这个来回还没收到，就表明消息大概率丢失了，需要重发。