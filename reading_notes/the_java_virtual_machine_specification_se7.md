# Java 虚拟机规范(Java SE7版)
#### The Java Virtual Machine Specification SE7

### 第 1 章 引言
* Java 语言是一门通用的、面向对象的、支持并发的程序语言。
* Java 虚拟机是整个 Java 平台的基石,是 Java 技术用以实现硬件无关与操作系统无关的关键部分,是 Java 语言生成出极小体积的编译代码的运行平台,是保障用户机器免于恶意代码损害 的保护屏障。
* Java 虚拟机与 Java 语言并没有必然的联系,它只与特定的二进制文件格式——Class 文件 格式所关联,Class 文件中包含了 Java 虚拟机指令集(或者称为字节码、Bytecodes)和符号 表,还有一些其他辅助信息。
* 基于安全方面的考虑,Java 虚拟机要求在 Class 文件中使用了许多强制性的语法和结构化 约束,但任一门功能性语言都可以表示为一个能被 Java 虚拟机接收的有效的 Class 文件。作为 一个通用的、机器无关的执行平台,任何其他语言的实现者都可以将 Java 虚拟机作为他们语言的 产品交付媒介。

### 第 2 章 Java 虚拟机结构

* 编译后被 Java 虚拟机所执行的代码使用了一种平台中立(不依赖于特定硬件及操作系统的) 的二进制格式来表示,并且经常(但并非绝对)以文件的形式存储,因此这种格式被称为 Class 文件格式。Class 文件格式中精确地定义了类与接口的表示形式,包括在平台相关的目标文件格 式中一些细节上的惯例1,例如字节序(Byte Ordering)等。
* Java 虚拟机可以操作的数据类型可分为两类:原始类 型(Primitive Types,也经常翻译为原生类型或者基本类型)和引用类型(Reference Types)。
* Java 虚拟机是直接支持对象的
* 虚拟机中使用 reference 类型来表示对某个对象的引用,reference 类型的 值读者可以想象成类似于一个指向对象的指针。每一个对象都可能存在多个指向它的引用,对象的 操作、传递和检查都通过引用它的 reference 类型的数据进行操作。
* Java 虚拟机所支持的原始数据类型包括了数值类型(Numeric Types)、布尔类型(Boolean Type §2.3.4)和 returnAddress 类型(§2.3.3)三类。其中数值类型又分为整型类型 (Integral Types,§2.3.1)和浮点类型(Floating-Point Types,§2.3.2)两种
* int 类型:值为 32 位有符号二进制补码整数,默认值为零。
* double 类型:取值范围是双精度浮点数集合中的元素,或者(如果虚拟机支持的话)是 双精度扩展指数(Double-Extended-Exponent)集合中的元素。默认值为正数零。
* boolean 类型:取值范围为布尔值 true 和 false,默认值为 false。
* returnAddress 类型:表示一条字节码指令的操作码(Opcode)。在所有的虚拟机支持的原始类型之中,只有 returnAddress 类型是不能直接 Java 语言的数据类型对应 起来的。
* 对于一个非零的、可数的任意浮点值,都可以表示为 s×m×2<sup>(e-N+1)</sup>的形式,其中 s 可以是 +1 或者-1,m 是一个小于 2N 的正整数,e 是一个介于 Emin=-(2<sup>K-1</sup>-2)和 Emax=2<sup>K-1</sup>-1 之间的整 数(包括 Emin 和 Emax)。这里的 N 和 K 两个参数的取值范围决定于当前采用的浮点数值集合。
* 所有 Java 虚拟机的实现都必须支持两种标准的浮点数值集合:单精度浮点数集合和双精度浮 点数集合。另外,Java 虚拟机实现可以自由选择是否要支持单精度扩展指数集合和双精度扩展指 数集合,也可以选择支持其中的一种或全部。这些扩展指数集合可能在某些特定情况下代替标准浮 点数集合来表示 float 和 double 类型的数值。
* 上述四种数值集合都不仅包含可数的非零值,还包括五个特殊的数值:正数零、负数零、正无 穷大、负无穷大和 NaN。
* returnAddress 类型会被 Java 虚拟机的 jsr、ret 和 jsr_w 指令所使用。
* 这几条指令以前主要被使用来实现 finally 语句块,后来改为冗余 finally 块代码的方式来实 现,甚至到了 JDK7 时,虚拟机已不允许 Class 文件内出现这几条指令。那相应地,returnAddress 类型就处 于名存实亡的状态。
*  Java 虚拟机定义了 boolean 这种数据类型,但是只对它提供了非常有限的支持。在 Java 虚拟机中没有任何供 boolean 值专用的字节码指令,在 Java 语言之中涉及到 boolean 类型值的运算,在编译之后都使用 Java 虚拟机中的 int 数据类型来代替。
*  Java 虚拟机直接支持 boolean 类型的数组,虚拟机的 newarray 指令可以创建这种数组。boolean 的数组类型的访问与修改共用 byte 类型数组的 baload 和 bastore 指令。
*  在 Oracle 公司的虚拟机实现里,Java 语言里面的 boolean 数组将会被编码成 Java 虚拟机的 byte 数 组,每个 boolean 元素占 8 位长度。
*  Java虚拟机中有三种引用类型:类类型(Class Types)、数组类型(Array Types)和 接口类型(Interface Types)。

