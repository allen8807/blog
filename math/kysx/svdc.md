# 第二讲 一元函数微分学 Single Variable Differential Calculus
## 一、导数定义（牛顿）
* 瞬时变化率
* $$ \lim_{\Delta x \to 0 } \frac{f(x_0 + \Delta x) - f(x_0)}{\Delta x} =f'(x_0) $$ 记为
* [注]
    * 1. 左右有别， $$ x_0 + \Delta x $$
        * $$ \lim_{\Delta x \to 0^+ } \frac{f(x_0 + \Delta x) - f(x_0)}{\Delta x} =f_+'(x_0) $$  右导数
        * $$ \lim_{\Delta x \to 0^- } \frac{f(x_0 + \Delta x) - f(x_0)}{\Delta x} =f_-'(x_0) $$  左导数
        * 故 $$f'(x_0) \exists  \Longleftrightarrow f_+'(x_0)=f_-'(x_0)$$
    * 2. $$ \Delta x \to t $$ 变量的广义化
         * $$ f'(x_0) \triangleq \lim_{t \to 0 } \frac{f(x_0 + t) - f(x_0)}{t}  $$ 
         * 学会凑出t
    * 3. 一静一动原则
        * $$ \lim_{\Delta x \to 0 } \frac{f(x_0 + \Delta x) - f(x_0 - \Delta x)}{2\Delta x} =f'(x_0) $$ 典型错误，这里是两动
        * $$ \lim_{\Delta x \to 0 } \frac{f(x_0 + \Delta x) - f(x_0)}{\Delta x} =f'(x_0) $$ 一静一动
        * 导数是瞬时变化率，所以里面必须有$$f(x_0)$$这个静点
    * 4.换元法 
        * 令$$ x_0 + \Delta x  = x $$
        * 等价写法 $$f'(x_0) = \lim_{ x \to x_0 } \frac{f(x) - f(x_0)}{x - x_0}  $$ 差值形式
        * $$ \lim_{\Delta x \to 0 } \frac{f(x_0 + \Delta x) - f(x_0)}{\Delta x} =f'(x_0)$$ 增量写法
* 见到$$f'(x_0)$$ 先用定义法来
* $$ h \to 0, \cos h \to 1^- , 1- \cos h \to 0^+$$
* $$\frac{|x|}x 在 x \to 0 时有界，但是极限不存在$$
* 2A-A≠A （A只是符号，只有A存在时才做数量运算）
## 二、计算
### 1.基本求导公式
* $$(x^\alpha)' = \alpha x^{\alpha -1} $$
* $$ (a^x)'=a^x \ln a ,(e^x)'=e^x$$
* $$(\ln x)'= \frac1x$$
* $$(\sin x)' = \cos x , (\cos x)'= -\sin x$$
* $$(\tan x)' = \sec^2 x , (\cot x)'= -\csc^2 x$$
* $$(\sec x)' = \sec x\tan x , (\csc x)'= -\csc x \cot x$$
* $$(\arcsin x)' = \frac1{\sqrt{1-x^2}} , (\arccos x)'= -\frac1{\sqrt{1-x^2}} $$
* $$(\arctan x)' = \frac1{1+x^2} , (arccot x)'= -\frac1{1+x^2} $$
* $$(\ln (x+\sqrt{x^2+1})' = \frac1{\sqrt{x^2+1}} , (\ln (x+\sqrt{x^2-1})' = \frac1{\sqrt{x^2-1}} $$
### 2.基本求导法
* 1. 复合函数求导——一层一层剥开她的心
    * $$(f[g(x)])'=f'[g(x)]g'(x)$$
    * $$(uv)'=u'v+uv' $$
    * $$[注](u_1u_2\dots u_n)=\\u'_1u_2\dots u_n +u_1u'_2\dots u_n+ \dots + u_1u_2\dots u'_n $$
    * $$(\frac uv)'= \frac{u'v-uv'}{v^2}$$
* 2.隐函数求导
    * $$ 显: y=f(x) 隐: F(x,y)=0 ----(*),y=y(x) $$  
    * $$ 方法:在（*）式两边同时对x求导，注意y=y(x)即可（复合求导）$$
* 3.对数求导法
    * 对于多项相乘相除，开方，乘方的式子，先取对数，再求导
    * [注] u=u(x)
        * $$ (\ln|u|)'_x = \left\{ \begin{array}{ll} (\ln u)' = \frac1u \bullet u'  & \textrm{$u > 0$}\\ (\ln (-u))' =\frac1{-u} \bullet (-u') = \frac1u \bullet u'  & \textrm{$u < 0$} \end{array} \right. $$
        * 形式上相同，视绝对值而不见
        * $$ (\ln|u|)'_x = \frac1u \bullet u'$$
* 4.反函数求导
    * $$\frac{dx}{dy} = \frac1{y'}$$
    * 其实就是隐函数和复合函数结合
* 5.参数方程求导
    * $$ y = \left\{ \begin{array}{ll} x=x(t) \\ y=y(t) &\end{array} \right. $$
    * t为参数
    * $$\frac{dy}{dx} = \frac{dy}{dt} \bullet \frac{dt}{dx} $$
    * 结合反函数求导
* 6.高阶导数（见强化班）
##三、中值定理
### 1.定理总结
* 1.$$涉及f(x)的定理$$
    * $$ 设f(x)在[a,b]上连续，则 $$ (————前提)
    * $$[1](有界性定理)\exists K > 0 ,使 |f(x)| \le K , \forall x \in [a,b]$$
    * $$[2](最值定理)m \le f(x) \le M ,其中m,M分别为f(x)在[a,b]上的最小，最大值$$
    * $$[3](介值定理)若m \le \mu \le M, 则 \exists \xi \in [a,b], 使 f(\xi)=\mu$$
    * $$[4](零点定理）若f(a)\bullet f(b)<0, 则 \exists \xi \in (a,b), 使 f(\xi)=0$$ 柯西
    * 不要让几何直观蒙蔽了双眼 ———— 柯西
    * [1] - [4] 只用不证
    * 数缺形时少直观,形少数时难入微 ———— 华罗庚
* 2.$$涉及f'(x)的定理$$
    * $$[5]费马定理$$
        * $$ 设f(x)在x=x_0处 \left\{ \begin{array}{ll} (1)可导 \\ (2)取极值 \end{array} \right. ,则f'(x_0)=0 $$ 自己证明
    * $$[6]罗尔定理$$
        * $$ 设f(x)满足以下三条 \left\{ \begin{array}{ll} (1)[a,b]上连续 \\ (2) (a,b)内可导 \\ (3) f(a)=f(b) \end{array} \right. ,则 \exists \xi \in (a,b), 使 f'(\xi)=0 $$ 自己证明
    * $$[7]拉格朗日中值定理$$
        * $$ 设f(x) \left\{ \begin{array}{ll} (1)[a,b]上连续 \\ (2) (a,b)内可导  \end{array} \right. ,则 \exists \xi \in (a,b), 使 f'(\xi)= \frac {f(b) -f(a)}{b-a} $$ 

    

    












