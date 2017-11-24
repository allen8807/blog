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
### 2.齐次型
* $$ \frac {dy}{dx} = f( \frac yx) ,换元，令\frac yx = u \Rightarrow y=u \bullet x \\  \Rightarrow y' = u' \bullet x + u \bullet 1 \Rightarrow u'x+u = f(u) \\ \Rightarrow \frac {du}{dx} \bullet x = f(u) - u \Rightarrow 继续分离变量 \int \frac{du}{f(u)-u} = \int \frac 
{dx}{x} $$
* 可接受隐式解
* [注1]求解微分方程中,除了后面"一阶线性型"欲讲的特殊情形外,一律出现ln u,且u不知正负时,写ln|u|
* [注2]
    * 非线性方程中:通解≠全部解(通解+奇解=全部解)
    * 线性方程中:通解=全部解
    * 考研只考通解



### 3.一阶线性型
* $$形如 y'+p(x)y=q(x),p(x),q(x)为已知函数,y未知$$
* $$看成vu'+v'u$$
* $$e^{\int pdx} \bullet y' + e^{\int pdx} \bullet p \bullet y = e^{\int pdx} \bullet q  \\ \Rightarrow (y \bullet e^{\int pdx})'=e^{\int pdx} \bullet q \\ \Rightarrow 两边积分 y \bullet e^{\int pdx}  = \int e^{\int pdx} \bullet qdx + C \\ \Rightarrow y = e^{-\int pdx}(\int e^{\int pdx} \bullet qdx + C ) 公式法$$
* [自注] 这个通解公式在线性代数里有个其他解释


## 三、二阶方程求解
* $$1.齐次方程 y'' + py' + qy = 0, p,q为常数$$
    * $$1. 写 \lambda^2+p\lambda+q =0 \Rightarrow \Delta = p^2-4q$$
    * $$2. \left\{ \begin{array}{ll} \Delta  > 0 \Rightarrow \lambda_1 ≠ \lambda_2 \Rightarrow y = C_1e^{\lambda_1x} + C_2e^{\lambda_2x}\\ \Delta  = 0 \Rightarrow \lambda_1 = \lambda_2 =\lambda \Rightarrow y = (C_1+C_2x)e^{\lambda x} \\ \Delta  < 0 \Rightarrow \lambda_{1,2} =-\frac p2 \pm \frac {\sqrt{4q-p^2}}2i = \alpha \pm \beta i \Rightarrow y = e^{\alpha x}(C_1\cos\beta x + C_2\sin\beta x) \end{array} \right. $$
* $$2.非齐次方程 y'' + py' + qy =e^{\alpha x} \bullet P_m(x)  $$
    * $$y_通=y_齐通+y^*_{非齐特}$$
    * $$1.照搬1 \Rightarrow y_齐通 $$
    * $$2.设定y^* = e^{\alpha x} \bullet Q_m(x) \bullet x^k, Q_m(x)为一般多项式（如ax^2+bx+c)$$
    * $$对于k,一看二算三比较$$
        * $$ 一看:自由项中的 \alpha $$
        * $$ 二算:\lambda^2+p\lambda+q =0 \Rightarrow \lambda_1, \lambda_2 $$
        * $$三比 \left\{ \begin{array}{ll} \alpha ≠ \lambda_1, \alpha ≠ \lambda_2 \Rightarrow k = 0\\ \alpha = \lambda_1或 \alpha = \lambda_2 \Rightarrow  k=1 \\ \alpha = \lambda_1 = \lambda_2  \Rightarrow k = 2 \end{array} \right. $$






    


