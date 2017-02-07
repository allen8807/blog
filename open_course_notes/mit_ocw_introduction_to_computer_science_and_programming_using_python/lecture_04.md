## 第四课 函数抽象与递归简介
### 2016-10-10
* We have assignment,conditionals,I/O,looping constructs (for,while)
* A language is Turing complete 一个语言应该是图灵完备的，就是说可以写出任何程序。（但不是可以easily写出任何程序）
* 串行化编程，代码不易阅读，尤其是代码量很大的时候
* We don't have Decomposition 分解, Abstraction抽象
* 分解将代码模块化
* 抽象让我们忽略细节
* Functions
    * break up into modules
    * suppress detail 忽略细节
    * create "new primitives" 本质是提供一种创建原语的思考方式
    * 函数的目的是寻找计算的共同模式
    * 加减乘除也是原语，是函数
    * 抽象化，要规格化
* def --keyword
* Name(x)--define formal parameters 形参
* return --keyword 控制转移
* None --special vale
* 每个分支都应该有个return
* Invoke function by passing in values for the parameters
    * sqrt(16)
    * Binds x to 16 -- local只在本地有效
    * ans is also bound local
    * Local binding do not affect global bindings.
* Interpretes -- global bindings
* Call function
    * local table
* 此处画图展示，外部变量和函数内变量赋值不影响
* 函数的规范说明，说明函数的用法，抽象，不需要细节
Farmyard problem
    * 20 heads , 56 legs 鸡兔同笼问题
    * numP + numC = 20
    * 4*numP + 2*numC = 56
    * emumerate & check 列举和和验证 
    * 就是brute-force algorithm 穷举算法
    * 如果扩展到三种，pigs, chickens, spiders 
* 链表和数组很像
* Recursion 递归 
    * 很方便的编程思想，在分解程序时也很有用
    * 将问题分解成同样的小问题
    * base case -- simplest possible solution
    * inductive step 归纳法的步骤
        * break problem into a simple version of same problem and some other steps
* 判断字符串是否回文
* 把问题分解成越来越简单的问题
* 代码要可收敛
* 经典问题 Fibonacci Numbers 兔子问题
    * Pairs(0) = 1
    * Pairs(1) = 1
    * Pairs(n) = Pairs(n-1) + Pairs(n-2)
* 递归，有继承意义的迭代程序。
* 有些问题可以容易想出递归的方法，但是不容易想出迭代的方法，自己选择正确的