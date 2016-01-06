# java 拼接字符串效率比较
---
前段时间在整理项目里的一些log输出，想到java字符串拼接效率问题，于是做了些测试。
测试主要针对String直接相加，StringBuilder，StringBuffer和format比较。

测试环境是jdk-1.7

比较结果证明string直接相加的效率并不低，记得以前看过，java的某个版本后将string连续相加优化成StringBuilder实现了。测试结果也证明了这一点，1.7已经包含了这个优化。

整体效率的结果是，效率从高到低

StringBuilder >= String 相加 >= StringBuffer > format