## 第十四课 背包问题分析，面向对象编程简介
### Lecture 14: Analysis of knapsack problem, introudction to object-oriented programming
### 2017-02-18
* 先讲一下决策树，貌似不少人上节课没太明白
* Binary Decision Tree
* Optimal substructure
* Memorization 默记法，动态规划的核心
* 是否能在线性时间内完成？
* 看看时间空间复杂度
* 时间复杂度 $$O(ns)$$
    * n items
    * s size
* 空间复杂度 $$O(ns)$$
* 某种意义上来说是空间换时间
* Size of solution 计算时间不光和输入的值有关，也和值占据的空间有关
* 最好还是根据size of solution 来计算，也就是根据占的空间
* 伪多项式算法 伪多项式时间算法 Pseudo Polynomial 
    * Polynomial in numeric value of input
    * Numeric value
        * Exponential in # digits
    * 想清楚这个问题是关键
* 重新审视一下复杂度大O：size of coding of input
    * 应该用计算机的数值位来表示输入规模
    * 一个问题的输入规模是保存输入数据所需要的bit位数    
* 飞鸿按：这里的字幕翻译完全云里雾里，估计字幕组的人没有看懂这段。这个伪多项式算法需要好好理解一下。这里的输入规模不再是传统数值，而是保存的数位。如果能看懂下面这句话，说明已经理解：
    * 算法的时间复杂度是输入数据的值的多项式表达，但却是输入数据的存储长度的指数时间表达
    * 考虑一下数组排序和计算一个数的阶乘这两个的时间复杂度
* 讲这些的原因是，希望你们能理解，我们讨论的复杂度很精妙的（quit subtle）。你必须清楚的知道你的意思，你可能会很惊讶有些程序跑得太长或者占得空间太大。你必须能区别程序的性能是和size of the problem 还是和size of the solution有关。是数组长度还是数组里的元素大小，搞清楚这点很重要。对于$$O(n^2)$$说清楚n是什么
* 这里已经告诉了一种快速解决背包问题的算法，只是它的核心仍然是指数增长的。
* 离开这个问题前，我们来看一下一个稍微变种的背包问题
    * 增加限制，既有重量又有容量限制
    * $$ \sum_{i=1}^{n}P_{i}X_{i}  $$
    * $$ \sum_{i=1}^{n}w_ix_i \leq C \quad and \quad  \sum_{i=1}^{n}v_ix_i \leq K  $$
* 看这个问题是为了对比两个修改以前的算法，要理解一个算法是要有普适性的

* 学生问题：如何选算法？
* 动态规划算法永远不会比穷举法差
* 总结：
    * 1）In dynamic programming, One of the thing that's going on is we're trading time for space. 空间换时间
    * 2）Don't be intimidated by exponential problems. 别被指数型问题吓到了
    * 3）Dynaminc programming is broadly useful. 动态规划用途广泛。当使用递归算法是可以考虑是否用得上动态规划
    * 4）Program reduction. 问题降解，归约。 将问题归约到已经解决的问题去
    
* 下面将回到Python，讨论python语言和程序结构
* Modlue(Modularity)
    * 将程序模块化分解
    * Collection of related functions. 模块是相关的函数集合
    * Refer to functions using dot notation. 用点来调用 
    ```
    import math
    math.sqrt(11) 
    ```     
* 不同的module可以避免混淆
* Classes 类 
* Object-Oriental programming 面线对象编程
* Data abstraction 数据抽象
* Abstract data types
* 40年前就有的想法，最近10-15年才被广泛接受
    * 例如Smalltalk，Clue 提供了语言学支持
    * 但是直到Java诞生才被大众关注
    * Java，C++，Python 现在没人会推荐不支持面向对象的语言
* 面向对象编程里的对象究竟是什么？
    * Object = collection of data and functions 对象是数据和函数的集合 函数是处理数据的
    * 所以传递对象的同时，传递了处理对象数据的函数
* 基础类型没关系，已经内置了
* User-defined types
* 数据和函数的结合是面向对象编程的核心也是它的定义
* 称之为封装 Encapsulation 胶囊里装了数据和方法
* 当人们讨论面向对象编程时，实际是在讨论消息传递。 in terms of message pass， a message passing metaphor. metaphor在这里只是表示一种思考方式
* The way people will talk about this, is one object can pass a message to another object, and receiving object responds by executing one of its methods on object.
* 考虑一个链表,一个圆
```
l.sort() 
c.area()
```
* 每个列表的object都是list type的instance
* 刚才讲的是instance，现在我们说一下类的概念
* Class = collection of objects with characteristics in common. 类是具有相同特质的对象的集合

