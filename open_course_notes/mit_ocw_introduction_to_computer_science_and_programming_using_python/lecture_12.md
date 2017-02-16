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