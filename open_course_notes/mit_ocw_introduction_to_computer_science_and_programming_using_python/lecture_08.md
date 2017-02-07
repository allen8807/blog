## 第八课 算法的复杂度：对数级，线性级，平方级，指数级
### 2016-10-20
* a sort of canonical algorithms 一系列权威算法
* 一个好的设计者，最基本的事情就是学会把新问题映射到已知的领域里去
* 如何推算出问题的复杂度的
* 例子1写一个计算整数指数幂的方法 只用乘法和加法 
    * Iterative exponent
    * 程序就是简单的循环迭代 expl(a,b) = a^b
    * 这个程序执行了多少步 2+3b steps
    * 当b很大时，附加的2就不大了，常数3的影响也不大，真正要关注的是b
* 要关注的是随着问题规模的增长，解决问题花费的代价是怎么增长的
* Rate of growth as size of problem grows
    * Asymptotic notation 渐进表示法
    * Big O notation 大O表示法 用的是大写的希腊字母omicron
        * -the upper limit to the growth of a function as the input gets large
    * f(x) ∈ O(n^2) f(x)的增长率不会超过n^2
        * n is a measure of the size of x
    * 最小的上界，最贴近增长率的上界 
* Recursive exponentiation 递归法
    * return a*expl(a,b-1)
    * t(b) = 3 + t(b-1) = 3 + 3 + t(b-2) = 3k + t(b-k)
    * Done b-k = 1 ,k = b-1
        * 3(b-1)+ t(1) = 3(b-1)+2 = 3b - 1 
    * O(b) 线性增长
* 另一个求乘方的方法
    * a^b=(a*a) ^ (b/2) b even 如果b是偶数
        * 这个方法将问题规模减半
    * a^b=a*(a^(b-1)  b odd 如果b是奇数
    * b even t(b)=b+t(b/2)
    * b odd t(b)= 6 + t(b-1) = 12 + t((b-1)/2)
    * t(b) = 12 + t(b/2) = 12 + 12 + t(b/4) = 12 +12 + 12+t(b/8)
    * =12k+t(b/2^k)
    * b/2^k = 1    k=log$$_2$$b
    * O(log b)
* O(m*n)
    * O(n^2) quadratic 二次的
* Towers of Hanoi 汉诺塔问题
    * 到世界尽头或者华盛顿财政危机解决
    * 很好的关于递归的例子
    * 增长率是多少？
        * T(n) = 1 + T(1) + 2T(n-1) = 3 + 2T(n-1)
        *  = 3 + 2*3 +4T(n-2) = ...
        *  = 3(1 + 2 + 4 + ... + 2^(k-1)) + 2^n (n-k)
        *  O(2^n) Exponential
* n = 1000 计算机每秒10亿次计算
* nanosecond speed

| n = 1000 | nanosecond speed | 
|:-- |:--- |
| log | 10 nanoseconds | 10 millisecs |
|  linear| 1 microseconds | 1 sec | 
| quadratic | 1 milliseconds | 16 minutes |
| exponential | 10^284 years | 

* 不同算法的表现差别很大
* 问题规模的增长比计算机速度增长快多了
* 避免使用指数级的算法
* 希望大家可以通过算法复杂度的计算看出算法的性能
* 希望关注的几个问题
    * 我们感兴趣的是渐进的增长率（asymptotic growth），也就是当问题规模变大时，算法的计算时间如何增长
    * 考虑最坏情况
    * 记住这些是增长率。是通常情况，对于特定输入可能无法简单衡量
* 最后的例子 搜索一个有序数组 search a sorted list
    * 遍历算法来搜索 O(len(s)) 线性复杂度
    * 二分法   O(logN) 
    * 找到数组中的一个数的时间是常量的，随机读取模型 O(1)
    * 对于大数组，python使用linked list 使得获取数组中元素的时间为常量级
* 了解这些算法后，就可以选择了
* 飞鸿雪泥按：这节课又一次提到二分法，这里没有详细写。二分法是非常重要的方法。