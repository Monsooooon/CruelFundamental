### Java: 知道双亲委派模型吗?有什么好处？

#### 双亲委派模型

【**三层架构的类加载器+双亲委派的类加载架构**】

三层架构类加载器：

- 启动类加载器：用来加载Java的核心类，是用原生代码来实现，不继承java.lang.ClassLoader。由于引导类加载器涉及到虚拟机本地具体实现，开发者无法直接获取到启动类加载器的引用，不允许直接通过引用操作。
- 扩展类加载器：负责加载JRE扩展目录。\lib\ext目录，或由java.ext.dirs系统属性指定的目中的JAR包的类。
- 应用程序类加载器：负责加载用户路径上的类库。
- 自定义加载器：可以自己加入自定义类加载器进行拓展。

双亲委派的类加载架构：

除了顶层的启动类加载器，其余的类加载器都有自己的父类加载器，类加载器不是以继承方式实现，而是通过组合关系来复用类加载器。

如果类加载器收到了类加载器请求，首先不会自己尝试加载这个类，而是将请求委派给父类加载器去完成，每个层次的类加载器都是这样，因此所有的加载请求都应该传递到最顶层的启动类加载器，只有当父类加载器反馈无法加载请求，子加载器才会尝试自己去完成加载。

#### 双亲委培模型的好处

Java中随着它的类加载器，具备了一种带有优先级的层次关系。

```
例如类java.lang.Object 放在rt.jar中，无论哪个类加载器要加载这个类，最终都是委派给这个模型最顶端的启动类加载器进行加载，因此Object在程序中的各种类加载器环境都能保证是同一个类。
反之，如果没有使用双亲委派模型，都由各个类加载器自己去加载，如果用户也编写了一个java.lang.Object类的话，并且放在程序的ClassPath中，那么系统会出现不同Object类，Java类型体系中最基础的行为也就无法保证，程序会变的很混乱，无法保证基础类的加载。
```
