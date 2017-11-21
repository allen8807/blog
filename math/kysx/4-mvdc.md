# 第四讲 多元函数微分学 Multivariable Differential Calculus
* 概念，计算，应用(极、最值) 

##一、概念
###1.极限
* $$设f(x,y)的定义域为D，P_0(x_0,y_0)是D的聚点，\\ \forall \varepsilon > 0, \exists \delta > 0, 当P(x,y) \in D \cap 去心u(P_0,\delta)时，\\恒有|f(x,y)-A| < \varepsilon \Rightarrow \\ \lim_{x \to x_0, y \to y_0}f(x,y)=A$$ 
    $$聚点的概念:理解为内点+边界点，但边界点不一定是D的$$

###2.连续性
* $$若\lim_{x \to x_0, y \to y_0}f(x,y)=f(x_0,y_0),称f(x,y)在(x_0,y_0)连续$$
    * $$[注]若"≠",叫不连续，不讨论间断类型$$
    
###3.偏导数（必考）————偏，片面，偷懒
* $$z=f(x,y)$$
* $$ \frac {\partial f}{\partial x}|_{(x_0,y_0)}= f_x'(x_0,y_0) \triangleq \lim_{\Delta x \to 0  } \frac {f(x_0+\Delta x,y_0)-f(x_0,y_0)}{\Delta x}$$
* $$\frac {\partial f}{\partial y}|_{(x_0,y_0)}=f_y'(x_0,y_0) \triangleq \lim_{\Delta y \to 0  } \frac {f(x_0 ,y_0+\Delta y)-f(x_0,y_0)}{\Delta y}$$
* $$ \partial  偏微分符号，拉格朗日发明，法文，读音类似round$$ 






