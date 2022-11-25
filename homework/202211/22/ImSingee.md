- 利用某些特别构造的 payload，让程序执行到第三方写入的代码  
-  
- 解决方案思路  
	- 操作系统层面  
		- 禁止一个页同时可写 + 可执行  
		- 地址随机化（ASLR）  
	- 换用内存安全的语言  
	- C：避免使用不进行缓冲区检查的函数、开启编译器缓冲区检查、  
