# 第一讲 极限
## 一、极限定义
* 6*4+1种定义

###1.函数极限
* $$ \lim_{x\to x_0} f(x) = A \Longleftrightarrow \\  \forall \varepsilon > 0, \exists \delta > 0, 0 < |x-x_0| < \delta时, |f(x) - A | < \varepsilon $$
###2.数列极限
* $$ \lim_{n\to \infty} x_n = a \Longleftrightarrow \\  \forall \varepsilon > 0, \exists N > 0, n > N 时, |x_n - a | < \varepsilon $$



## 二、极限性质
### 1.唯一性

* 极限若存在，极限必唯一
* $$ 若lim_{x->x_0}f(x)=A(\exists),则A唯一 $$
* 反证法证明
 
### 2.局部有界性
* $$[Th]若lim_{x->x_0}f(x)=A(\exists), 则\\\exists \delta > 0, 0 < |x-x_0| < \delta时,\exists M > 0,使|f(x)| < M$$
* 添加条件，不等式证明
* 讨论有界性的方法
 
* [自注]初等函数是由幂函数（power function）、指数函数（exponential function）、对数函数（logarithmic function）、三角函数（trigonometric function）、反三角函数（inverse trigonometric function）与常数经过有限次的有理运算（加、减、乘、除、有理数次乘方、有理数次开方）及有限次函数复合所产生，并且能用一个解析式表示的函数。
* 初等函数在其定义区间内必连续
 
### 3.局部保号性（保序性）（脱帽法）
* $$[Th]若lim_{x->x_0}f(x)=A > 0, 则\\ \exists \delta > 0, 0 < |x-x_0| < \delta时,f(x) > 0$$ 反之亦然
* $$[推论]若\exists \delta > 0, 0 < |x-x_0| < \delta时, \\ f(x) >( \ge) 0 且lim_{x->x_0}f(x)=A (\exists), 则 A \ge 0$$ 反之亦然

* 对极限的理解 
* $$ lim f(x) = 3 $$
* $$ 2 < f(x) < 5 , (2,5) 并不是f(x) 的取值区间，这只是事实陈述$$
* $$ lim我=你 => 即使给我整个世界，我也只在你的身边 $$
* $$ 1-\cos x > 0 ,x≠0$$ 
 
 
 ## 三、极限计算
 ### 1.函数极限计算
 * 综述:
     * 1.化简先行(等价替换，恒等变形，抓大头(找带头大哥))
     * 2.判别类型(七种未定式)
     * 3.使用工具(洛必达，泰勒)
     * 4.注意事项
 * $$\lim f(x),x是连续变量$$
 * 七种未定式
     * $$ \frac 00 (\frac {无穷小}{无穷小}), \frac {\infty}{\infty}, {\infty}\bullet0 $$
     * $$ {\infty}-{\infty} $$
     * $$ {\infty}^0, 0^0, 1^{\infty} $$
     * [注]此处0不是真正的0，1不是真正的1
 * 计算工具
     * 洛必达法则
         * 斗鱼主播 1012132 数学史
         * $$ \frac 00 (\frac {无穷小}{无穷小}), \frac {\infty}{\infty} $$
         * $$ f(x),g(x)极限都为0或{\infty},则 \\ \lim \frac {f(x)}{g(x)} =\lim \frac {f'(x)}{g'(x)} (可以是\exists或{\infty}） $$
         * 用了再说，先看导函数是否存在，导函数比值的极限是否存在
         * $$[注1]\lim \frac {f'(x)}{g'(x)} \exists或为{\infty}才能用$$
         * [注2] 常用等价无穷小
             * $$x \to 0$$ 
                * $$ \sin x \sim x, \arcsin x \sim x $$
                * $$ \tan x \sim x, \arctan x \sim x $$
                * $$ e^x-1 \sim x, \ln (1+x) \sim x  $$
                * $$ (1+x)^ \alpha - 1 \sim \alpha x $$
                * $$ 1- \cos x \sim \frac12x^2 $$
              
    * 宇哥考研 微博
    * [注]化简方式
        * 等价无穷小替换
        * 及时提出极限不为0的因数
        * 恒等变形（有理化，提公因式，++--**//)
        * [小结]设置分母有原则，简单因式才下放
            * 简单 $$ x^α, e^{βx} $$
            * 复杂 $$ \ln x, \arcsin x, \arctan x $$等 
            * $$ \ln u \sim u-1 ,u \to 1 $$
        * 换元法
    * $$ {\infty}-{\infty} $$
        * 有分母，通分
        * [注] 熟记各种三角公式
        * 没有分母，创造分母，再通分，令x=(1/t),倒代换
    * $$ {\infty}^0, 0^0, 1^{\infty} $$
        * $$ u^v = e^{v \ln u} $$
        * $$ \lim u^v = e^{\lim v(u-1)} , 1^\infty $$
    * 泰勒公式
        * $$ 观点:任何可导函数f(x) = \sum a_nx^n统一美 $$
        * 熟稔于心: $$ x \to 0 $$
        * $$ \sin x = x - \frac16x^3+o(x^3) $$
        * $$ [Th] 无穷小A = 无穷小B + 高阶无穷小\alpha \\ \Rightarrow A \sim B $$
        * $$ x - \sin x \sim \frac16x^3 $$
        * $$ \arcsin x = x + \frac16x^3+o(x^3) $$
        * $$ \sin x = x - \frac16x^3+o(x^3) $$
        * $$ x - \arcsin x \sim -\frac16x^3 $$
        * $$ \tan x = x + \frac13x^3+o(x^3) $$
        * $$ \arctan x = x - \frac13x^3+o(x^3) $$
        * $$ \cos x = 1 - \frac{x^2}2 + \frac{x^4}{24} + o(x^4) $$
        * $$ \ln(1+x) = x - \frac{x^2}2 + \frac{x^3}3 - \frac{x^4}{4} + o(x^4)  \\通项公式 (-1)^{n-1} \frac{x^n}n $$
        * $$ e^x = 1+ x + \frac{x^2}{2!} + \frac{x^3}{3!} + \dots  \\通项公式  \frac{x^n}{n!} $$
        * $$ \frac1{1-x} = 1 + x + x^2 + \dots ,|x| < 1 \\通项公式 x^n  $$
    * 展开原则
        * 见到 $$ \frac AB $$型，用上下同阶原则，即若分母（分子）是$$x^k$$，则分子（分母）展开至$$x^k$$
        * 见到 $$ A-B$$型，用幂次最低展开原则，即，将A，B分别展开至系数不相等的x的最低次幂为止
      
### 2.数列极限计算 $$ \{ x_n \} $$ 三方面
* (1) 若 $$ x_n $$ 易于连续化，转化为函数极限计算，归结原则
    * $$依据:若 \lim_{x \to +\infty}f(x)=A,则\lim_{n \to +\infty}f(n)=A $$
    * 连续的极限是A，则离散的极限也是A
* (2) 若 $$ x_n $$ 不易于连续化，用“夹逼准则”（或定积分定义（见后））
    * [Th]:
     * $$ 1. y_n \le x_n \le z_n $$
     * $$ 2. y_n \to A, z_n \to A , n \to \infty $$
     * $$ 3. x_n \to A $$
    * 放缩法
    * 只动分母，不动分子 
    * [注] 夹逼准则不验证“等号”，即 $$ < , \le $$均可
    * n充分大时，利用函数“天生的有界性”
* （3） 若 $$ \{ x_n \} $$ 由递推式 $$ x_n = f(x_{n-1})$$给出，用“单调有界准则”
    * [Th] 给出$$ \{ x_n \} $$，若$$ \{ x_n \} $$ 单调增且有上界或 $$ \{ x_n \} $$ 单调减且有下界， 则 $$ \lim_{n \to \infty} x_n 存在 ，\{ x_n \}  收敛$$
    * 高阶，低阶互推，数学归纳法或者递推法
    * 先探索前几项，找规律
    * 第一数学归纳法
      * 1.验n=1时成立
      * 2.设n=k时成立
      * 3.证n=k+1时成立

## 四、极限的应用 -- 连续与间断
### 1. 基本常识
* 任何初等函数在其定义区间内连续，故考研中只研究两类特殊的点
     * 分段函数的分段点（可能间断）
     * 无定义点（必然间断）
     
     
### 2.连续的定义
* $$ lim_{x \to x_0} f(x)  \Rightarrow x ≠ x_0 处$$
* $$ f(x_0) \Rightarrow x = x_0 处 $$
* $$ lim_{x \to x_0} f(x)  和 f(x_0) 本身并没有关系 $$
* $$ 若lim_{x \to x_0} f(x) = f(x_0), 则称f(x)在x=x_0处连续 $$
* [注] $$ lim_{x \to x^+_0} f(x) = lim_{x \to x^-_0} f(x) = f(x_0) $$三者相等，才连续


### 3.间断的定义
* $$ lim_{x \to x^+_0}f(x) \Rightarrow （1）$$
* $$ lim_{x \to x^-_0} f(x) \Rightarrow （2）$$
* $$ f(x_0) \Rightarrow （3）$$
* $$ 设 f(x)在x=x_0点的某去心邻域有定义 $$ 前提
    * 1. (1),(2)均存在，且
        * $$（1）≠（2） \Rightarrow x_0 为跳跃间断点 $$
        * $$（1）=（2）≠ (3) \Rightarrow x_0 为可去（可补）间断点 $$
        * 统称第一类间断点
    * 2. (1),(2）至少一个不存在（考研中，只考了(1),(2）均不存在）
        * $$ 若不存在= \infty \Rightarrow x_0 为无穷间断点  $$
        * $$ 若不存在= 振荡 \Rightarrow x_0 为振荡间断点  $$
    * [注]
        * 1.单侧定义不讨论间断性
        * 2.若出现一侧是振荡，一侧无穷，则分侧讨论，左侧振荡间断，右侧无穷间断
        * 菲赫金格尔茨 微积分教程，三卷 
      

   
