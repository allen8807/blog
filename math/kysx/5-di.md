# 第五讲 二重积分 Double Integral
* 概念，计算

### 一、概念
* 1.比较
    * 和定积分比较，是一个曲顶柱体的体积
    * $$\iint_{D}f(x,y) d \sigma  , d\sigma > 0$$
* 2.对称性(必考)
    * 1.普通对称性
        * $$设D关于y轴对称,\\ \iint_Df(x,y)d\sigma = \left\{ \begin{array}{ll} 2\iint_{D_1}f(x,y)d\sigma , & \textrm{$f(x,y)=f(-x,y)$} \\ 0, & \textrm{$f(x,y)=-f(-x,y)$} \end{array} \right. $$
    * 2.轮换对称性（在直角系下）
        * 积分值与用何字母表示无关
        

## 二、计算

###1.直角坐标系
* $$ I = \iint_Df(x,y) d\sigma = \iint_Df(x,y)dxdy$$
    * 1.x型区域(上下形),后积x
        * 后积先定限，限内画条线，先交下曲线，后交上曲线
        * $$I=\int_a^bdx\int_{y_1(x)}^{y_2(x)}f(x,y)dy$$
    * 2.y型区域(左右型),后积y
        * 后积先定限，限内画条线，先交左曲线，后交右曲线
        * $$I=\int_c^ddy\int_{x_1(y)}^{x_2(y)}f(x,y)dx$$
* 一定要画对D

###2.极坐标系
* $$\left\{ \begin{array}{ll} x=r\cos \theta\\ y=r\sin \theta \end{array} \right. $$
* 后积先定限，限内画条线，先交内曲线，后交外曲线
* $$I=\int_{\alpha}^{\beta}d\theta\int_{r_1(\theta)}^{r_2(\theta)}f(r\cos \theta,r\sin \theta)rdr$$ 
* $$ d\sigma = r \bullet d\theta \bullet dr =  d\theta \bullet r \bullet dr$$


        

