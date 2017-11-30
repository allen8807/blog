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
    * $$\overrightarrow {grad}\ U |_{P_0} =\{ u'_x|_{P_0} , u'_y|_{P_0} \}$$
    
* $$3.散度 \vec u = \vec u(x,y,z) = \{P,Q,R\} 旋转 $$
    * $$ \vec u = P(x,y,z)\vec i + Q\vec j + R\vec k  $$
    * $$ 散度 div\ \vec u = \frac {\partial P}{\partial x} + \frac {\partial Q}{\partial y} + \frac {\partial R}{\partial z} $$
    
* $$4.旋度, 三阶行列式$$
    * $$ \vec rot \quad \vec u = \left| \begin{array}{ccc}
\vec i & \vec j & \vec k \\
\frac{\partial }{\partial x} & \frac{\partial }{\partial y}  & \frac{\partial }{\partial z}  \\
P & Q & R
\end{array} \right| $$

## 二、三重积分
### 1.定义
* 类比二重积分
* $$ \iint_Df(x,y)d\sigma $$
* $$ \iiint_{\Omega}f(x,y,z)dv $$

### 2.计算
* 1.直角系与柱面系下
    * $$dv=dxdydz (直角系下)$$
    * $$dv=d\theta rdrdz (直角+极 = 柱)$$
    * 法一:先一后二法(先z后xy法，投影穿线法)
        * 后积先定限，限内画条线，先交写下限，后交写上限
        * 某个例子
        * $$I= \iiint_{\Omega}zdv = \iint_{D_{_1xy}:x^2+y^2\le 1}d\sigma \bullet \int_1^2 zdz \\+ \iint_{D_{_2xy}:1\le x^2+y^2\le 4}d\sigma \bullet \int_{\sqrt{x^2+y^2}}^2 zdz  $$
    * 法二:(先xy后z的方法，定限截面法)
        * $$\iiint_{\Omega}zdv = \int_1^2 dz \iint_{D_{xy}:x^2+y^2\le z^2}zd\sigma   $$

* 2.球面系下
    * $$dv = r^2\sin\varphi d\theta d\varphi dr \qquad 记住即可 $$
    * $$\left\{ \begin{array}{ll} x = r\sin\varphi \bullet \cos\theta \\ y = r\sin\varphi \bullet \sin\theta \\ z = r\cos\varphi \end{array} \right.$$ 
    * $$ I =  \iiint_{\Omega}f(x,y,z)dv \\ = \int_{\theta_1}^{\theta_2}d\theta \int_{\varphi_1}^{\varphi_2}d\varphi \int_{r_1}^{r_2}f(x,y,z)r^2\sin\varphi dr \\ = \int_{\theta_1}^{\theta_2}d\theta \int_{\varphi_1}^{\varphi_2}d\varphi \int_{r_1}^{r_2}f(r\sin\varphi \cos\theta, r\sin\varphi\sin\theta, r\cos\varphi)r^2\sin\varphi dr  $$
    
## 三、第一型积分
### 1.第一型曲线积分(和定积分，二重积分，三重积分本质一致都是面积)

* 1.定义
    * 对比定积分，底边由直线变曲线，dx变ds弧微分，L:y=y(x)
    * $$ \int_Lf(x,y)ds $$
    * $$ ds =\sqrt{ (dx)^2 + (dy)^2}$$
    * $$ ds =\sqrt{ 1 + (y'_x)^2}dx$$
    
* 2.计算口诀:一投二代三计算
    * $$1.参数方程 L: \left\{ \begin{array}{ll} x = x(t) \\ y = y(t)  \end{array} \right. \qquad \alpha \le t \le \beta $$
        * $$ \int_Lf(x,y)ds = \int_{\alpha}^{\beta}f(x(t),y(t))\sqrt {(x'(t))^2+(y'(t))^2}dt$$
    * $$2.显式方程 L: \left\{ \begin{array}{ll} y = y(x) \\ (x = x) \end{array} \right. \qquad a \le x \le b $$
        * $$ \int_Lf(x,y)ds = \int_a^bf(x,y(x))\sqrt {1+(y'(x))^2}dx$$
        
### 2.第一型曲面积分

* 1.定义
    * $$对比二重积分，底面变为曲面，d\sigma 变为dS 面密度,曲面质量$$
    * $$ \iint_{\Sigma}f(x,y,z)dS $$
    * $$ dS =\sqrt{1+(z'_x)^2+(z'_y)^2}dxdy $$
* 2.计算口诀 :一投二代三计算
    * $$\iint_{\Sigma:z=z(x,y)}f(x,y,z)dS \\ = \iint_{D_{xy}}f(x,y,z(x,y))\sqrt{1+(z'_x)^2+(z'_y)^2}dxdy $$

## 四、第二型积分
### 1.第二型曲线积分——无几何背景



    






