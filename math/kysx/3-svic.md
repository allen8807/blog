# 第三讲 一元函数积分学 Single Variable Integral Calculus
* 定义，计算，应用 

## 一、定义
### 1.不定积分
* 1.定义
    * $$ \forall x \in I,使F'(x)=f(x),则\\称F(x)是f(x)在I上的一个原函数。\\全体原函数就叫不定积分，记成\\ \int f(x)dx = F(x) + C $$ 
* 2.原函数存在定理（强化班）
    * 1.连续函数必有原函数
        * $$ 设f(x)在I上连续,\\证明F(x)= \int_a^x f(t)dt,(a,t \in I)必可导,\\且F'(x)=f(x), \forall x \in I    $$
            * 证明使用积分中值定理
            * $$ \int_a^bf(x)dx = f(\xi)(b-a)$$ 积分形式转化为函数形式
    * $$2.含跳跃,可去,无穷间断点的f(x)在此区间无原函数$$
        * $$跳跃处f(x_0 -0 ) ≠ f(x_0 + 0) \\ \Rightarrow F'(x_0) ≠ f(x_0) 所以不\exists F'(x)$$ 
    * $$3.含振荡间断点的f(x)在此区间可能有也可能没有原函数$$

### 2.定积分
* 1.必要条件
    * $$ \int_a^bf(x)dx 存在 \Leftrightarrow f(x) 在[a,b]上可积$$
    * $$ \int_a^bf(x)dx 存在 \Rightarrow [a,b]有限区间$$
    * $$ \int_a^bf(x)dx 存在 \Rightarrow f(x)在[a,b]上有界$$
    * $$ f(x) 在[a,b]上可积 \Rightarrow f(x)在[a,b]上有界$$
* 2.充分条件
    * $$ f(x)在[a,b]上连续 \Rightarrow \int_a^bf(x)dx 存在 $$
    * $$ f(x)在[a,b]上连续 \Rightarrow f(x) 在[a,b]上可积 $$
    * $$ f(x)在[a,b]上只有有限个间断点且有界 \int_a^bf(x)dx 存在 $$
* [小结]
     * $$ \int f(x)dx  ,函数族 $$
     * $$ \int_a^b f(x)dx ,面积值(数）$$
* $$ N-L公式  \int_a^b f(x)dx = F(x)|_a^b = F(b) -F(a)$$


### 强化班总结

* [注1]
    * $$f(x)连续 \Rightarrow F(x)=\int_a^xf(t)dt可导$$
    * $$f(x)可积 \Rightarrow F(x)=\int_a^xf(t)dt连续$$
* [注2]
    * $$\int_a^xf(t)dt \leftarrow f(x) \rightarrow f'(x)$$
    * 1.奇偶性
        * $$\int_a^xf(t)dt 偶\leftarrow f(x) 奇 \rightarrow f'(x) 偶$$
        * $$\int_a^xf(t)dt(a=0,偶,a≠0,不确定)\leftarrow f(x)偶 \rightarrow f'(x)奇$$
    * 2.周期性
        * $$1.可导f(x)以T为周期 \Rightarrow f'(x) 以T为周期$$
        * $$2.可积f(x)以T为周期，则\\\int_a^xf(t)dt以T为周期的充要条件是 \int_a^Tf(x)dx = 0 $$
        * [预备Th]
            * $$若f(x)以T为周期，可积，\\则\int_a^Tf(x)dx = \int_a^{a+T}f(x)dx, \forall a $$
    * 3.有界性
        * $$[Th] 设f(x)在[a,b]有限区间内可导,\\且f'(x)有界,\forall x \in (a,b), 则 f(x) 有界, \forall x \in (a,b)$$
    * 4.单调性(无明确结论)
* [注3] 关于定积分的精确定义,黎曼积分,常义积分
    * $$1.两个任意\left\{ \begin{array}{ll} [a,b]任意切分 \\ 任意取高  \end{array} \right. 之后,\\ \int_a^bf(x)dx存在（唯一），称f(x)可积。$$
    * 2.考研中
        * $$1.n等分[a,b] \frac {b-a}n \to 0, n \to \infty$$
        * $$2.取右端点高 f(a+\frac {b-a}n i)$$
        * $$ 则 \lim_{n \to \infty} \Sigma_{i=1}^nf(a+\frac {b-a}n i)\frac {b-a}n = \int_a^bf(x)dx$$
    * 3.$$令a=0,b=1,则\lim_{n \to \infty} \Sigma_{i=1}^nf(\frac in)\frac 1n = \int_0^1f(x)dx$$
    * 三部曲
        * $$1.先提出\frac 1n$$
        * $$2.再凑出 \frac in$$
        * $$3.\frac 1n读作\int_0^1上的dx，\frac in读作\int_0^1上的x$$

### 3.变限积分 （强化班）
* $$1.\\\int_a^x f(t)dt————变上限积分函数\\\int_x^b f(t)dt————变下限积分函数\\\int_{\varphi_1(x)}^{\varphi_2(x)} f(t)dt————变限积分函数$$
* 2.变限积分属于定积分范畴
    * $$[a,b]有限,f(x)有界$$
    * $$如\\int_a^x f(t)dt,|x-a|有限变量，f(t)有界，x取不到\infty,x有限$$

    
        

    



## 二、计算（四大方法）
* 1.凑微分法
    * 1.基本积分公式(熟稔于心) 
        * $$ \int x^kdx=\frac1{k+1}x^{k+1}+C,k≠-1 $$
            * $$ \int \frac1{x^2}dx=-\frac1x+C $$
            * $$ \int \frac1{\sqrt x}dx=2\sqrt x+C $$
        * $$ \int \frac1xdx=\ln |x|+C $$
        * $$ \int a^xdx = \frac { a^x}{\ln a} + C $$
            * $$ \int e^xdx =  e^x + C $$
        * $$ \int \sin xdx= -\cos x + C $$
        * $$ \int \cos xdx= \sin x + C $$
        * $$ \int \tan xdx= -\ln|\cos x| + C $$
        * $$ \int \cot xdx= \ln |\sin x| + C $$
        * $$ \int \sec xdx= \ln |\sec x +\tan x| + C $$
        * $$ \int \csc xdx= \ln |\csc x -\cot x| + C $$
        * $$ \int \sec^2 xdx=  \tan x + C $$
        * $$ \int \csc^2 xdx=  -\cot x + C $$
        * $$ \int \sec x\tan xdx=  \sec x + C $$
        * $$ \int \csc x\cot xdx=  -\csc x + C $$
        * $$ \int \frac1{\sqrt{1- x^2}}dx=  \arcsin x + C $$
            * $$ \int \frac1{\sqrt{a^2- x^2}}dx= \int \frac1{\sqrt{1- (\frac xa)^2}}d(\frac xa) = \arcsin {\frac xa} + C $$
            * $$ \int \frac1{\sqrt{a^2 + x^2}}dx = \ln(x+ \sqrt{a^2 + x^2}) + C $$
            * $$ \int \frac1{\sqrt{x^2 -a^2}}dx = \ln(x+ \sqrt{x^2-a^2}) + C $$
        * $$ \int \frac1{1+ x^2}dx=  \arctan x + C $$
            * $$ \int \frac1{a^2+ x^2}dx=\frac 1a \int \frac1{1+ (\frac xa)^2}d(\frac xa) = \frac1a\arctan {\frac xa} + C $$
            * $$ \int \frac1{a^2 - x^2}dx=\frac 1{2a} \ln|\frac{a+x}{a-x}| + C $$
            * $$ \int \frac1{ x^2 - a^2}dx=\frac 1{2a} \ln|\frac{x-a}{x+a}| + C $$
        * $$ \int \sqrt{a^2- x^2}dx= \frac{a^2}2 \arcsin {\frac xa} +\frac x2\sqrt{a^2-x^2} + C $$
        * $$ 凑微分 \frac 1{\sqrt{u}}du=d(2\sqrt u)$$
        * $$ [Th]对于 \int f(x)dx, f(x)越复杂 \Rightarrow 越高兴$$
        * $$1. 先对复杂部分求导 2.再凑微分$$
        * $$求导后，倒着看， \frac {d f(x)}{dx} = F(x) \Rightarrow d f(x) = F(x)dx$$

* 2.换元法
    * 当凑微分不成功时，考虑换元 将复杂换成简单
    * 1.三角换元
        * $$ 当f(x)中含有\sqrt{a^2-x^2},\sqrt{a^2+x^2},\sqrt{x^2-a^2}可做如下换元 $$
        * $$\sqrt{a^2-x^2} \Rightarrow 令x=a \sin t, t \in (-\frac {\pi}2, \frac {\pi}2) $$
        * $$\sqrt{a^2+x^2} \Rightarrow 令x=a \tan t, t \in (-\frac {\pi}2, \frac {\pi}2) $$
        * $$\sqrt{x^2-a^2} \Rightarrow 令x=a \sec t, \left\{ \begin{array}{ll} (1)x > 0, t \in (0, \frac {\pi}2) \\ (2) x < 0, t \in ( \frac {\pi}2, \pi) \end{array} \right. $$
        * 函数回代要保证单调性，单调函数才有反函数
        * $$[注]若见到 \sqrt{ax^2+bx+c} \Rightarrow 化为\sqrt{\varphi^2(x)-k^2},\sqrt{k^2-\varphi^2(x)},\sqrt{\varphi^2(x)+k^2}再作三角换元$$
    * 2.倒代换
        * $$ x = \frac1t ,可用于分子次数明显低于分母次数$$
    * 3.复杂部分代换
        * 令复杂部分=t
        * 比如带根号的复杂部分
* 3.分部积分法
    * $$ \int udv = uv - \int vdu $$
    * $$ \int udv 难 \Rightarrow \int vdu易 $$
    * "反（反三角函数）、对、幂、指或三"排在前面的求导，排在后面的积分
    * $$ \int xe^xdx = \int xde^x = xe^x - \int e^xdx = xe^x - e^x + C$$
* 4.有理函数的积分
    * $$1.定义 形如 \int \frac {P_n(x)}{Q_m(x)}dx (n<m)的积分$$
    * $$2.方法$$
        * $$1.将Q_m(x)因式分解 $$
        * $$2.将\frac {P_n(x)}{Q_m(x)} 拆成若干最简有理分式之和$$
    * $$3.拆分原则$$
        * $$1.Q_m(x)分解出(ax+b)^k \Rightarrow 产生k项\\ \frac{A_1}{ax+b} +\frac{A_2}{(ax+b)^2} + \dots + \frac{A_k}{(ax+b)^k} ,k=1,2,\dots$$
        * $$2.Q_m(x)分解出(px^2+qx+r)^k\Rightarrow 产生k项\\ \frac{A_1x+B_1}{px^2+qx+r} +\frac{A_2x+B_2}{(px^2+qx+r)^2} + \dots + \frac{A_kx+B_k}{(px^2+qx+r)^k} ,k=1,2,\dots$$

##三、定积分的计算
* $$ \int_a^b f(x)dx  = F(b) -F(a)$$
* 1. 先按四大基本积分法求出F(x)
* 2. 代入上下限，只不过要求记住换元法时的细节:
    * $$ 对于 \int_a^b f(x)dx  = \int_{\varphi^-1(a)}^{\varphi^-1(b)} f[\varphi(t)]\varphi'(t)dt, 令x=\varphi(t) \\ 且要求\varphi'(t)连续，并x=\varphi(t)不超出区间[a,b]$$
* $$I_n= \int_0^{\frac {\pi}2}\sin^nxdx,n为大于1的整数$$  
    * $$可以得到递推式I_n=\frac{n-1}nI_{n-2}$$  
    * $$ I_n = \left\{ \begin{array}{ll} \frac{n-1}{n}\bullet\frac{n-3}{n-2}\dots\frac12\bullet\frac{\pi}2, & \textrm{$n为正偶数$} \\ \frac{n-1}{n}\bullet\frac{n-3}{n-2}\dots\frac23, & \textrm{$n为大于1的奇数$}  \end{array} \right.  华里士公式，华氏公式$$

##四、一元积分学应用(几何）——重在计算
###1.用积分表达和计算平面图形的面积
* $$1.y=y_1(x),y=y_2(x),x=a,x=b (a < b)所围平面图形$$
    * $$ \int_a^b|y_2(x)-y_1(x)| dx$$
    
###2.用积分表达和计算旋转体的体积
* $$1.y=y(x)与x=a,x=b (a < b)及x轴所围\sigma绕x轴旋转一周所得旋转体$$
    * $$ V_x=\int_a^b\pi\bullet y^2(x)dx$$
* $$2.上述\sigma 绕y轴旋转一周所得旋转体$$
    * $$V_y= \int_a^b 2\pi x\bullet | y(x)|dx$$ ——柱壳(qiao)法
* $$3.用积分表达和计算函数的平均值$$
    * $$y(x)在[a,b]上的平均值\bar y \triangleq \frac{\int_a^by(x)dx}{b-a} $$
    







        






 























 





        




        

 

