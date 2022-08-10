
  
- 边缘触发和水平触发  
-  
- 水平触发 Level-Triggered  
	- 只要可读/写就会返回  
	- 描述的是监听的文件描述符的状态  
-  
- 边缘触发 Edge-Triggered  
	- 只有与上一次相比变化了才会返回（例如上次不可读这次可读了）  
	- 描述的是监听的文件描述符**变化**的状态  
	- 是 [[epoll]] 比 [[select]] 和 [[poll]] 优越的一大重点  
-  
- ## 推荐阅读  
	- [epoll 中的边缘触发](https://blog.singee.me/2021/07/04/721488b0985842389e634bc637b257cc/)  