## 第十三课 动态规划，重叠子问题，最优子结构
### Lecture 13: Dynamic programming: overlapping subproblems, optimal substructure
### 2017-02-17

* Overlapping subproblems
    * 子问题是重叠的
    * Memoization 默记法 
        * Record value 1st time. Then look it up subsequently. 第一次的时候记录下来，以后用的时候查询使用。
* 快速fib算法
    * 记录每次的算出的fib值
    * 返回记录的对应项数
    * 算法复杂度为O(n)
* 这是很多Dynamic programming算法的核心，保存已经计算好的结果
* Table lookup 查表是默记法的特例
* 讲fib是因为简单
* 下面讲最优子结构
* Optimal substructure
    * get a globally optimal solution from locally optimal solutions to sub-problems
    * Global optimal solution can be constructed from optimal solutions to sub-problems.
    * 全局最优和局部最优重叠时候，可以用动态规划
* 回到0/1背包问题
    * $$|A|=n$$
    * $$2^n$$ 全部的可能性
* 这个问题是否有最优子结构？
* Decision Tree 决策树
    * 假设重量是$$ W = [5,3,2] $$ 
    * 假设价值是$$ V = [9,8,7] $$
    * $$ Max = 5 $$
    * Depth-first, Left-first 深度优先，左侧优先
* 如何构建决策树
    * 确定节点
    * $$ index , avaliable,value $$
    * $$ 2,5,0 $$
    * 回溯
    * 决策树
    * ![tree](./img/lec13_1.jpeg)
* 明白这个工作原理，这就是系统化
* 复杂度是多少？
    * 最坏情况 指数级
* 运算前先心算估计下结果（当然数据量小的时候）
* 30个物品，最大重量40的时候，运算次数是17millions ，17240165
* 使用那个优化的方法，用一个memo记录已经计算过的部分，重叠子问题
* 30个物品，最大重量40的时候，运算次数只有1805次
* 巨大的进步，Dynamic programming的魅力所在



