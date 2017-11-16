## 第十课 分治法，合并排序，异常
### 2016-11-20
* Search 
* 首先复习上节课的内容
* 
|  Ordered - Binary | Unordered - linear |
|:-- |:--- |
| logN | N  |
| n logn - to get order | Amortize |
| nlogn + logn | n |
| nlogn + klogn | k*n |

* 简单复习下二分法
* 二分法是一个简单的分治法的例子
* Divide and conquer algorithm  分治法 
    * split the problem into several sub-problems of the same type.
    * solve independently 
    * combine solutions
* 二分搜索法实际上是将问题分成两个，但是抛弃了另一个，这样结果合并也没有太大意义。所以子问题就是父问题的结果，但是这就是分治法的思想。
* 要用这种思想来处理排序
* Merge sort 归并排序 1945年 John von Neumann 约翰·冯·诺依曼发明
    * merge two lists 合并两个排序好的序列需要多少步骤？
    * [3,12,17,24] [1,2,4,30] 
    * [1,2,3,4,12,17,24,30] 只需要比较7次
    * 只需要比较每一列的第一个，所以每次合并所需的复杂度是线性的
    * O(n) - n is sum of number of elements in each list
* Merge sort 
    * divide list in half
    * continue until we have singleton lists 直到我们拥有单个元素列表
    * Merge of the sublists
* 现场演示归并排序 （飞鸿雪泥按：感觉很适合多线程并行使用）
* 分治法要权衡在合并时需要的代价
* 通过图形展示归并排序的算法时间复杂度是O(nlogn)
* 概括一下
    * 解决问题的一标准方法是将问题分解成规模更小的相同问题，如果可以就可以用分治法
    * 要决定分成几份
    * 要决定分解到什么地方是可以解决的基本问题
    * 要决定如何合并
* 适合分治法的问题是，可以简单分解并且合并过程不是非常复杂的问题
* 最后一个算法 哈希算法 hashing
* Hashing
    * 举个例子，整数集 collection of integer
    * 把每个整数直接放在对应的位置
    * 时间复杂度 O(1) 常数时间
    * 如果是字母，找一个哈希函数映射到数字
* 核心就是将对象映射到数，访问时间为常量级
* Trade space for time 以空间换时间
* 如何保证哈希函数将任何输入映射到唯一存储空间去？
    * 答案是不能
* 对于一个复杂问题，很难设计一个哈希函数具备完全平均的分配
* 但应该尝试去设计，尽量让每一个点上的数据量很小
* Hard to create
* 简单对以前的三四节课总结
    * 介绍了算法类型
    * 希望你们知道如何做一些简单的算法复杂度分析
    * 如何根据算法的特点将其辨别出来并且知道它属于哪一类算法
    * 教给一套标准的算法
        * Rootforce 暴力的尝试每一种路径，规模小时，效率高。先猜测再验证
        * Successive approximation ， 逐次逼近 Newton-Raphson迭代是一个好例子
        * Divide and conquer 分治法
    * 这些都在工具箱里，希望你能看到一个问题说出最适合解决这个问题的算法，并将问题映射到相应的案例里去
* 谈谈Python语法里最后一个异常Exceptions
    * unhandled
    * handle
    * try - except block
* Exception vs assert?

| Exception  |  assert|
|:-- |:--- |
| 处理不愿发生的事情 | Pre-conditions 测试条件|
|  | post-coditions|

* 为什么有异常处理？ 
    * 如果有可能输入不是预期类型，需要异常，不希望有非预期的情况漏过去
    * 防止用户输入让程序陷入困难的情况
