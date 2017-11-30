# 第八讲 多元函数积分学 Multivariable Integral Calculus
* 预备知识，三重积分，第一型积分（线，面），第二型积分（线Green公式，面Guass公式），stokes公式 

## 一、预备知识
### 1."切一刀，投下来，转一圈"
* 1 "切一刀"——曲面方程的切平面
    * $$设\sum : F(x,y,x)=0 切平面 P_0为面上一点$$
    * $$1. \vec n = \{ F'_x|_{P_0}, F'_y|_{P_0}, F'_z|_{P_0}, \} = \{A,B,C\}$$
    * $$ 2. 写方程 A(x-x_0)+B(y-y_0)+C(z-z_0) = 0 $$
* 2."投下来"——曲线（曲面）在坐标面上的投影曲线（平面区域）
    * $$ L 投下来\rightarrow L_投$$ 
    * $$ \Sigma 投下来\rightarrow D$$
    * $$ 投影时，先消去z,在补上z=0$$
* 3."转一圈"——旋转曲面方程
    * $$1.提法:将\Gamma: \left\{ \begin{array}{ll} F(x,y,z)=0\\ G(x,y,z)=0    \end{array} \right. 绕L: \\ \frac {x-x_0}{l} =  \frac {y-y_0}{m}+\frac {z-z_0}{n} 旋转一周所得曲面\Sigma$$ 
    * $$2.求法$$
        * $$M_0(x_0,y_0,z_0)在L上, \vec \tau (l,m,n)是L的法向量 $$
        * $$M_1(x_1.y_1,z_1)在\Gamma上,M_1绕L旋转一周得纬圆,P(x,y,z)为纬圆上一点$$
        * $$ M_0,M_1,P构成圆锥$$
        * $$\left\{ \begin{array}{ll} (x_1-x_0)^2+(y_1-y_0)^2+(z_1-z_0)^2=(x-x_0)^2+(y-y_0)^2+(z-z_0)^2\\l(x-x_1)+m(y-y_1)+n(z-z_1)=0\\F(x_1,y_1,z_1)=0 \\G(x_1,y_1,z_1)=0    \end{array} \right.  \\ \Rightarrow \Sigma: f(x,y,z)= 0 ——空间曲面方程 $$

### 2.场论初步
* $$u=u(x,y) —— 数量场 field 没有向量方向，例如温度场$$
* $$\vec u = \vec u(x,y) —— 向量场，有方向，有大小 如重力场$$

* $$1.方向导数 u=u(x,y)$$             
    * $$P_0(x_0,y_0), P_1(x_0+t\cos\alpha,y_0+t\sin \alpha),P_0到P_1为\vec l$$
    * 1.定义法 
        * $$ \frac {\partial u}{\partial \vec l} | _{P_0} \triangleq \lim_{t\to 0^+} \frac{u(x_0+t\cos\alpha,y_0+t\sin \alpha) - u(x_0,y_0}{t} $$
    * 2.公式法
        * $$ 若u(x,y)在P_0处可微,\\则\frac {\partial u}{\partial \vec l} | _{P_0}=u'_x|_{P_0} \bullet \cos \alpha + u'_y|_{P_0} \bullet \sin \alpha $$

* $$2.梯度gradient u=u(x,y) $$
    * $$\vec {grad}\ U |_{P_0} =\{ u'_x|_{P_0} , u'_y|_{P_0} \}$$
    
* $$3.散度 \vec u = \vec u(x,y,z) = \{P,Q,R\} 旋转 $$
    * $$ \vec u = P(x,y,z)\vec i + Q\vec j + R\vec k  $$
    * $$ 散度 div \vec u = \frac {\partial P}{\partial x} + \frac {\partial Q}{\partial y} + \frac {\partial R}{\partial z} $$
    
* $$4.旋度$$
    * $$ \vec rot \quad \vec u =  $$



