# 第七讲 无穷级数 Infinite Series （强化班）
* 数项级数的判敛，幂级数的收敛域，展开与求和

## 引言
### 1.概念
* $$给出{u_n}$$
    * $$ 1. S_n=u_1+u_2+\dots+u_n $$
    * $$2. \lim_{n \to \infty}S_n = \Sigma_{n=1}^{\infty}u_n 叫无穷级数$$
* $$ \Sigma_{n=1}^{\infty}u_n 收敛 \Rightarrow  \lim_{n \to \infty}u_n = 0$$
* $$本质:研究u_n \to 0 的速度 (n \to \infty)$$

### 2.分类
*  $$\left\{ \begin{array}{ll} (常)数项级数\left\{ \begin{array}{ll} 1.\Sigma_{n=1}^{\infty}u_n & (u_n \ge 0)  ——正项级数\\ 2.\Sigma_{n=1}^{\infty}(-1)^nu_n &(u_n > 0) ——交错级数 \\3.\Sigma_{n=1}^{\infty}u_n & (u_n符号无限制)——任意项级数   \end{array} \right. \\ 函数项级数 ——4.\Sigma_{n=1}^{\infty}a_nx_n ——幂级数\end{array} \right. $$
* [注] 3类级数 可能=1类级数+2类级数

## 一、数项级数的判敛
### $$1.正项级数 \Sigma_{n=1}^{\infty}u_n (u_n \ge 0) 的判敛 $$
* 1.收敛原则(考抽象)
    * $$\Sigma_{n=1}^{\infty}u_n 收敛 \Leftrightarrow \{S_n\}有上界 $$ 
    * 证
    * $$ \{S_n\}有上界  \Leftrightarrow  \{S_n\}有界 \Leftrightarrow \{S_n\}收敛  \\ \Leftrightarrow \lim_{n \to \infty}S_n 存在 \Leftrightarrow  \Sigma_{n=1}^{\infty}u_n 收敛 $$
* 2.比较判别法
    * $$设\Sigma_{n=1}^{\infty}u_n, \Sigma_{n=1}^{\infty}v_n 为正项级数, 且u_n \le v_n, 则 \\ \left\{ \begin{array}{ll} \Sigma_{n=1}^{\infty}v_n  收 \Rightarrow \Sigma_{n=1}^{\infty}u_n 收\\ \Sigma_{n=1}^{\infty}u_n 发 \Rightarrow \Sigma_{n=1}^{\infty}v_n 发    \end{array} \right.  $$
    * $$[注]比较: \left\{ \begin{array}{ll} 简单: u_n自身放缩\\ 复杂:命题人告知    \end{array} \right.  $$
* 3.比较判别法的极限形式,2的进化,本质
    * $$设\Sigma_{n=1}^{\infty}u_n, \Sigma_{n=1}^{\infty}v_n 为正项级数, 则$$
    * $$\lim_{n \to \infty} \frac {u_n}{v_n} (\frac 00 型) =  \left\{ \begin{array}{ll} 0 \Rightarrow u_n 小 & \left\{ \begin{array}{ll} \Sigma_{n=1}^{\infty}v_n  收 \Rightarrow \Sigma_{n=1}^{\infty}u_n 收\\ \Sigma_{n=1}^{\infty}u_n 发 \Rightarrow \Sigma_{n=1}^{\infty}v_n 发    \end{array} \right.  \\ \infty \Rightarrow v_n 小 &  \left\{ \begin{array}{ll} \Sigma_{n=1}^{\infty}u_n  收 \Rightarrow \Sigma_{n=1}^{\infty}v_n 收\\ \Sigma_{n=1}^{\infty}v_n 发 \Rightarrow \Sigma_{n=1}^{\infty}u_n 发    \end{array} \right.     \\ A≠0 \Rightarrow & u_n,v_n同敛散 \end{array} \right.  $$
    * A≠0是重中之重
* 4.比值判别法(达朗贝尔判别法)
    * $$设\Sigma_{n=1}^{\infty}u_n 为正项级数, 则$$
    * $$ \lim_{n \to \infty} \frac {u_{n+1}}{u_n}   =\rho \left\{ \begin{array}{ll} < 1 \Rightarrow  收\\ > 1 \Rightarrow  发  \\ = 1 该法失效,另谋他法(转用比较法)  \end{array} \right.  $$


    

