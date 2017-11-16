## 第五课 浮点数和二分法(逐次近似)
### 2016-10-11
* 计算机被认为擅长处理数字
* integer
    * arbitrary precison Python支持任意精度的整数
    * Long
    * Long数的运算结果也是Long
* Float -- floating point -- real 浮点数
    * 符合IEEE 754 floating point标准
    * Scientific notation科学计数法的变体
    * Mantissa exponent 尾数和指数
    * 二进制系统
    * significant 重要数 mantissa也被称为significant 
    * 1 <= matissa <= 2  mantissa
    * -1022: 1023 exponent
    * 计算机是64 Bit
        * 1 Bit sign 一位存放符号
        * 11 exp     11位存放指数
        * 52 mantissa 52位存放尾数
    * 大约17位的10进制数字精度 17 decimal digits
    * 超过这个精度的大部分语言都做不到
* 1/8 = 0.125
    * Base 10 : 1.25 * 10 ^ -1
    * Base 2 : 1.0 * 2 ^ -3
* 1/10 = 0.1 = 1 * 10 ^ -1
    * Base 2 ? 无限长数字 这就是Python显示0.1会变成0.10000...01
    * Python 内部调用 repr()显示数字将数字显示成string，对于float会round to 17 digits 
    * 误差累计
    * Worry about == on floats 对于浮点数不要做相等判断
    * abs(a*a -2.0)< epsilon 通过这种方法进行浮点数相等的比较
* 找平方根的方法 
* Might not be an exact answer
* Can't enumerate all guesses 因为实数是uncountable 
* Guess,check,improve 
* successive approximation 逐次逼近法
    * guess = initial guess
    * for iter in range(100)
        * if f(guess) close enough : return guess
        * else guess = better guess
    * ERROR
* Bisection method 二分法
    * 解的范围是线性空间
    * 每次逼近，epsilon大于0
    * 程序示例
* 改进方法会在下次讨论
* 飞鸿雪泥按：二分法应该在均匀分布的线性解空间里表现得比较好