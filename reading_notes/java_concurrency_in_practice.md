# Java 并发编程实践

## Java Concurrency in Practice

## Chapter 1 简介

* 多程序产生原因：提高资源利用率，公平性，便利性
* 线程是轻量级进程
* 线程优势：多处理器，建模简单，异步事件响应，用户界面反应灵敏
* 线程风险：安全性，活跃性，性能问题

## Chapter 2 线程安全性

* 正确使用线程和锁
* 线程安全代码的核心是对状态访问操作进行管理，特别是对共享的（Shared）和可变的（Mutable）状态的访问 
* 线程安全最核心的是正确性。
* 原子性
  * 竞态条件 因为不恰当的执行条件而出现不正确的结果
  * 复合操作
* 加锁机制
  * 内置锁（Intrinsic Lock）或监视器锁（Monitor Lock） 相当于一种互斥锁。线程进入同步代码会自动获得锁，离开会自动释放锁。
  * 重入 这意味着获取锁的操作粒度是“线程”而不是“调用”。Java中同一线程可以重入自己持有的内置锁，不然可能会死锁，如递归调用的时候。pthread互斥体的粒度是“调用”。
* 用锁保护状态
  * 只有在写入共享变量时才需要使用同步是错误的。
  * 每个共享的和可变的变量都应该只由一个锁来保护。
  * 包含多个变量的不变性条件，涉及的所有变量都需要由同一个锁来保护。
* 活跃性和性能
  * 简单性和性能之间存在制约，但是不能盲目为了性能而牺牲简单性，因为可能会破坏安全性。
  * 执行长时间的计算或者操作的时候，不要持有锁。

## Chapter 3 对象的共享

* 关键字synchronized 一方面可以用于实现原子性或者确定“临界区（Critical Section）”，另一个重要的方面在于内存可见性（Memory Visibility）。
* 安全发布
* 可见性
  * 为了确保多个线程之间对内存的写入操作的可见性，必须使用同步。
  * 失效数据
  * 非原子的64位操作
  * 最低安全性（out-of-thin-airsafety）适用于绝大多数变量 
  * Java内存模型要求，变量的读写操作都必须是原子操作，但对于非volatile类型的long和double变量，JVM允许将64位的读操作或者写操作分解为两个32位操作。
  * 加锁的含义不仅仅局限于互斥行为，还包括内存可见
* Volatile变量
  * 是一种弱同步机制
  * 读取volatile变量时总会返回最新写入的值。
  * 访问volatile变量不会执行加锁操作
  * 加锁机制既可以确保可见性，又可以确保原子性，而volatile变量只能确保可见性。
* 发布与逸出
  * “发布（Publish）”一个对象的意思是指，使对象能够在当前作用域之外的代码中使用。
  * 当某个不应该发布的对象被发布时，这种情况就被称为逸出（Escape）。
  * 不要在构造过程中使用this引用逸出。
* 线程封闭
* 仅在单线程里访问数据，就不需要同步
* Ad-hoc线程封闭
  * 维护线程封闭性职责完全由程序实现来承担。
  * 很脆弱，尽量少用
* 栈封闭
  * 栈封闭是线程封闭的一种特例，在栈封闭中，只能通过局部变量才能访问对象。（编者按：栈封闭简单说就是放在函数里且不会发布的局部变量）
* ThreadLocal类
  * 提供了get和set等访问接口的方法，这些方法为每个使用该变量的线程都存有一份独立的副本，因此get总能返回由当前线程在调用set时设置的最新值。
  * ThreadLocal变量类似于全局变量，它能降低代码的可重用性，并在类之间引入隐含的耦合性，因此在使用时要格外小心。
* 不变性
  * 不可变对象一定是线程安全的。
  * 不可变对象满足以下条件：
    * 对象创建后不可修改；
    * 对象的所有域都是final类型；
    * 对象是正确创建的（对象创建期间，this引用没有逸出）。
  * Final域 final类型的域是不能修改的，但是如果final域所引用的对象是可变的，这些被引用的对象是可以修改的。
* 安全发布
  * 不正确的发布：正确的对象被破坏
    * 没有同步可见性，会导致多线程读时产生无效值
  * 不可变对象与初始化安全性
    * 任何线程都可以在不需要额外同步的情况下安全访问不可变对象，即使在发布这些对象时没有使用同步。
  * 安全发布的常用模式
    * 安全的发布对象，对象的引用以及对象的状态必须同时对其他线程可见。
    * 在静态初始化函数中初始化一个对象引用。
    * 将对象的引用保存到volatile类型的域或者AtomicReferance对象中
    * 将对象的引用保存到某个正确构造对象的final类型域中
    * 将对象的引用保存到一个由锁保护的域中。
  * 事实不可变对象（Effectively Immutable Object）
    * 在没有额外同步的情况下，任何线程都可以安全地使用被安全发布的事实不可变对象。
  * 可变对象 要安全地共享可变对象，这些对象就必须被安全地发布，并且必须是线程安全的或者由某个锁保护起来。
  * 安全地共享对象 当发布一个对象时必须明确地说明对象的访问方式。
    * 并发程序中使用和共享对象时，可以使用的实用策略
      * 线程封闭
      * 只读共享
      * 线程安全共享
      * 保护对象
* 对象的发布需求取决于它的可变性
  * 不可变对象可以通过任意机制来发布。
  * 事实不可变对象必须通过安全方式来发布。
  * 可变对象必须通过安全方式来发布，并且必须是线程安全的或者由某个锁保护起来。

## Chapter 4 对象的组合

## Chapter 7 取消与关闭

* Java没有提供任何机制来安全地终止线程。但它提供了中断（Interruption），这是一种协作机制，能够使一个线程终止另一个线程的当前工作。
* 7.1 任务取消
  * 如果外部代码能在某个操作正常完成前将其置入“完成”状态，那这个操作就可称为可取消的（Cancellable）。
  * Java中没用一种安全的抢占式方法来停止线程，因此也没有安全的抢占方式来停止任务。
  * 


