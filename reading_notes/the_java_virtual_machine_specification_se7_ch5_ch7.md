# Java 虚拟机规范 (Java SE 7 版)Ch5_Ch7
#### The Java Virtual Machine Specification SE7

### 第 5 章 加载、链接与初始化
* Java 虚拟机动态地加载、链接与初始化类和接口。
* 加载是根据特定名称查找类或接口类型的 二进制表示(Binary Representation),并由此二进制表示创建类或接口的过程。
* 链接是为 了让类或接口可以被 Java 虚拟机执行,而将类或接口并入虚拟机运行时状态的过程。
* 类或接口的 初始化是指执行类或接口的初始化方法`<clinit>`(§2.9)。
* 5.1 运行时常量池
* 
