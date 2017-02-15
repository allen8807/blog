## 第十二课 调试的更多内容，背包问题，动态规划简介
### 2017-02-09

* 关于调试剩下的几个小点
    * 错误可能不是发生在你认为会发生的地方，如果是，你可能已经找到它了
    * 注意几件事
        * 自变量顺序 Reversed order of arguments  
        * 拼写错误 Spelling
        * 初始化 Initialization , 循环开始的初始化
        * 对象与值比较 Object vs Value equality ==
        * Aliasing 别名混淆 
            * Deep vs shallow copy 深复制和浅复制
        * Side effect 副作用 函数可能会修改实参值
* 熟练的程序员会建立一个自己的犯错模型
    * 知道自己会犯什么错误
    * 多反省自己
    * 收集自己犯过是错误
    * 遇到错误首先想到这些错误
* Keep record of what you tried 记录你尝试过的修改 
    * 系统化编程 不在已经犯过的错误上浪费时间
* Reconsider assumption 重新考虑你的假设 
    * 例如运行的不是你在写的程序
* Debug code, not comments 调试的是代码不是注释
* Get help
