## epoll的两种触发模式？

epoll的两种触发模式包括水平模式(level trigger)和边缘模式(edge trigger)

1. LT: 是epoll的默认操作模式，只要有消息还未读取完成，就一直触发时间
2. ET: 消息到来时触发一次事件，通知应用程序立即处理，后续不再检测这种事件。效率较高