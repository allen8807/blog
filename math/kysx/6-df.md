# 第六讲 微分方程 Differential Equation
* 概念，一阶方程求解，高阶方程求解

## 一、概念
* 1. $$ F(x,y,y',y'',\dots,y^{(n)}) $$
* 2. 阶数——方程中y的最高阶导数的阶数
    * $$如 y\sin x - y'' = \cos x + 2: 二阶 $$
    * $$\left\{ \begin{array}{ll} n=1, 一阶\\ n \ge 2, 高阶 \end{array} \right. $$
* 3.通解——解中所含独立常数的个数=方程的阶数

## 二、一阶方程的求解
### 1.变量可分离型
* $$形如\frac {dy}{dx} = f(x,y) 若能分离成= g(x)\bullet h(y) \Rightarrow \int \frac {dy}{h(y)}= \int g(x) dx $$
* 两边积分
* [注1]求解微分方程中,除了后面"一阶线性型"欲讲的特殊情形外,一律出现ln u,且u不知正负时,写ln|u|
* [注2]
    * 非线性方程中:通解≠全部解(通解+奇解=全部解)
    * 线性方程中:通解=全部解
    * 考研只考通解,数学专业考全部解
### 2.齐次型
* $$ \frac {dy}{dx} = f( \frac yx) ,换元，令\frac yx = u \Rightarrow y=u \bullet x \\  \Rightarrow y' = u' \bullet x + u \bullet 1 \Rightarrow u'x+u = f(u) \\ \Rightarrow \frac {du}{dx} \bullet x = f(u) - u \Rightarrow 继续分离变量 \int \frac{du}{f(u)-u} = \int \frac 
{dx}{x} $$
* 可接受隐式解

### 3.一阶线性型
* $$形如 y'+p(x)y=q(x),p(x),q(x)为已知函数,y未知$$
* $$看成vu'+v'u$$
* $$e^{\int pdx} \bullet y' + e^{\int pdx} \bullet p \bullet y = e^{\int pdx} \bullet q  \\ \Rightarrow (y \bullet e^{\int pdx})'=e^{\int pdx} \bullet q \\ \Rightarrow 两边积分 y \bullet e^{\int pdx}  = \int e^{\int pdx} \bullet qdx + C \\ \Rightarrow y = e^{-\int pdx}(\int e^{\int pdx} \bullet qdx + C ) 公式法$$
* [自注] 这个通解公式在线性代数里有个其他解释

### 4.可降阶 （强化班）
*[注]尚有两种类型的方程貌似二阶，实可降阶
    * $$1.y''=f(x,y')型 ————缺y$$
        * $$缺y\Rightarrow 干掉y',y'' ————赶尽杀绝y$$
        * $$令y'=p,则y''=p' \\\Rightarrow p'=f(x,p) 变为以上三种类型$$
    * $$2.y''=f(y,y')型————缺x$$
        * $$缺x,决不允许x再出现————斩草除根x $$
        * $$令y'=p,则y''=\frac{dp}{dx}=\frac{dp}{dy}\frac{dy}{dx}=\frac{dp}{dy}p$$
        * $$故\frac{dp}{dy}p=f(y,p)$$

## 三、二阶方程求解 （高阶方程2-4阶 强化班）
### $$1.二阶齐次方程 y'' + py' + qy = 0, p,q为常数$$
    * $$1. 写 \lambda^2+p\lambda+q =0 \Rightarrow \Delta = p^2-4q$$
    * $$2. \left\{ \begin{array}{ll} \Delta  > 0 \Rightarrow \lambda_1 ≠ \lambda_2 \Rightarrow y = C_1e^{\lambda_1x} + C_2e^{\lambda_2x}\\ \Delta  = 0 \Rightarrow \lambda_1 = \lambda_2 =\lambda \Rightarrow y = (C_1+C_2x)e^{\lambda x} \\ \Delta  < 0 \Rightarrow \lambda_{1,2} =-\frac p2 \pm \frac {\sqrt{4q-p^2}}2i = \alpha \pm \beta i \Rightarrow y = e^{\alpha x}(C_1\cos\beta x + C_2\sin\beta x) \end{array} \right. $$
    
### 2.二阶非齐次方程 
* $$1. y'' + py' + qy =e^{\alpha x} \bullet P_m(x)  $$
    * $$y_通=y_齐通+y^*_{非齐特}$$
    * $$1.照搬1齐次方程通解 \Rightarrow y_齐通 $$
    * $$2.设定y^* = e^{\alpha x} \bullet Q_m(x) \bullet x^k, Q_m(x)为一般多项式（如ax^2+bx+c)$$
    * $$对于k,一看二算三比较$$
        * $$ 一看:自由项中的 \alpha $$
        * $$ 二算:\lambda^2+p\lambda+q =0 \Rightarrow \lambda_1, \lambda_2 $$
        * $$三比 \left\{ \begin{array}{ll} \alpha ≠ \lambda_1, \alpha ≠ \lambda_2 \Rightarrow k = 0\\ \alpha = \lambda_1或 \alpha = \lambda_2 \Rightarrow  k=1 \\ \alpha = \lambda_1 = \lambda_2  \Rightarrow k = 2 \end{array} \right. $$
    * $$y^*代回原方程，用待定系数,求出Q_m(x)的系数，确定y^*$$
* $$2.y'' + py' + qy =e^{\alpha x} \bullet (P_m(x)\cos \beta x + P_n(x)\sin \beta x )$$
    * $$设定y^* = e^{\alpha x} \bullet (Q_l^{(1)}(x) \bullet \cos \beta x + Q_l^{(2)}(x)\sin \beta x ) \bullet x^k,\\ l = max(m,n)$$
    * $$对于k,一看二算三比较$$
        * $$ 一看:自由项中的 \alpha ,\beta , ( \alpha \pm \beta i)$$
        * $$ 二算:\lambda^2+p\lambda+q =0 \Rightarrow \lambda_1, \lambda_2 $$
        * $$三比 \left\{ \begin{array}{ll}  \lambda_{1,2} ≠ \alpha \pm \beta i \Rightarrow k = 0\\ \lambda_{1,2} = \alpha \pm \beta i  \Rightarrow  k=1 \end{array} \right. $$
    * $$y^*代回原方程，用待定系数,求出Q_l(x)的系数，确定y^*$$
    * $$照搬1齐次方程通解 \Rightarrow y_齐通 $$
    * $$y_通=y_齐通+y^*_{非齐特}$$

## 四、应用题（强化班）
* 1.背景公平————信息给予
* 2.翻译成数学表达式












    


