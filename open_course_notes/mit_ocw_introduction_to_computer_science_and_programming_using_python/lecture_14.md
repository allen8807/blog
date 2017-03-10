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
    * $$ \sum_{i=0}^n \frac{1}{i^2}  $$
   
    
