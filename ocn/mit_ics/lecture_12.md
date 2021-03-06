## 第十二课 调试的更多内容，背包问题，动态规划简介
### 2017-02-09

* 关于调试剩下的几个小点
    * 错误可能不是发生在你认为会发生的地方，如果是，你可能已经找到它了
    * 注意几件事
        * 自变量顺序 Reversed order of arguments  
        * 拼写错误 Spelling
        * 初始化 Initialization , 循环开始的初始化
        * 对象与值比较 Object vs Value equality ==
        * Aliasing 别名混淆 
            * Deep vs shallow copy 深复制和浅复制
        * Side effect 副作用 函数可能会修改实参值
* 熟练的程序员会建立一个自己的犯错模型
    * 知道自己会犯什么错误
    * 多反省自己
    * 收集自己犯过是错误
    * 遇到错误首先想到这些错误
* Keep record of what you tried 记录你尝试过的修改 
    * 系统化编程 不在已经犯过的错误上浪费时间
* Reconsider assumption 重新考虑你的假设 
    * 例如运行的不是你在写的程序
* Debug code, not comments 调试的是代码不是注释
* Get help - Explain 寻求帮助，要会解释
* Walk away 休息一会
* 修改错误的注意点
    * Haste makes waste 欲速则不达
        * 方案是否能解决问题并不引起其他问题
    * Code should not always gain 代码不能总是增长
        * 清理代码，整理代码
    * Make sure that you can revert 保证可以回滚代码
        * Save old versions
* 公式化问题的处理方法
* Optimization problems 优化问题 优化问题一般有两个要点
    * A function to maximize(min) 要求出最大或最小值
    * A set of constrains 有一系列约束
    * 典型问题 
        * 最短路径问题 shortest path
        * 旅行商问题 Traveling sales problem (TSP)
        * 装箱问题 Bin packing 装东西顺序之类的
        * Sequence alignment problem 序列对比问题 DNA,RNA,自然语言
        * Knapsack 背包问题
            * 判断要带多少东西，最大化价值
* Problem reduction 问题规约 举这么多例子是为了让大家进一步考虑问题规约
* 处理一个问题，将它归结映射到一个老问题（已经解决的问题），利用前人的成果

* 下面看背包问题
* 现在大部分优化问题都没有快速的解决方案
* 目前只处理过亚线性问题，最多也就是多项式问题，这些不能处理背包问题
* Continuous knapsack problem 连续背包问题
* 问题描述
    * 你有一个 8lbs 的包
    * 4lbs Au dust 金沙
    * 3lbs Ag dust 银沙
    * 10lbs raisins 葡萄干
* 如何系统化这个问题？
    * 求 Cg\*PG + Cs\*PS + Cr\*PR 的最大值
    * 约束条件是PG+PS+PR < = 8
* 解决方法很简单，4磅金沙，3磅银沙，1磅葡萄干
* Greedy algorithm 贪婪算法 上面描述的其实是一种贪婪算法
    * 每一个步骤都在最大化你的价值，局部最优
* 贪婪算法并不总是适用
* Locally optinal decisions do not always lead to global optimum 局部最优不一定能得到全局最优
* 变种 0/1 Knapsack problem 0/1 背包问题
    * n items 每个要么都拿要么不拿
    * 四个东西 手表，收音机，花瓶，画
* 贪婪的贼 贪婪算法 先拿最有价值的
* 动作慢的贼怎么做？ 穷举
    * 想要最大值的函数是 ∑PiXi X是0/1向量
    * 约束函数是 ∑WiXi < = C 背包容量
    * 穷举法是指数级的 Exponential
* Dynamic programming 动态编程 数学家Bellman发明的词，因为军方为了不让别人知道研究的是什么。。。
    * Overlapping subproblems 重叠子问题 又被叫作Optimal substructure 最理想子结构
* 先看一个重叠子问题的例子，用递归解决Fibonacci数问题
    * 递归的方法，增长率很高
    * 里面重叠子问题也很多，求fib(5) 会调用 fib(4) fib(3)，而求fib(4)又会调用fib(3) fib(2)，这里fib(3)调用了2次，其他的也是
    * 下次课会看另一种解决方法，增长率会低很多