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
