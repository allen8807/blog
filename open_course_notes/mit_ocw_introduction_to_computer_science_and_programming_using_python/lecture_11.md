## 第十一课 测试与调试
### 2016-11-26
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
    * 因为对小对象测试比大对象容易多了,调试小程序也更容易，最后再合成大程序进行测试。
    * 一定要做单元测试
* 为什么测试总是挑战？why testing always challenge?
    * 小例子 
    * def max(x,y)  穷举会有无尽的可能
* Test suite 测试集
    * Small enough 足够小，能在合理时间内完成 
    * Large enough to give some confidence. 足够大，能给我们信心 
* 后面会讲如何找到一个合适的测试集，现在只是给大家一个印象
* 运行测试集，发现时间过长或者有错误，就需要调试了debugging
* debug 来源
    * 1947.09.09 Grace Murray Hopper 第一位美国海军女上将，第一批程序员之一
    * 测试反正切和余弦函数发现不能运行，最后再70号传送带那里发现卡住了一个虫子
    * 但是最早的来源是1896年电力手册上的，优秀的程序员要学会debug
    * debug是通用技能，可以用于各种系统
* Myths of bugs 对于bug的错误认识
    * 1 bugs crawl into programs 虫子爬进系统。 bug是由错误的操作参数的
    * 2 bugs breed    错误繁殖。 错误不会繁殖，但是错误会有很多。
* Goal: Not to eliminate one bug. Bug-free. 调试的目的不是为了消除一个bug而是得到一个没有bug的程序
* 发现了一个bug意味着可能有更多的bug
* 调试器
    * 最好的两个调试器，也是最古老的
        * Print statement 输出
        * Reading 阅读代码
    * 其他调试器
    * Be systematic 系统化地做调试 好的调试员与差的调试员的区别所在
        * Reduce search space  减少搜索空间
        * Localize the source of problem  定位问题所在
        * 调试是一个搜索过程需要搜索算法
* 怎么让调试过程变得系统化？
    * study program text
    * how could it have produced this result
    * is it part of family? 这个错误是不是只是一部分
    * How to fix it ?
* Scientific method 科F学方法
    * Study a vailable data. 
        * Test results 所有的测试结果，不光是有错的
    * Program text 带着怀疑的态度阅读代码 skeptical eye
    * Form a hypothesis  构造假设
    * Design & run repeatable experiment
    

    