## 第十七课 计算模型，随机走动模拟
### Lecture 17: Computational models: random walk simulation
### 2017-12-31
* Informal problem description to formal(rigorous) problem strict.
* Inventing computational models.
* Dealing with & exploiting randomness 
    * stochastic
* Making sense of data
* Evaluating quality of answers
* Start simple
* Simulate random walk
* 建模 Location, Compass Pt, Field, Drunk
* math, random, pylab
* 做了一个仿真程序，随机走500步，运行三次，绘出三张图，结果似乎是并没有在0处振荡的
    * 这里我用更简单的模型做仿真，跑了1亿步结果也不是在0处振荡
    * 个人觉得这些有限数字对于这个大量还是太小了
* 结果似乎出乎意料，那究竟为什么，且听下回分解

## 第十八课 表示模拟结果.Pylab与绘图
### Lecture 18: Presenting simulation results, Pylab, plotting
### 2017-12-31
* 总结仿真程序
* 1.Inner loop that simulate 1 trial
* 2."Enclose" inner loop in a loop that conducts appropriate # of trials
* 3.Calculate & present statistics 
* 通过计算平均值，使得结果光滑，但这是正确的结果吗？
* 100次重复500步，得到平均结果为4步，但是单次结果明显和这个不一样10-40步都有
* 从简单的做起，1步，重复四次，发现计算平均值的方法错了
* 修正后，得到500步的平均距离为20步

* Label axes - & look
* Ask if answer makes sense
    * Consistent with other evidence
* Systematic about debugging
    * simple example

* 随机漫步模型
    * 布朗运动 Browning motion
    * 股票市场 stock market 错了
    * 动力学模型 Kinectics
    * 进化模型 Evolution

