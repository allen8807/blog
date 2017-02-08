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
    