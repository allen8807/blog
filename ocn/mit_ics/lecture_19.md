## 第十九课 有偏好的随机漫步模型与概率分布
### Lecture 19: Biased random walks, distributions
### 2017-12-31
* 先做了一个仿真程序，将随机漫步改成向南方走时，一次走两步
* 仿真结果偏移了不止2倍，赌场的一些猫腻
* 通过绘图，显示仿真结果的分布情况，引入分布概念，正态分布之类的
* 仿真里加入滑梯，只需要修改field类，结果的变化很大，
* 讲一下仿真程序
* 起源可以追溯到曼哈顿计划 Manhattan Project
    * 模拟核爆炸 nuclear detonation
    * 蒙特卡洛模拟程序 Monte Carlo simulation
* 仿真在什么时候用？
    * 很难得到一个分析结果时
    * 即使能得到，仿真分析也有意义
* Generate a sample of representative scenarios 创建一个简单的有代表性的场景
    * Experimental device 把仿真程序当成研究设备
    * 运行仿真就是在做实验
* 记住仿真是描述性的而非预测性的 descriptive not prescriptive
    * 仿真模拟不是一个最优化过程 not an optimization procedure

## 第二十课 统计试验模拟程序，预测pi值
### Lecture 20: Monte Carlo simulations, estimating pi
### 2018-01-01
* 对仿真模型分类 （分歧）
    * 判断问题是stochastic还是deterministic 是一个随机问题还是个确定性问题。前者不是确定结果，后者是确定结果
    * static vs dynamic 静态还是动态 动态问题有时间的问题，主要精力在动态问题
        * 动态问题的一个例子 Queuing network model 排队网络问题
    * discrete vs continuous 离散和连续

* Monte Carlo simulation 蒙特卡洛随机过程 赌博游戏中有随机性而且是离散的
    * 演绎统计学 inferential statistics
    * Random sample tends to exhibit the same properties as the population from which it is drawn. 随机样本趋向于展现它所在分类的相同的属性
* 仿真了掷硬币的例子，掷1个硬币，掷3个硬币
* 引出下面的问题：
* 过去的行为能预测未来的行为吗？
    * 金融危机前的预测模型？
* 一般建立一个模型，希望能够预测
* 有趣的是可以用随机性技术去获得问题的解决方法，这个可能不是固有的随机性 not inherently stochastic 
* 下面用随机方法计算pi
    * 其实就是概率面积法，向单位面积的正方形里扔飞镖，统计有多少落在四分之一圆里 Buffon Laplace
* pi的历史，1650BC 埃及 3.16， 圣经3，阿基米德 223/71 - 22/7 约3.1418  
* 一千万次仿真结果在最后趋向稳定
* 但这意味着我们获得了正确结果吗？不，并不是。请听下回分解
* 十亿次的结果

## 第二十一课 验证模拟仿真程序结果，线性回归，曲线拟合，预测pi值
### Lecture 21: Validating simulation results, curve fitting, linear regression
### 2018-01-02
* 十亿次的结果是3.14161124 ，即使100亿次也不会更接近多少，越往后趋向变化越慢

