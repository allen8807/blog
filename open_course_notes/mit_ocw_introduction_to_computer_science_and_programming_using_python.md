# 麻省理工学院：计算机科学及编程导论
# Introduction to Computer Science and Programming Using Python 

## 第一课 课程目标，数据类型，运算，变量
### 2016-09-27

* 不希望高水平的人来听这门课
* 不希望学生仅仅因为没经验而觉得自己不够格（we don't want you to feel inadequte when you're simply inexperienced.）
* Skills:
    * Computational thinking(计算思维) 
    * Understand code
    * Understand ablilities and limits
    * map the problems into computation
* 阅读代码的能力更重要
* 教你读，教你写，教你知道什么能做什么不能做，更重要的是开启你们如何从别的领域里提炼概念，并研究如何将它们映射到计算机领域的能力
* 课程使用python教学
* 笔记即使不看也有利于记忆和学习
* Think like a computer scientist 像计算机学家一样思考
* 在计算模式中思考
* what is computation?
* What is knowledge?
    - Declarative knowledge（陈述性）
        * 描述一个事实，定义，原理
        * 但不会说出如何计算出来的
        * It tells you how you might test something, but it doesn't tell you how to.
    - Imperative knowledge（程序性）
        * 对推导事实的描述
        * It tells you how to deduce something.
* 最早的计算机 Fixed-program computers （固定程序计算机） 为特定程序设计的小线路
    * calculators
    * Atanasoff, 1941 - linear eqs. 解决线性方程
    * Turing bombe 破译密码
* Stored-program computer(存储程序计算机）
    * memory, control unit, arithmetic logic unit, input , output
    * PC 计数器
* Program is a recipe
    * Fixed set of primitives can program anything.
* 1936年 Turing 提出 6个基本类型。
* It says anything you can do in one programming language, you can do in another programming language. It's called **_Turing compatibility_**.
* 你在一种编程语言中能做的事情，在另一种语言中也能做。这叫做**_图灵兼容性_**。
* 没有最好的语言。There is no best language.
* Python 讨论语言的三个纬度
    * High vs. low
    * General vs. targeted
    * Interpreted vs. compiled
* Syntax -- what are the legal expressions in this language
    * "cat dog boy"
* Static semantics（静态语义） -- which programs are meaningful.
    * "My desk is Susan."
* Semantics (Full semantics) -- what dose the program mean? or what's going to happen when I run it?
* Style 
* Python里的Values
    * Numbers
        * 3 -- Integer
        * 3.14 -- Float
    * String
* Python里的整除，浮点除法，字符串相加
* Variables
    * myString = 
    * 变量绑定

## 第二课 分支，条件和循环
### 2016-09-28
* Primitive data -- numbers and strings 
* 把基础类型组合起来
* value and type
* Combine in expressions: operands and operators.(运算符和运算对象组成）
* Interpreter -- evaluate and print 解释器本质上是运算和输出
* Silent -- no print unless explicit.
* 类型转换 type conversion
* Type checking 类型检查 要尽早做
    * week vs. strong typing
    * type discipline 
        * A. 检测运算符在不同条件下做什么操作
        * B. 写代码时要约束运算符的运算对象或者参数类型
* Operator precedence 操作优先规则
    * 有疑问时用括号 when in doubt, use parentheses
* Variables have own values
* Assignment 
    * x = 3 * 5
    * x是指向内存的一个链接（指针）
    * y = 15
    * z = x z指向15而不是x
* Type of variable -- inherits from value 继承类型来自于值
* Dynamic types 动态类型，类型根据当前绑定的值而改变
    * x = 'abc' 类型改变成string
    * 养成好的编程习惯，不要反复改变变量类型
    * don't change types arbitrarily
* Variable used any place it's legal to use the value.
* Statement = legal commands that python can interpret.
    * print , assignment
* 好的编码风格
    * comments 帮助代码阅读者理解代码
    * 变量名的选择，用有意的词
* Variable names -- important to document.
* 28 Keywords excluded. 不用系统保留字，python有28个保留字
* Straight-line programs 一个接一个地执行一系列的指令的程序
* Branching programs 分支程序 -- can change the order of instructions based on some test( usually value of variable).
* Conditional
* Syntax colon is important 
    * idetifies a block
        * colon is start
        * carriage return is the end
* if<some test > :
    * Block of instructions
* else :
    * Block of instructions
* if 可以嵌套
* 给有分支结构的程序设计测试用例，要覆盖每一个路径
* 对条件里的每一个进行检查
* Boolean combination
    * AND, OR, NOT
    * Type -- two values
        * True
        * False
* 直线程序的执行时间和指令数成正比
* 简单分支程序，算法时间复杂度是常数，最多和指令总数一样，和输入无关
* 计算算法代价
* 迭代循环，需要持续地判断，这是一个不同的控制结构
* 循环，重复执行一个代码片段
* 搞清楚对输入的期望
* create iterations

## 第三课 一般代码样式，循环式程序
### 2016-09-29
* 之前已经学过三种东西DATA, OPERATIONS, COMMANDS
    * data（数据）
        * Numbers
        * Strings
        * Booleans
    * operations（操作）
        * +,*
        * and, or
    * commands（命令）
        * assignment
        * input/output
        * conditionals
        * loop mechanisms (while)
* good programming style 良好的编程风格
    * comments 要有注释
    * type discipline 类型检查
    * descriptive variable name 有意义的变量名
    * documenting your code 代码文档化
* Iterative programs 迭代程序
    * choose variable that "count" 选择一个计数器变量
    * initialize outside the loop 在外部初始化
    * set up end test (variable)设置（计数器变量的）终止条件
    * construct block of code 构造循环代码块
        * change variable 记得改变循环计数器
    * what to do when done 完成时做什么
* Flow chart 流程图
    * 描述程序流程
    * 将流程可视化
    * 直观地看出迭代程序和分支程序的执行顺序不同
* 线性复杂度程序 a linear process
    * 程序代码执行次数和输入参数线性相关
* 另一个工具 Simulate the code ，模拟代码
| ans | x | ans*ans | 
|:--  |:---|:--------| 
| 0   | 16 | 0     | 
| 1   |    | 1     |
| 2   |    | 4     |
| 3 | | 9 |
| 4 | | 16 |
| 5 | | 25 |
* 程序要保证两件事
    * 程序能够结束
    * 程序返回正确的结果
* Defensive programming 防卫性程序设计
    * 一种良好的设计方法
    * General principle: People are dumb and will make mistakes. 人是愚蠢的，会犯错的。
* Exhaustive enumeration 详尽的列举
    * try all "reasonable" values until you find solution 遍历所有合理的值直到找到解决方案
    * 例子，找所有的除数
* For loop for循环
    * 遍历一个集合
    * for (vov) in (some collection)
        * block of code
    * for循环不用担心程序不能结束
* Tuple -- ordered sequence of elements 元组，一系列有序的元素
    * (immutable)
    * foo=(1,2,3,4）
    * 元组可以从反向访问 foo[-1]
    * selection foo[0]
    * slicing foo[1:3] 切片
* range(1,10) 返回的是数组
* 两个tuple可以相加，接到后面
* 字符串是有序的元素序列
* Strings - also support
    * Selection
    * Slicing
* 形成迭代的思想
    * 弄清楚要变量的东西
    * 弄清楚要遍历的集合
    * 弄清楚每一步做什么
    * 弄清楚终结测试是什么
* 这些结构可以用来做什么？
    * 可以做所有的事情
    * Turing complete language 这是被称为图灵完全化语言的特点

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

## 第五课 浮点数和二分法(逐次近似)
2016-10-11
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

## 第六课 二分法，牛顿-拉普森法，对于数组的简介
2016-10-12
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

## 第七课 数组以及可变性，字典，伪码，对于代码运行效率的简介
2016-10-18
* Ivys[1] = -15 表示Ivys还是绑定原来的对象，而它的元素绑定了另一个对象
* 数组是多相的 list can be heterogeneous 也就是说元素可以是多类型的
* 不用小写的L命名变量
* 两个变量指向同一个对象，对象改变，两个变量都可见
* Dictionaries
    * Mutable, heterogeneous
    * Not ordered 
    * Generalized the indexing 
    * key-value pair (key ,value)
    * 散列算法 hashing 可以在常数时间内找到key
* 后面要讲两个话题
    * 如何使用已经学过的东西帮助组织和优化代码
    * 如何计算算法效率
* 如何组织代码
    * 例子计算直角三角形的斜边
    * Pseudo code 伪代码 对步骤进行描述的语言，不是某种特定的语言
        * input value for base as float 输入一个浮点数作为底
        * input value for height as float
        * square-root of b*b + h*h
            * save as a float in hyp
        * print something out using value in hyp
    * 1. 使用了模块概念
    * 2.指定了数据类型
    * 3.控制流
    * 4.使用抽象，没有具体说如何求平方根（引入math库）
* 先写伪代码，一堆数据，启动顺序
* 别相信用户会按照规则来
* 用伪代码把这些串起来之后就可以开始一些结构方面的优化了
    * 两块代码的不同之处在哪？
        * 做了两件事，一件是根据输入得到输出，另一件是输入不是正确类型该输出什么
        * 将两件事分别封装
        * 将一个方法放入一个模块
        * 代码减少了，编译和阅读更容易
        * 更重要的是separated out implementation from functionality, or implementation from use 将功能和实现分离了
        * 这意味这如果要改变输出，并不需要改变方法只要改变输入即可
        * 将用户和实现者分开了，这是创建方法的原因。用户不用关心实现的细节。实现和使用分离。
* 养成解决问题前先写伪代码的习惯。修改伪代码的遗漏流程比修改代码的要容易的多
* 用伪代码定义控制流，基本模块是哪些，模块间如何传参
* What is the flow of control, what are the basic modules, what information needs to be passed between those modules in order to make the code work.
* Efficiency 效率
    * 给一个关于效率的基本认识
    * 本课不会讲那些复杂的问题，只讲基本的简单问题
    * 让大家产生对处理效率问题的一些直觉 some intuition
    * 能够制作一个关于各种算法分类的目录，当遇到问题时可以找到合适的那一类算法，并在其中找到解决问题的方法
    * 打开台灯的同时，按下计算机按钮，灯光到达桌面的时候，计算机已经运算了两次（1.8GHz的mac air）
    * 计算机很快，为什么还要效率？因为我们要处理的问题的复杂度的增长比计算机提速还要快。比如1秒处理半个G的数据。谷歌处理100亿的网页
    * Sanjay Ghemawat 毕业于MIT，设计了能让Google快速搜索的算法
    * 设计一个新算法是很难的，所以更好的方法是把问题映射到已经设计好的算法中去，并用这些算法来提高效率
    * choice of algorithm 培养选择算法的能力 
    * map problem into a class of algorithm 映射问题到一类算法
* 有两个需要量化的东西 space & time
    * how much memory to complete
    * what is the number of basic steps needed as a function of the input size
* 针对basic steps的两个假设
    * random access model 取得内存中任意位置变量的时间是恒定的
    * 基本的原始操作计算花费的时间是恒定的
* 还要解决三个问题
    * best case     min 意义不大
    * worst case    max 很多情况就是最坏的，比如搜索不到的情况
    * expected case avg
* 不知道用户输入的分布
* 下次课会很有趣，拿出了三个像汉诺塔的玩具

## 第八课 算法的复杂度：对数级，线性级，平方级，指数级
2016-10-20
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

## 第九课 二分法搜索，冒泡排序与选择排序
2016-11-17
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

## 第十课 分治法，合并排序，异常
2016-11-20
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

## 第十一课 测试与调试
2016-11-26
* Testing and Debugging
* 世界不是完美的
* 一些定义
* Validation 验证
    * Process to uncover problem & increase confidence 发现问题和增加程序可靠性的自信
    * Testing and Reasoning 是测试和推理这两件事情的组合
    * 推理是说明为什么这样一个测试集是合理的
* Debugging 调试
    * Process of ascertaining why the program failing 找出程序失败的原因
    * 这个问题有两个方面 Function & performance 
* Defensive programming 防卫型编程 
    * Abet validation & debugging 
    * 使用assert声明来尽早发现问题
* Test和debug是不同的，测试是将输入输出对比说明书，而debug，我们研究是什么导致出现了问题。
* Test: examine input/output pairs
* Unit Testing 
    * Functions classes
* Integration testing
    * Overall program
* 先对小功能做测试，对每个功能进行独立测试，再整体测试
    * 因为对小对象测试比大对象容易多了 