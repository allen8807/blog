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
        * $$ 设f(x)在x=x_0处 \left\{ \begin{array}{ll} (1)可导 \\ (2)取极值 \end{array} \right. ,\\则f'(x_0)=0 $$ 自己证明
    * $$[6]罗尔定理$$
        * $$ 设f(x)满足以下三条 \left\{ \begin{array}{ll} (1)[a,b]上连续 \\ (2) (a,b)内可导 \\ (3) f(a)=f(b) \end{array} \right. ,\\则 \exists \xi \in (a,b), 使 f'(\xi)=0 $$ 自己证明
    * $$[7]拉格朗日中值定理$$
        * $$ 设f(x) \left\{ \begin{array}{ll} (1)[a,b]上连续 \\ (2) (a,b)内可导  \end{array} \right. ,\\则 \exists \xi \in (a,b), 使 f'(\xi)= \frac {f(b) -f(a)}{b-a} $$ 
        * $$[注]若f(a)=f(b),则f'(\xi)=0，成为罗尔$$
    * $$[8]柯西中值定理$$
        * $$ 设f(x),g(x) \left\{ \begin{array}{ll} (1)[a,b]上连续 \\ (2) (a,b)内可导  \\ g'(x) ≠ 0\end{array} \right. ,\\则 \exists \xi \in (a,b), 使 \frac {f(b) -f(a)}{g(b)-g(a)} = \frac {f'(\xi)}{g'(\xi)}$$ 
        * $$[注]若g(x)=x, \frac{f(b) -f(a)}{b-a} = \frac {f'(\xi)}1 \Rightarrow 拉格朗日$$
    * $$[9]泰勒定理（泰勒公式）$$
        * $$任何可导f(x) = \Sigma a_nx^n 统一美 $$ 
        * 1. 带拉格朗日余项的泰勒公式
            * $$若f(x) 是n+1阶可导，$$
            * $$f(x)=f(x_0)+f'(x_0)(x-x_0)+\frac{f''(x_0)}{2!}(x-x_0)^2+\dots+\frac {f^{(n)}(x_0)}{n!}(x-x_0)^n + \frac {f^{(n+1)}(\xi)}{(n+1)!}(x-x_0)^{n+1}  , \xi 介于x,x_0之间 $$ 
            * $$ \frac {f^{(n)}(x_0)}{n!}(x-x_0)^n 是通项$$
            * $$ \frac {f^{(n+1)}(\xi)}{(n+1)!}(x-x_0)^{n+1}$$是拉格朗日余项 
            * $$ f(x) 是n+1阶可导，n+1阶写拉格朗日余项$$
            * $$ 若f(x)三阶可导 \Rightarrow $$ 
                * $$f(x)=f(x_0)+f'(x_0)(x-x_0)+\frac{f''(x_0)}{2!}(x-x_0)^2+ \frac {f'''(\xi)}{3!}(x-x_0)^3 , \xi 介于x,x_0之间$$ 带拉格朗日余项的泰勒三阶公式
            *$$若x_0=0,$$
                * $$f(x)=f(0)+f'(0)x+\frac{f''(0)}{2!}x^2+ \frac {f'''(\xi)}{3!}x^3 , \xi 介于x,x_0之间$$ 带拉格朗日余项的三阶麦克劳林公式
        * 2.带佩亚诺余项的泰勒公式
            * $$若f(x) 是n阶可导，$$
            * $$f(x)=f(x_0)+f'(x_0)(x-x_0)+\frac{f''(x_0)}{2!}(x-x_0)^2+\dots+\frac {f^{(n)}(x_0)}{n!}(x-x_0)^n + o((x-x_0)^n)  , \xi 介于x,x_0之间 $$ 
            * $$ \frac {f^{(n)}(x_0)}{n!}(x-x_0)^n 是通项$$
            * $$ o((x-x_0)^n)$$是佩亚诺余项 
            * $$ 若f(x)三阶可导 \Rightarrow $$ 
                * $$f(x)=f(x_0)+f'(x_0)(x-x_0)+\frac{f''(x_0)}{2!}(x-x_0)^2+ \frac {f'''(x_0)}{3!}(x-x_0)^3 +o((x-x_0)^3)$$ 带佩亚诺余项的泰勒三阶公式
            *$$若x_0=0,$$
                * $$f(x)=f(0)+f'(0)x+\frac{f''(0)}{2!}x^2+ \frac {f'''(x_0)}{3!}x^3 +o(x^3) $$ 带佩亚诺余项的麦克劳林公式
    * [10] 积分中值定理，后面讲
    
### 2.五大方面的应用
* 1. 涉及f(x)的应用（定理1-4）
    * $$ 设f(x)在[a,b]上连续,证明 \exists \xi \in [a,b],\\使\int_{a}^{b} f(x)dx = f(\xi)(b-a)$$ [积分中值定理]
    * 用介值定理证明
    * $$ 黎曼提出了定积分，莱布尼兹创造积分符号 \int $$ 
    * 定积分是一个面价值，定积分是一个数
    * $$[注]: 若a < b , f(x) \le g(x) \Rightarrow \int_a^bf(x)dx \le \int_a^bg(x)dx . 积分的保号性 $$
    * 介值定理三部曲
        * $$ 1.m \le f(x) \le M \\ 2. m \le \mu \le M \\ 3. f(\xi) = \mu$$
        * $$ 关键在于1到2步里的 f(x) \Rightarrow \mu $$
        * $$ f(\xi) = \frac{\int_{a}^{b} f(x)dx}{(b-a)} 也记为 \bar f 叫f(x)在[a,b]上的平均值$$
* 2.罗尔定理的应用(定理6)
    * 罗尔定理两大关键
    * 1.求导公式逆用法
        * $$F(x) = f(x) \bullet x \Rightarrow F'(x)=f'(x)\bullet x+f(x)\bullet 1$$
            * $$ F'(\xi) =  f'(\xi)\bullet \xi+f(\xi) = 0 $$
        * $$ F(x)=f(x)\bullet e^x \Rightarrow F'(x)=f'(x)\bullet e^x+f(x)\bullet e^x$$
            * $$ F'(\xi) =  (f'(\xi)+f(\xi))e^{\xi}=0 $$
            * $$ f'(\xi)+f(\xi) =0 $$
        * $$ F(x)=f(x)\bullet e^{\varphi (x)} \Rightarrow \\F'(x)=f'(x)\bullet e^{\varphi (x)}+f(x)\bullet e^{\varphi (x)} \bullet \varphi' (x)$$
            * $$ F'(\xi)=(f'(x)+f(\xi)\bullet \varphi'(\xi))\bullet e^{\varphi (x)} = 0 $$
            * $$ f'(x)+f(\xi)\bullet \varphi'(\xi) = 0 $$
    * 2.积分还原法
        * 1.将欲证结论中的$$\xi 改为 x$$
        * 2.积分,(为简单，令C=0)
        * 3.移项，使等式一端为0，另一端记为F(x)
    * $$ f'(x) = \frac {d f(x)}{dx} $$ 这里的dx是什么含义？
    * $$ \int udv = uv - \int vdu $$
    * $$ F(x)=f(x)g'(x) - g(x)f'(x) $$
* 3.拉格朗日中值定理的应用（定理7）
    * $$1.将f复杂化(一般等式证明)$$
    * 2.给出高阶条件，证低阶不等式
    * 3.给出相对低阶，证高阶不等式
    * $$ 4.具体化f，a < \xi < b , \Rightarrow 不等式 $$
* 4.柯西中值定理应用
    * $$ \frac {f(b) -f(a)}{g(b)-g(a)} = \frac {f'(\xi)}{g'(\xi)} $$
    * $$ f——抽象，g——具体 $$
* 5.泰勒公式的应用——信号$$f^{(n)}, n \ge 2 $$
    * 用在高阶
    * [注] 
        * $$ 1.  f(a)=f(b), f(c)=f(d) \Rightarrow \\ f'(\xi_1) = 0, f'(\xi_2) = 0 \Rightarrow f''(\xi)=0 $$
        * $$2.  泰勒展开成f'',f''', \dots $$
        
## 四、导数的几何应用
* （极值点、最值点、拐点；单调性、凹凸性；渐近线）

### 1.极值与单调性
* 1.极值定义
    * 1.广义极值
        * $$\exists x_0的某个邻域, \forall x \in u(x_0,\delta ) 都有 f(x) \le f(x_0) \\称x_0为f(x)的广义极大值点$$ 
        * 双侧定义
    * 2.真正极值
        * $$ \exists x_0的某个去心邻域, \forall x \in  去心 u(x_0,\delta ) 都有 f(x) < f(x_0) \\称x_0为f(x)的真正极大值点$$ 
    * [注]若无说明，按1办事，同理对最值
* 2.单调性与极值判别
    * $$1.若f'(x) > 0 ,\forall x \in I \Rightarrow f(x) 单调增,反之亦然$$
    * $$2.若f(x)在x_0连续, 去心 u(x_0,\delta )可导, \\(x_0-\delta, x_0 )内f'(x) < 0, (x_0, x_0 + \delta)内f'(x)>0 \Rightarrow 极小 , 反之亦然$$
    * $$3.若f(x)在x_0二阶可导, f'(x_0) = 0 ,f''(x_0)>0 \Rightarrow 极小 , 反之亦然$$
        * [注] 泰勒公式可证
            * $$f(x)=f(x_0)+f'(x_0)(x-x_0)+\frac{f''(x_0)}{2!}(x-x_0)^2 +o((x-x_0)^2)$$
            * $$ 移项 f(x)- f(x_0) = \frac{f''(x_0)}{2!}(x-x_0)^2 +o((x-x_0)^2) > 0 $$ 
            
### 2.凹凸性与拐点
* 1.凹凸性
    * $$ \forall x_1,x_2 \in I $$
    * $$ \frac{f(x_1)+f(x_2)}2 > f(\frac{x_1+x_2}2) \Rightarrow 凹 反之为凸$$
* 2.拐点————连续曲线凹凸弧的分界点
* 3.判别法 设f(x)在I上二阶可导，
    * $$1.若f''(x) > 0, \forall x \in I \Rightarrow f(x)凹 ,反之为凸$$
    * $$2.若f(x)在x_0点处左右邻域f''(x)变号 \Rightarrow （x_0,f(x_0)是拐点 $$   
     
### 3.渐近线
* 1.铅垂渐近线
    * $$ 若\lim_{x \to x_0^+(或x_0^-)}f(x) = \infty \Rightarrow x = x_0 为铅垂渐近线$$
    * (出现在:无定义点或区间端点)
* 2.水平渐近线
    * $$ 若\lim_{x \to +\infty(或-\infty)}f(x) = A \Rightarrow y = A 为水平渐近线$$
* 3.斜渐近线
    * $$ 若\lim_{x \to +\infty(或-\infty)}\frac{f(x)}x = a≠0 \\且\lim_{x \to +\infty(或-\infty)}[f(x) -a(x)] = b \exists \\ \Rightarrow y=ax+b  为斜渐近线$$
    
### 4.最值
* $$ 1.f(x)在[a,b]上,找\left\{ \begin{array}{ll} (1)f'(x) = 0 \Rightarrow x_0驻点 \\ (2) f'(x)不\exists \Rightarrow x_1不可导点 \\ (3) 端点a,b \end{array} \right. ,\\则 比较f(x_0),f(x_1),f(a),f(b) 取其最大（小）为最大（小）值$$
* $$若在I上求出唯一极大(小)值点，则由实际背景 \Rightarrow 此点即为最大(小)值点$$ 




        
        








        