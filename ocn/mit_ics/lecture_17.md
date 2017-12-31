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

* Label axes

