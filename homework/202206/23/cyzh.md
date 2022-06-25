## 2022/06/23

### C++: 描述内存分配方式以及它们的区别。



#### 栈：

函数内除的局部变量的存储单位都会在栈上

#### 堆：

动态内存，程序运行时可以申请任意大小的内存

#### 自由存储区域：

程序在运行的时候利用`new`关键字申请的内存空间

#### 全局/静态存储区域：

存储全局变量和静态变量

#### 常量存储区：

存储常量字符串，程序结束后由系统释放



#### ref：

[C++ 中的内存分配和动态内存 | 从零开始的BLOG (hellozhaozheng.github.io)](https://hellozhaozheng.github.io/z_post/Cpp-内存分配和动态内存/#:~:text=描述 C%2B%2B 的内存分配方式以及它们之间的区别%3F 在 C%2B%2B 中%2C 内存区分为5个区%2C 分别是%3A,自由存储区%2C 全局%2F静态存储区%2C 常量存储区. 栈%3A 函数内的局部变量的存储单元都会在栈上创建%2C 函数执行结束时这些存储单元会被自动释放. 堆%3A 也称为动态内存.)

- Java: 知道new一个对象的过程吗?