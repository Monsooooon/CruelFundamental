## constructor 和 destructor 能virtual么

1. 对于构造函数而言，如果当前类含有虚函数的话，其第一步操作是将内存的首地址填充当前类的虚函数表地址，然后执行接下来的构造。所以如果构造函数是虚函数的话，需要通过虚函数表指针才能找到构造函数的地址，但虚函数表指针又是构造函数填充的。这就是鸡生蛋蛋生鸡的问题了。所以构造函数不能是虚函数。

2. 对于析构函数，如果当前类存在子类，则最好是把析构函数声明为虚函数。这是因为如果用积累指针指向类子类，那么在析构的时候，很有可能造成子类的空间发生泄漏。

```c++
class Bass;
class Derived : public Base {};

Base* p = new Derived{};

delete p; // 如果Base的析构函数不是virtual的话，会造成子类的空间没有正确析构

```