## 第七课 数组以及可变性，字典，伪码，对于代码运行效率的简介
### 2016-10-18
* Ivys[1] = -15 表示Ivys还是绑定原来的对象，而它的元素绑定了另一个对象
* 数组是多相的 list can be heterogeneous 也就是说元素可以是多类型的
* 不用小写的L命名变量
* 两个变量指向同一个对象，对象改变，两个变量都可见
* Dictionaries
    * Mutable, heterogeneous
    * Not ordered 
    * Generalized the indexing 
    * key-value pair (key ,value)
    * 散列算法 hashing 可以在常数时间内找到key
* 后面要讲两个话题
    * 如何使用已经学过的东西帮助组织和优化代码
    * 如何计算算法效率
* 如何组织代码
    * 例子计算直角三角形的斜边
    * Pseudo code 伪代码 对步骤进行描述的语言，不是某种特定的语言
        * input value for base as float 输入一个浮点数作为底
        * input value for height as float
        * square-root of b*b + h*h
            * save as a float in hyp
        * print something out using value in hyp
    * 1. 使用了模块概念
    * 2.指定了数据类型
    * 3.控制流
    * 4.使用抽象，没有具体说如何求平方根（引入math库）
* 先写伪代码，一堆数据，启动顺序
* 别相信用户会按照规则来
* 用伪代码把这些串起来之后就可以开始一些结构方面的优化了
    * 两块代码的不同之处在哪？
        * 做了两件事，一件是根据输入得到输出，另一件是输入不是正确类型该输出什么
        * 将两件事分别封装
        * 将一个方法放入一个模块
        * 代码减少了，编译和阅读更容易
        * 更重要的是separated out implementation from functionality, or implementation from use 将功能和实现分离了
        * 这意味这如果要改变输出，并不需要改变方法只要改变输入即可
        * 将用户和实现者分开了，这是创建方法的原因。用户不用关心实现的细节。实现和使用分离。
* 养成解决问题前先写伪代码的习惯。修改伪代码的遗漏流程比修改代码的要容易的多
* 用伪代码定义控制流，基本模块是哪些，模块间如何传参
* What is the flow of control, what are the basic modules, what information needs to be passed between those modules in order to make the code work.
* Efficiency 效率
    * 给一个关于效率的基本认识
    * 本课不会讲那些复杂的问题，只讲基本的简单问题
    * 让大家产生对处理效率问题的一些直觉 some intuition
    * 能够制作一个关于各种算法分类的目录，当遇到问题时可以找到合适的那一类算法，并在其中找到解决问题的方法
    * 打开台灯的同时，按下计算机按钮，灯光到达桌面的时候，计算机已经运算了两次（1.8GHz的mac air）
    * 计算机很快，为什么还要效率？因为我们要处理的问题的复杂度的增长比计算机提速还要快。比如1秒处理半个G的数据。谷歌处理100亿的网页
    * Sanjay Ghemawat 毕业于MIT，设计了能让Google快速搜索的算法
    * 设计一个新算法是很难的，所以更好的方法是把问题映射到已经设计好的算法中去，并用这些算法来提高效率
    * choice of algorithm 培养选择算法的能力 
    * map problem into a class of algorithm 映射问题到一类算法
* 有两个需要量化的东西 space & time
    * how much memory to complete
    * what is the number of basic steps needed as a function of the input size
* 针对basic steps的两个假设
    * random access model 取得内存中任意位置变量的时间是恒定的
    * 基本的原始操作计算花费的时间是恒定的
* 还要解决三个问题
    * best case     min 意义不大
    * worst case    max 很多情况就是最坏的，比如搜索不到的情况
    * expected case avg
* 不知道用户输入的分布
* 下次课会很有趣，拿出了三个像汉诺塔的玩具