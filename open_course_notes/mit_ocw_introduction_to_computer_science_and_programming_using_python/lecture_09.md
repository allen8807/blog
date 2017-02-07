## 第九课 二分法搜索，冒泡排序与选择排序
### 2016-11-17
* 已经看过许多算法，目标是让大家可以看到算法特性，并且映射到特定分类里去
* 再一次讲二分法
* 为什么一定会结束？
* 如何实现列表list
    * 数字列表，用数组形式 常数时间 （能这样的关键是数字占内存一样，所以可以随机访问）
    * 如果是各种类型的呢？ 使用链表 线性时间 lisp是这么实现的 ，这种情况下，二分搜索就不是对数级的了
    * Python不是这么实现的，它用盒状指针图 a box and pointer diagram ,list 里都是指针 ，这样又变成了数组形式
* Generalize 二分法步骤
    * 1. pick the mid point
    * 2. check to see if this is the answer
    * 3. if not reduce to a smaller problem and repeat
* 这是一个实用的工具不仅是解决搜索问题，也是解决一整类问题的方法
* 这个模版不仅描述了二分法，实际也描述了对数形算法
* 用来搜索的有序的队列是哪来的？
* 如果拿到的是无序队列，那么是否应该先排序再搜索？
* Should we sort before we search?
* Can we sort in sublinear time? 能在亚线性时间内排序吗？亚线性指比线性时间短，类似对数？
    * NO，不可能，因为每个数都要看一遍
* Can we sort in linear time?
    * Probably not 每个数都观察，但是放的位置应该依赖于队列长度
* How fast can we sort it?
    * N * LogN time

| Linear case | sorted & search |
|:-- |:--- |
| N | N*logN + logN |

* 如果只搜一次那不用排序，但这一般不可能
* Amortize the cost 分摊成本
    * k searchs of a list 
| Linear case | sorted & search |
|:-- |:--- |
| K*N | N \* logN + K * logN |

* 来看排序算法
* selection sort 选择排序 cell sort
    * 遍历列表，每次找后面最小的，记录位置，最后和当前位置的元素交换
* 循环不变量 loop invariant
    * 结构中，在每次循环中都为真的量，每次循环都不做改变的量
    * list is split into prefix & suffix ,prefix is sorted , suffix is not
* 复杂度是多少？ N^2
* Bubble sort 冒泡排序
* 复杂度 N^2
* 两个算法哪个更好？
    * 选择排序的交换次数很少
* Divide and conquer algorithm 分治法 二分法是分治法的一个版本