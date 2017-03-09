## 第十四课 背包问题分析，面向对象编程简介
### Lecture 14: Analysis of knapsack problem, introudction to object-oriented programming
### 2017-02-18
* 先讲一下决策树，貌似不少人上节课没太明白
* Binary Decision Tree
* Optimal substructure
* Memorization 默记法，动态规划的核心
* 是否能在线性时间内完成？
* 看看时间空间复杂度
* 时间复杂度 O(ns)
    * n items
    * s size
* 空间复杂度 O(ns)
* 某种意义上来说是空间换时间
* Size of solution 计算时间不光和输入有关，也和问题规模有关
* 最好还是根据输入规模来计算
* 伪多项式算法 伪多项式时间算法 Pseudo Polynomial 
    * Polynomial in numeric value of input
    * Numeric value
        * Exponential in # digits
    * 想清楚这个问题是关键
* 重新审视一下复杂度大O：size of coding of input
    * 应该用计算机的数值位来表示输入规模
    * 一个问题的输入规模是保存输入数据所需要的bit位数


