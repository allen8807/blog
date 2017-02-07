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
