## 第六课 二分法，牛顿-拉普森法，对于数组的简介
### 2016-10-12
* 二分法
    * 解空间是线性有序的 totally ordered
    * 验证解，然后舍弃一半的解空间，然后继续
* 别相信程序员，一定要验证参数
* 回归测试 regression test
    * 当因为一个问题修改了程序模块后，要重新测试一遍所有功能
* 找0.25的平方根，出错，因为一开始定的解空间不包含解。0.5比0.25大
    * 解决方法，下界是0，上界是1和x里大的那个
* 二分法迭代次数并不固定
* 处理复杂问题我们关注收敛速率问题 speed of convergence
* 二分法由古希腊人发明，一直到17世纪都是最先进的。
* sqrt(x) 其实是解方程
* f(guess) = guess^2 -x
* f(guess) = 0 求这个根
* Isaac Newton Joseph Raphson
* Newton-Raphson
* 猜一个数，然后找这个数处的切线，下一个猜想就是这个切线和x轴的交点
    * 大部分情况下，切线和x轴的交点是个更好的接近解的结果
    * 有时候切线与X轴没有交点，要注意
    * 高中时用了该方法求平方根
    * 导数，一阶导数是斜率
    * dy/dx
    * f'(guess_i_)=2*guess
    * guess_i+1_ =guess_i_ - f (guess_i_)/(2guess_i_)
    * f(3) = 9 - 16 = -7
    * guess_i+1_ = 3 -(-7/6) = 4.16666
    * 然后继续
* NR方法比二分法要快一些
    * 复杂情况下效果更好
* Ansers can be wrong 答案可能是错的
    * 浮点数溢出
* 数学很难，python简单
* Non-scalar type 非基本类型 
    * Tuples 元组
    * Strings 字符串 
    * Immutable 不可变的
* Mutable -- List
    * Techs=['MIT','Cal Tech']
    * Ivys=['Harvard','Yale','Brown']
    * Univs=[],univs.append(techs) 会把数组加到数组里去

    * 以上的内存结构图
    * 数组也是对象
    * Flatten
    * L=[1,'MIT',3.3,['*']]
    * 数组里可以放各种对象
* remove方法，改变了数组，数组的可变性
