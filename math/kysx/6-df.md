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
### 3.一阶线性型
* $$形如 y'+p(x)y=q(x),p(x),q(x)为已知函数,y未知$$
* $$看成vu'+v'u$$
* $$e^{\int pdx} \bullet y' + e^{\int pdx} \bullet p \bullet y = e^{\int pdx} \bullet q  \\ \Rightarrow (y \bullet e^{\int pdx})'=e^{\int pdx} \bullet q \\ \Rightarrow 两边积分 y \bullet e^{\int pdx}  = \int e^{\int pdx} \bullet qdx + C \\ \Rightarrow y = e^{-\int pdx}(\int e^{\int pdx} \bullet qdx + C ) 公式法$$
$$ [自注] 这个通解公式在线性代数里有个其他解释




    


