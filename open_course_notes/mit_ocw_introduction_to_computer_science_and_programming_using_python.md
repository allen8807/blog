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
2016-09-29
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
2016-10-10
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

# 第五课 浮点数和二分法(逐次近似)
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




    

    
