- ## 单例模式  
	- 保证全局只有一个对象存在  
	- 最大的问题：初始化的时机  
		- 提前初始化  
		- 懒初始化 - 有并发访问的问题（涉及加锁）  
			- 双重检查锁注意事项：必须标记为 volatile  
				- 应该避免使用双重检查锁  
- ## 工厂模式  
	- #TODO  