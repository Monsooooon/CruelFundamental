Q: 程序从加载到运行,会发生什么
A: 
预编译阶段,编译阶段,优化阶段,汇编阶段,链接阶段
从加载到运行主要是链接阶段,分位静态链接和动态链接
静态链接将链接库的代码复制到可执行程序中,使可执行文件变大
动态链接将代码放到共享对象中,通过虚地址映射的方式调用